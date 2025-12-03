---
description: Understand what is a rule, and how you can create, edit and manage it
---

# What is a Rule?

## Rule Types

There are several types of rules in DecisionRules, and each can be used to create a different type of decision. For simple decisions following an IF - ELSE logic you can use Decision Trees. For more complex logic use Decision Tables, where each row corresponds to some combination of condition and result.

While it is true that our business rule engine is low-code and does not require knowledge of programming languages, one type of rule we do offer is a Scripting Rule, whose content is JavaScript code. This is a rule that allows you to enrich your decision-making process.

Lastly, we also offer the Rule flow. With this rule, you can create an entire decision process or maybe a part of it that shares a common logic. In a simple editor, you can easily link individual rules together as they logically follow each other.

{% hint style="info" %}
_See_ [_Rule Types_](/broken/pages/C428SVEbDiRt896FuJaX) _section for more information about each rule type._
{% endhint %}

## Rule Structure

Each rule consists of two main parts:

1. ### Rule Settings

Rule settings is the space for managing your rule. In addition to the rule name and note, this is where you define things like Rule Variables, and more importantly the input-output model. This model specifies the structure of the data you will send to the rule as input and then receive back as output. You can also enable audit logs for the rule here.

2. ### Rule Designer

In the Rule Designer interface, you create the rule itself. Based on the rule type, you create individual rows (Decision Table), blocks (Decision Tree), lines of code (Scripting Rule) or combine rules into one larger decision unit (Rule Flow). The one feature of Rule Designer that is common to all rule types, and one of the main advantages of DecisionRules, is the Test Bench.

#### Test Bench

This is an input-output editor that makes it easy to test the behavior of your new or existing rules when you insert certain input data. You can either enter data using a simple editor or you can use a JSON editor where you can put the entire input in JSON format.

## Rule Management

You can share your rules between spaces where you are a user directly in <mark style="color:purple;">DecisionRules</mark> (In Business Rules list), or use the export-import feature to download your rules and import them wherever you need them. By downloading as a JSON file to your local repository, you also create a backup for your rules.

Access your rules through REST API requests using external tools. Easily connect the DecisionRules rule engine to your existing logic. The most important type is the Solver API, which allows you to evaluate your inputs using the rules you create. Another type is the Management API, with which you can, for example, change the status of your rule. The last type of API is Business Intelligence that allows you to access Audit logs.

{% hint style="info" %}
_For more information about the API, see the documentation in the_ [_API section_](https://app.gitbook.com/s/-MN4F4-qybg8XDATvios/api/api-introduction)_._
{% endhint %}
