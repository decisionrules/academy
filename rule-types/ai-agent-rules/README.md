---
description: >-
  This page introduces the DecisionRules AI Rule, highlighting its key
  capabilities and applications.
---

# AI Agent Rules

## Introduction

DecisionRules counts with two core AI features:&#x20;

**AI Assistant** for authoring and navigating rules faster, supporting your Business Rules construction.&#x20;

**AI Agent Rule** for integration of Large Language Model (LLM) technology in the flows of precise and deterministic Decision-Making.&#x20;

In this section we will focus on the second one, you can find more information about the [AI Assistant](https://docs.decisionrules.io/doc/ai-assistant/about-ai-assistant) in our documentation.&#x20;

While current LLMs work with probability predictions and so allow 'hallucinations', Decision Engines are designed for deterministic outcomes and strong auditing. Therefore, for real integration with our reliable rules, DecisionRules constrains LLMs to an input/output model with precise structure, to guarantee an explainable and predictable Business Rule.&#x20;

The **AI Agent Rule** able to handle unstructured tasks— language reasoning, document analysis, handling ambiguity— otherwise no covered by more rigid rules. It transforms unstructured or complex data into **typed, structured JSON responses**, ensuring that even when you use AI, the final outcome remains integrated into a predictable and stable Decision Flow.

{% hint style="info" %}
You can always use the AI Agent by itself, but it is a good practice to use an AI Agent to handle the "messy" data at the start of a process, and then pass its structured JSON output to a Decision Table for a final, 100% deterministic result.
{% endhint %}

<figure><img src="../../.gitbook/assets/decisionflow with AI (2).png" alt=""><figcaption></figcaption></figure>

## AI Agent Rule Designer

The AI Agent Designer is optimized to help you bridge the gap between natural language instructions and clear decisions. The interface is split into two primary areas: the **Left Sidebar** for configurations and the **Main Panel** for building your logic.

### Left Sidebar

The sidebar handles the environment in which your model operates. To set up this background you can configure the rule sources and the optional features:

* **AI Model:** Select the specific Large Language Model (LLM) you wish to use (e.g., GPT-4, Claude, etc.).
* **Connector:** Manages the authenticated link between DecisionRules and the AI provider, ensuring secure communication.
* **Cache AI Response (Toggle):** A toggle to enable caching. This ensures that identical inputs return the same result instantly, reducing costs and increasing speed for repeated requests.
* **Explainable AI (Toggle):** Enables the generation of a system-defined explanation object, providing transparency into why the model reached a specific conclusion.
* **Data Dictionary:** A live reference panel of all available data. This allows you to drag and drop _Input variables_, _Rule Variables_, and _Attachments_ directly into your instructions.

<figure><img src="../../.gitbook/assets/left sidebar.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
In this Academy you will learn to use and manage the optional features, if you want a more technical description continue reading our documentation on [Cache](https://docs.decisionrules.io/doc/rules/ai-agent/caching) and the [Explainable AI](https://docs.decisionrules.io/doc/rules/ai-agent/caching).
{% endhint %}

### The Main Panel

This panel is the blank notebook where you describe the plot of your rule. It is organised into four specialized bookmarks:

* **Prompt / Instruction:** The core of the rule. Here, you write natural language instructions telling the AI what to do. You can use {_variables_} from your Data Dictionary to inject real-time data into your prompt.
* **Annotations:** This is the most critical tab for deterministic results. Here, you define exactly what the output JSON should look like, providing data types (Text, Number, Boolean, etc.) and descriptions for every field the model returns.
* **Explainable AI:** Active only when toggled in the sidebar, this tab lets you configure four fields that help audit the model's logic: `probability`, `reason`, `source_fragments`, and `warnings`. These fields are injected automatically.
* **Attachments:** Allows you to upload reference documents (PDFs, TXT, etc.). These files become part of the rule's versioned logic, allowing the AI to "read" specific policies or guidelines before making a decision.

<figure><img src="../../.gitbook/assets/main panel.png" alt=""><figcaption></figcaption></figure>

## Connectors

DecisionRules Spaces allow you to connect directly and more efficiently with your AI provider. These AI models that are set by a secure communication as authentizise provider for all the rules in the Space are counted as [**Connectors**](https://docs.decisionrules.io/doc/space/connectors), it means, you can manage them along side Data and Integration providers. &#x20;

We support a wide range of relevant Large Language Models for our connectors and continuously expand this list based on client requests.&#x20;

**The most important aspect of implementation is as follows:** "_To use model in the AI Agent Rule, you must first connect your LLM to your DecisionRules Space_".&#x20;

#### Steps to connect your LLM

1. Go to left-side menu and click on <mark style="background-color:purple;">**Space**</mark>
2. On the new menu opened next to it, select <mark style="background-color:purple;">**Connectors**</mark>&#x20;
3. Click on the main purple frame: "Add Connector"
4. Select among the AI models options
5. Fill in the information required
6. Press <mark style="background-color:purple;">**Create**</mark>&#x20;

&#x20;&#x20;

<figure><img src="../../.gitbook/assets/Add a PostgreSQL Database Connector (2).gif" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
You can also configure the connection of a new model within the **Left sidebar** of the _AI Agent Designer_, just click the <mark style="background-color:purple;">**+ Create**</mark> button next to Connectors.&#x20;
{% endhint %}

With the tutorial below you will be able to create a simple AI Agent Rule and discover how to integrate the new funcionalities with a Decision Flow.&#x20;

{% embed url="https://app.gitbook.com/o/-MN4G-7P_ExsN1x1n9Mp/s/2kePaAlhzmPFZTjuxdCY/~/edit/~/changes/66/rule-types/ai-agent-rules/create-a-simple-ai-agent-rule" %}
