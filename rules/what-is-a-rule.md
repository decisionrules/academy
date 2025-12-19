---
description: Understand what is a rule, its types, and how you can create and manage it
---

# What is a Rule?

The term 'rule' is used as a shorthand term for 'decision rule' or 'business rule'. A decision rule is a logic of instructions or conditions for making a decision over a set of predefined outputs. Decision rules provide a useful and fast way to process decision-making according to an institution's guidelines.&#x20;

## Rule Types

There are several types of rules in <mark style="color:purple;">DecisionRules</mark>, and each can be used to create a different type of decision. For simple decisions following an IF - ELSE logic you can use [Decision Trees](https://academy.decisionrules.io/rule-types/decision-trees). For retrieving information by simple key-base search, you can maintain your data with [Lookup Tables](https://docs.decisionrules.io/doc/rules/lookup-table). For more complex logical processes use [Decision Tables](https://academy.decisionrules.io/rule-types/decision-tables), where each row corresponds to some combination of conditions and results.

Our business rule engine combines both, a low-code engine that does not require knowledge of programming languages, and an engine that still allows you to apply such expertise. One type of rule we do offer is a [Scripting Rule](https://academy.decisionrules.io/rule-types/scripting-rules), whose content is JavaScript code. This is a rule that allows you to enhance your decision-making process.

Lastly, we also offer the category of 'Rule Flows'. These are a special type of rules, where you can create an entire flow of decisions that share a common logic. [Decision Flow](https://academy.decisionrules.io/rule-types/decision-flow) is the rule that easily link individual rules together in the form of 'Nodes', as they logically follow each other, and solves your requests in real time. The design of the [Integration Flow](https://docs.decisionrules.io/doc/rules/flow/decision-flow-vs.-integration-flow) is similar, but oriented to long-running processes and database batch processing. &#x20;

{% hint style="info" %}
Nodes are relevant rule blocks building the Flows, more about the possible nodes in your palette [here](https://app.gitbook.com/s/-MN4F4-qybg8XDATvios/rules/flow/flow-nodes-overview).&#x20;
{% endhint %}

## Rule Structure

Each rule consists of two main parts:

### Rule Model

Our decision rules are built according to the input/output model. The structure of the rules implies the reception of an input and the returning of an output.&#x20;

In the Model part of your rules you can specify the data you will send to the rule as input and then receive back as output. There, you can also access the settings of the rule, where you manage its name, alias and status, enable audit logs and other features.

### Rule Designer

In the Rule Designer interface, you create the rule itself. Based on the rule type, you create individual rows (Decision Table), blocks (Decision Tree), lines of code (Scripting Rule) or combine rules into one larger decision unit (Rule Flows). The one feature of Rule Designer that is common to all rule types, and one of the main advantages of <mark style="color:purple;">DecisionRules</mark>, is the Test Bench.

## Test Bench

This is an input-output editor that makes it easy to test the behavior of your new or existing rules when you insert certain input data. You can either enter data using a simple editor or you can use a JSON editor where you can put the entire input in JSON format.

## Share and Connect Rules

You can share your rules between spaces in two forms. First, if you are a user of the spaces in question, you can share directly in <mark style="color:purple;">DecisionRules.</mark> Go to the folder structure, your Rules List, and click on the context menu button  <mark style="background-color:purple;">**...**</mark>  corresponding to that rule, a dropdown menu will appear, select the 'Share with space' option.

Second, use the [export-import](https://academy.decisionrules.io/rules/export-and-import-of-the-rules) feature to download your rules and import them wherever you need them. By downloading as a JSON file to your local repository, you also create a backup for your rules.

Access your rules through REST API requests using external tools. Easily connect the DecisionRules engine to your existing logical processes. The most important connection is to make an external request for solving your decision rules and get an output for your team. You can send a request with the Solver API, which is located in the button  <mark style="background-color:purple;">**+ Integrations**</mark>  at the top bar of your rule. &#x20;

<figure><img src="../.gitbook/assets/Connect Rules.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
_For more information about the API, see the documentation in the_ [_API section_](https://app.gitbook.com/s/-MN4F4-qybg8XDATvios/api/api-introduction)_._
{% endhint %}
