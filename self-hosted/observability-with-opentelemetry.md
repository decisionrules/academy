---
description: >-
  Learn how OpenTelemetry helps you monitor and troubleshoot your DecisionRules
  workloads
---

# Observability with OpenTelemetry

{% embed url="https://youtu.be/KbF9vFweY7k?si=jx7GUoy--fEYHeYq" %}

## Introduction

A single call to the DecisionRules Solver looks simple from the outside. You send input, you get output. Inside, that call can be a Decision Flow calling a dozen child rules, each with its own conditions and its own outputs. In production, flows grow, and when a decision comes back with an unexpected result, the input and the output alone will not tell you what happened in between.

DecisionRules provides built-in observability through OpenTelemetry (OTLP) and structured logging. You can export traces, logs and metrics to Grafana, Datadog, an OpenTelemetry Collector or any other OTLP-compatible platform. Jaeger can be used for distributed traces. Everything is configured through environment variables on the server container, so there is no agent to install and no change to your rules or Decision Flows.

Observability is available in self-hosted deployments running on Docker or Kubernetes, from version **1.25.2 onwards**, and requires a license with telemetry enabled. If telemetry is not enabled by your license, OTLP traces, logs, metrics and stdout logging all remain disabled and `OTLP_URL` is ignored.

{% hint style="info" %}
_For the complete list of environment variables and their default values, see the_ [_OpenTelemetry and Access Logging_](https://docs.decisionrules.io/doc/other-deployment-options/docker-and-on-premise/opentelemetry-and-access-logging) _section of the documentation._
{% endhint %}

## What Traces, Logs and Metrics Tell You

The three signals answer three different questions, and choosing the wrong one is the most common mistake when troubleshooting a decision.

#### Traces

Traces show the execution flow of a request as a tree of spans, including instrumented HTTP and dependency calls made during rule or Decision Flow execution. Use traces when you want to know how a request moved through the system and how long each instrumented step took.

#### Logs

Logs are structured JSON records of what came in and what went out. There are three types. Access logs cover inbound and outbound requests and responses. Audit logs cover rule execution and contain the rule alias, the input data, the output data and the execution time. Application logs cover internal runtime errors.

If someone asks which decision was made and on what inputs, the answer is in the audit log, not in the trace.

#### Metrics

Metrics are aggregate runtime and service measurements across the deployment. They describe the health of the environment rather than individual requests.

Traces, access logs and audit logs can share the same `traceId`, so a trace, the access log for that request and the audit record for that rule execution can be lined up next to each other. Metrics are exported as aggregate measurements and are not tied to an individual request `traceId`.

## Turning Telemetry On

Telemetry is activated by one variable, and each signal is then switched on separately.

| Environment Variable   | Description                                                     | Default Value |
| ---------------------- | --------------------------------------------------------------- | ------------- |
| ---                    | ---                                                             | ---           |
| `OTLP_URL`             | Base OTLP endpoint, required to activate the telemetry pipeline | `undefined`   |
| `OTLP_TRACES_ENABLED`  | Enables the trace exporter and runtime instrumentations         | `false`       |
| `OTLP_LOGS_ENABLED`    | Enables the OTLP log exporter                                   | `false`       |
| `OTLP_METRICS_ENABLED` | Enables the periodic metric reader and exporter                 | `false`       |

{% hint style="info" %}
_If no telemetry appears at all, check_ `OTLP_URL` _first. The signal toggles have no effect until it is set, and telemetry also has to be enabled by your license._
{% endhint %}

## Deployment Patterns

DecisionRules supports several observability patterns. Which one you choose depends on the infrastructure you already have rather than on what you want to see.

{% stepper %}
{% step %}
### Full OpenTelemetry Integration

This pattern exports telemetry directly to an OTLP-compatible platform. Use it for centralized monitoring, distributed tracing, production diagnostics and SLA monitoring.

```yaml
env:
  - name: OTLP_URL
    value: "otel-collector:4318"
  - name: OTLP_TRACES_ENABLED
    value: "true"
  - name: OTLP_LOGS_ENABLED
    value: "true"
  - name: OTLP_METRICS_ENABLED
    value: "true"
```

A logs-only variant works the same way, with only `OTLP_LOGS_ENABLED` set. It is useful when a centralized logging platform is available but distributed tracing is not required.
{% endstep %}

{% step %}
### Structured Logging to Stdout

DecisionRules can emit structured JSON logs directly to stdout without any telemetry collector. This is often enough for troubleshooting and operational monitoring, and it works with Kubernetes log collection out of the box.

```yaml
env:
  - name: OTLP_URL
    value: "."
  - name: OTLP_STDOUT_ACCESS_LOGS_ENABLED
    value: "true"
  - name: OTLP_STDOUT_AUDIT_LOGS_ENABLED
    value: "true"
```

Access and audit logs can still be correlated through `traceId` and `spanId` where trace context is available or generated by the observability flow. With traces disabled, an inbound access log does not always carry an active span context.

{% hint style="info" %}
_You do not need an OpenTelemetry collector for this pattern._ `OTLP_URL` _is still set, as a placeholder, because it is what activates the observability pipeline._
{% endhint %}
{% endstep %}

{% step %}
### Stdout Logging with Audit Persistence Disabled

By default, audit logs are persisted to the audit database. Some deployments prefer audit records to leave through the logging pipeline only, with retention handled by an external platform. In this pattern audit logs are still generated and still emitted to stdout, they are simply not stored in MongoDB.

```yaml
env:
  - name: OTLP_URL
    value: "."
  - name: OTLP_STDOUT_AUDIT_LOGS_ENABLED
    value: "true"
  - name: AUDIT_MONGO_ENABLED
    value: "false"
```
{% endstep %}

{% step %}
### Hybrid Mode

OTLP export and stdout logging can run at the same time. You get centralized telemetry plus local container visibility, which makes debugging easier during deployments and migrations.

```yaml
env:
  - name: OTLP_URL
    value: "otel-collector:4318"
  - name: OTLP_TRACES_ENABLED
    value: "true"
  - name: OTLP_LOGS_ENABLED
    value: "true"
  - name: OTLP_STDOUT_ACCESS_LOGS_ENABLED
    value: "true"
  - name: OTLP_STDOUT_AUDIT_LOGS_ENABLED
    value: "true"
```
{% endstep %}
{% endstepper %}

#### Choosing a pattern

| If you have                                                                            | Use                                            |
| -------------------------------------------------------------------------------------- | ---------------------------------------------- |
| Grafana, Datadog, an OpenTelemetry Collector or another OTLP platform in production    | Full OpenTelemetry integration                 |
| Kubernetes log collection and no observability platform                                | Structured logging to stdout                   |
| An external log retention platform and a requirement to keep audit data out of MongoDB | Stdout logging with audit persistence disabled |
| A migration or rollout in progress and you want both views                             | Hybrid mode                                    |

## Controlling What Leaves Your Deployment

Sensitive keys such as authorization headers and API keys are redacted before telemetry leaves the container. Both `OTLP_LOG_SANITIZATION_ENABLED` and `OTLP_TRACE_SANITIZATION_ENABLED` default to `true`.

{% hint style="info" %}
_Sanitization is enabled by default for both logs and traces. You opt out of redaction, you do not opt in._
{% endhint %}

Beyond redaction, you can shape what is emitted.

| Environment Variable              | Description                                                                                                                                                                                                  | Default Value |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------- |
| `OTLP_LOG_ATTRIBUTE_ALLOWLIST`    | Comma-separated allowlist of log fields emitted by the OTLP log pipeline, applied before both stdout emission and collector export. `traceId`, `spanId` and `level` are always present even when not listed. | `undefined`   |
| `OTLP_ACCESS_EXCLUDE_HEALTHCHECK` | Excludes health endpoints from access traces and logs                                                                                                                                                        | `false`       |
| `OTLP_ACCESS_ONLY_SOLVER`         | Limits telemetry to Solver and job related traffic paths                                                                                                                                                     | `false`       |
| `OTLP_STDOUT_ACCESS_BODY_FORMAT`  | Body formatting strategy for access logs in stdout. Valid values: `JSON`, `string`, `string-pretty`.                                                                                                         | `'JSON'`      |
| `OTLP_STDOUT_WRAPPER_KEY`         | Wraps the stdout payload into a nested key for downstream parsers                                                                                                                                            | `undefined`   |
| `LOGGER_TYPE`                     | Controls console log format. Valid values: `STRING`, `JSON`, `NONE`.                                                                                                                                         | `STRING`      |
| `LOGGER_LEVEL`                    | Minimum log level to print or emit, for example `error`, `warn`, `info`, `debug`                                                                                                                             | `info`        |

If you run a busy deployment, switching on `OTLP_ACCESS_EXCLUDE_HEALTHCHECK` and `OTLP_ACCESS_ONLY_SOLVER` together removes a large amount of noise before it reaches your collector. That matters when your observability platform charges by ingest volume.

## Reading the Output

#### Traces

A trace is a tree. The root span is the inbound API request, and instrumented HTTP and dependency calls made during execution appear as nested spans underneath. On a real production Decision Flow this tree gets deep, and that depth is exactly what you cannot see from the request and the response alone.

#### Logs

Every log is structured JSON and carries `traceId` and `spanId`.

An inbound access request log, generated when the API receives a request:

```json
{
  "logType": "access",
  "direction": "inbound",
  "role": "request",
  "method": "POST",
  "url": "/rule/solve/my-rule/1",
  "traceId": "0f976b707efdd319550484483ab5f222",
  "spanId": "1e1ea1c52b642277",
  "body": {
    "input": {}
  }
}
```

An audit log, generated only when audit logging is enabled on the rule:

```json
{
  "logType": "audit",
  "statusCode": 200,
  "traceId": "0f976b707efdd319550484483ab5f222",
  "spanId": "1e1ea1c52b642277",
  "body": {
    "ruleAlias": "my-rule",
    "executionTime": 0.5,
    "inputData": {
      "input": {}
    },
    "outputData": [
      {
        "output": "Hello from Solver"
      }
    ]
  }
}
```

Outbound access logs follow the same shape with `"direction": "outbound"`. Application error logs use `"logType": "application"` together with a `level`, an `errorType` and a `message`.

{% hint style="info" %}
_For inbound and outbound response examples and the application error log format, see the_ [_log examples_](https://docs.decisionrules.io/doc/other-deployment-options/docker-and-on-premise/opentelemetry-and-access-logging) _in the documentation._
{% endhint %}

#### Correlation fields

| Field        | Purpose                                                      |
| ------------ | ------------------------------------------------------------ |
| `traceId`    | Correlates logs and spans belonging to the same request flow |
| `spanId`     | Identifies the specific operation or span within a trace     |
| `logType`    | Distinguishes access, audit and application logs             |
| `timestamp`  | Event creation time                                          |
| `statusCode` | HTTP response status when applicable                         |

## Verifying Your Setup

To verify traces, set `OTLP_URL` and `OTLP_TRACES_ENABLED` to `true`, then restart the server container. Run any rule from the DecisionRules application, or send a Solver request. Find the access log whose `url` matches your Solver endpoint, copy its `traceId` and search for that value in traces. You should see the execution tree for that request.

To verify logs only, set `OTLP_URL` and the relevant log toggle, restart the container and run a rule. Then search for the structured access or audit log in your log destination, whether that is your collector or the container's stdout.

In both cases, confirm that authorization headers and API keys appear redacted. If they do not, check that sanitization has not been switched off.
