# About Intelligence

Every rule execution generates valuable data. In addition to the decision outcome, **DecisionRules** captures detailed information about the evaluation process, including input and output values, execution time, solver version, and other relevant metadata.

This data serves a wide range of purposes. You may want to understand _why_ a particular decision was reached, monitor _how_ rules are being used in production, track _trends in execution patterns_, or verify that a newly deployed rule operates as intended.

{% embed url="https://youtu.be/kz-v9dkFJlg?si=CK1NgvWlwJ1jgCCB" %}

The **Intelligence** module gives you two ways to work with this data:

1. **Deep-dive into individual executions** to examine the details of a specific rule run.
2. **Analyze aggregated views** to gain insights into the broader usage and behavior of your DecisionRules environment.

By providing both granular and high-level perspectives, Intelligence empowers you to monitor, optimize, and improve your decision automation with confidence.

### What can you do with Intelligence?

Intelligence helps you answer questions such as:

* Which business rules are executed most frequently?
* How has rule usage changed over time?
* Which users or applications generate the most activity?
* When did a particular rule execute, and what was the outcome?
* Are there unusual trends or unexpected changes in system activity?
* Which rules should be reviewed or optimized based on their usage?

By combining detailed execution history with aggregated metrics, Intelligence transforms operational data into meaningful insights that support both technical and business users.

### Intelligence features

#### Audit Logs

Audit Logs provide a detailed record of every rule execution. Each log contains the complete execution context, including input data, output data, timestamps, execution metadata, and other information captured during rule evaluation.

Audit Logs are useful whenever you need to inspect a particular execution, investigate unexpected results, or verify how a decision was evaluated.

#### Statistics

**Statistics** take the data from **Audit Logs** and turn individual execution records into meaningful aggregated metrics and insightful trends.

Rather than examining one execution at a time, **Statistics** give you a high-level view of how your rules are performing and evolving over time. They let you monitor usage patterns, detect changes in rule activity, compare performance across different timeframes, and support data-driven decisions for optimization and improvement.

### Who is Intelligence for?

Different users benefit from Intelligence in different ways:

* **Business users** can understand how decision automation supports their business processes.
* **Developers and rule authors** can identify heavily used rules and investigate unexpected behavior.
* **QA engineers** can verify rule execution and analyze production activity during testing or issue investigation.
* **Administrators** gain visibility into user activity, system usage, and operational trends.
