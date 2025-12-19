---
description: This tutorial will walk you through the creation of a simple Scripting Rule.
---

# Create Simple Scripting Rule

## How to create a simple decision table

Let's advance one step at a time.

### 1. Log in

Becoming a superhero is a fairly straightforward process. After entering our [<mark style="color:purple;">login page</mark>](https://app.decisionrules.io/auth/login), you will be able to pass your credentials and log in.

<figure><img src="../../.gitbook/assets/login 2025.png" alt="" width="375"><figcaption></figcaption></figure>

There are multiple options for user login. If you do not have an account yet, you can [<mark style="color:purple;">create one</mark>](https://app.decisionrules.io/auth/register?type=true-registration). After logging in to the application, the folder structure of your Rules List will be displayed.

### 2. Create a new Scripting Rule

To display the rules creation list, click the <mark style="background-color:purple;">**+ Create**</mark> button on the search bar. Select your rule and you will be prompted to provide a nam&#x65;**.** For this example, select a name for your rule as you wish and press "Confirm". The new rule will be created and its design interface will be displayed. We will continue in the Rule Setting menu.

<figure><img src="../../.gitbook/assets/Create Scripting Rule Academy Dec 2025.gif" alt=""><figcaption></figcaption></figure>

### 3. Make basic settings

Rule Settings will be in a left-hand side menu, or you can access them by Rule Model at the top bar. Let's do some settings. Since we do not want this decision table to be available yet, we will change its status to **Pending**. To do this, switch on the current status **Published** to **Pending**.

To apply these changes, we have to click the <mark style="background-color:orange;">**Save**</mark> button at the top of the page, right corner.

### 4. Create an Input and Output model

We will now create an input and output model, which we will then use to set conditions and results. We create this model with a **JSON editor**.

{% hint style="info" %}
After creating an input or output model, we must always confirm the changes with the <mark style="background-color:purple;">**Save**</mark>  button.
{% endhint %}

#### **Input model**

First, we delete all created objects. Then we will add our specified requirements (**value1, value2**) as empty objects. Let's start with the input model. First, you can switch from "Designer" to "Model" at the centre of the top bar. Change from Simple Editor to JSON Editor at the toggle next to the "Rule Settings" button. Delete all default objects. Then add your specified requirements, e.g. **value1, value2**, as empty objects.&#x20;

{% hint style="info" %}
Because our model is simple, these objects do not contain any others. For more complex models, more information is [<mark style="color:purple;">here</mark>](https://docs.decisionrules.io/doc/decision-tables/input-and-output/json-editor).
{% endhint %}

#### **Input model Example:**

```javascript
{
  "value1": {},
  "value2": {}
}
```

#### **Output model**

We set the output model similarly, where we set it as root **result** (empty object).

**Output model Example:**

```javascript
{
  "result": {}
}
```

### 6. Creating rules

Now let's move on to code editor by clicking on **Scripting Rule Designer** it in the upper center and create individual rules.

{% hint style="success" %}
Our code editor is based on **Monaco Editor,** using its features, like autocomplete, syntax highlight, line numbers, etc.

**Shortcut Keys** are also working, but you need to be with a cursor in the editor.

**CTRL/CMD + S** - save

**CTRL/CMD + R** - run

**CTRL/CMD + Z** - undo

**CTRL/CMD + SHIFT + Z** - redo

**CTRL/CMD + F** - find

**SHIFT + ALT + F** - format
{% endhint %}

{% hint style="success" %}
Scripts must be written in **JavaScript** language.
{% endhint %}

For simplicity, we will remove the code from the code editor to create a new rule.

When to code editor is empty, we can start to create our own rule in **JavaScript.** It is straightforward, and you need to write your code which can look like below.

{% hint style="success" %}
Input must always be entered as input.yourInputVariable.

Output must always be entered as output.yourOutputVariable.

To return an output, always enter **return output** at the end of your script!
{% endhint %}

```javascript
/* 
    1.  Input variables
    Input body is set in input variable 
*/
let a = input.value1;
let b = input.value2;

/*
    2.  Define simple "multiply" function
*/
function multiply(a, b) {
    return a * b;
}

/*
    3.  Execute multiply function and store value result variable
*/
let resultMultiply = multiply(a, b);

/*
    4.  Set output model which is returned in REST API
*/
output.result = resultMultiply;

/*
    Optionally: It is possible print values to console
*/
log('Result multiply:', resultMultiply);

/*
    5.  Return output  
*/
return output;
```

{% hint style="info" %}
**console.log()** is forbidden due to performance, but you can use **log()** instead.
{% endhint %}

{% hint style="success" %}
You can use **log()** to print values in the console, which is at the bottom of the code editor.
{% endhint %}

{% hint style="info" %}
Always **save** your script using <mark style="background-color:purple;">**Save**</mark> (bottom of the page) or CTRL/CMD + S
{% endhint %}

### 7. Test created scripting rule

{% hint style="warning" %}
Don't forget to save your scripting rule!
{% endhint %}

Now we can test our rule. Before testing the rule, we must change the status of the rule to **"Published"**.

If we want to test a rule, we can click on the Test Bench button. An input and output window will show up at the bottom of the page. Press the <mark style="background-color:green;">**Run**</mark> icon at the center of the window.&#x20;

<figure><img src="../../.gitbook/assets/test bench scripting rule.png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
You can find more information about input and result at [<mark style="color:purple;">Solver API</mark>](https://docs.decisionrules.io/doc/api/rule-solver-api).
{% endhint %}

The result will be displayed in the **Output window (the right one)**.

{% hint style="info" %}
The debug mode can be turned on by clicking on [ <mark style="background-color:purple;">**Debug off**</mark>](#user-content-fn-1)[^1] . In scripting rules, it will enable to write **log()** in the console.
{% endhint %}

#### Request body example:

```javascript
{
  "value1": 2,
  "value2": 4
}
```

#### Response body example:

```javascript
{
  "result": 8
}
```

{% hint style="info" %}
More information about Test Bench is [<mark style="color:purple;">here</mark>](https://app.gitbook.com/s/-MN4F4-qybg8XDATvios/rules/common-rule-features/test-bench).
{% endhint %}

[^1]: 
