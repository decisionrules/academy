# Create a Simple AI Agent Rule

{% hint style="success" %}
All steps can be created and managed right in DecisionRules app
{% endhint %}

**Use Case:** The rules of this tutorial were designed to be called by a user when a new NDA arrives and the team want to decide the necessary redlines in real time.&#x20;

**Goal:** The goal was to automate the process such that the system sends the NDA to DecisionRules and retrieve the evaluation of the document with the redlines that must be pointed out.&#x20;

The main features in DecisionRules to achieve this goal are the **AI Agent Rule** and the **Decision Flow**. In this detailed end-to-end tutorial, we'll guide you to build an **AI Agent Rule** for the analysis of the unstructured data given in the new NDA, getting back the data of the NDA in structured JSON format. In the second part of this tutorial we'll model a **Decision Flow** that integrates the **AI Agent Rule** and complete the goal in a predictable, deterministic way.&#x20;

We'll cover navigating through the creation process, configuring **Decision Flow** nodes, and generating the final output, which includes the redlines of the NDA according to the evaluation of the rules, the reference in the text for the decision of those redlines, and personalized messages for the user in case of misbehaviour because the unstructured data.&#x20;

At the end we’ll test our new rule with one mock example. This tutorial will help you understand key **AI Agent Rule** practices and data manipulation techniques.&#x20;

## 1st Part: How to create a simple AI agent rule

Let's advance one step at a time.

### 1. Log in

Becoming a superhero is a fairly straightforward process. After entering our [<mark style="color:purple;">login page</mark>](https://app.decisionrules.io/auth/login), you will be able to pass your credentials and log in.

<figure><img src="../../.gitbook/assets/login 2025.png" alt="" width="375"><figcaption></figcaption></figure>

There are multiple options for user login. If you do not have an account yet, you can [<mark style="color:purple;">create one</mark>](https://app.decisionrules.io/auth/register?type=true-registration). After logging in to the application, the folder structure of your Rules List will be displayed.

### 2. Create a new AI Agent Rule

To display the rules creation list, click the <mark style="background-color:purple;">**+ Create**</mark> button on the search bar. Select your rule and you will be prompted to provide a nam&#x65;**.** For this example, we will create a AI Agent Rule for analysing a new NDA, select a name for your rule as you wish and press "Confirm". The new rule will be created and its design interface will be displayed.

<figure><img src="../../.gitbook/assets/Create a New AI Agent Rule in DecisionRules.gif" alt=""><figcaption></figcaption></figure>

### 3. Create the input and output (I/O) model

We will now create the **Input/Output** model which is used to set the instructions for the AI and the invariable structure of the output . Similar to the other rules, there are two ways to write these models:

#### Using the simple editor

First, you can switch from "Designer" to "Model" at the centre of the top bar.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2026-04-29 at 14.52.49 (2) (1).png" alt=""><figcaption></figcaption></figure>

**Delete the default attribute "input"** by clicking the trash can icon next to the name. Then, add your own attribute: First create the root of your attributes clicking the **+Add** button. For this example you will need just one root: <mark style="color:purple;background-color:purple;">**nda**</mark>. After, you can add all the data required for the analyzis of that `nda` object: <mark style="color:purple;background-color:purple;">**originatingParty**</mark>, <mark style="color:purple;background-color:purple;">**disclosingParty**</mark>, <mark style="color:purple;background-color:purple;">**receivingParty**</mark>, and <mark style="color:purple;background-color:purple;">**text**</mark>.&#x20;

<figure><img src="../../.gitbook/assets/Edit Input Fields in Model Configuration.gif" alt=""><figcaption></figcaption></figure>

Now, you can continue with the output model. It will be set similarly. As root attributes, add <mark style="color:green;background-color:green;">**terms**</mark> and <mark style="color:green;background-color:green;">**reference**</mark>. Then, you can add a similar child attributes to the both roots because they are connected.&#x20;

* The `terms`' fields are expecting: **the precise report**, whether the data exist; what exact number, name or sentence it is.
* The `reference`'s fields are expecting: **the exact words in the text** from where the AI is taking the report for terms.

Rename the new attributes according the information you want to obtain. A comprehensive list of attributes that will be useful in future examples and exercises is the following:

* <mark style="color:green;background-color:green;">**scope\_and\_definition**</mark>, <mark style="color:green;background-color:green;">**confidentiality\_period\_years**</mark>, <mark style="color:green;background-color:green;">**governing\_law**</mark>, <mark style="color:green;background-color:green;">**notice\_period\_days**</mark>, <mark style="color:green;background-color:green;">**reciprocity**</mark>, <mark style="color:green;background-color:green;">**exclusions**</mark>, <mark style="color:green;background-color:green;">**permitted\_disclosures**</mark>, <mark style="color:green;background-color:green;">**liability\_cap\_usd**</mark>, <mark style="color:green;background-color:green;">**return\_of\_information\_required**</mark>, <mark style="color:green;background-color:green;">**return\_deadline\_days**</mark>, and <mark style="color:green;background-color:green;">**residuals\_clause**</mark>.&#x20;

{% hint style="warning" %}
You don't have to write one by one the attributes, see how to use the JSON editor below.
{% endhint %}

<figure><img src="../../.gitbook/assets/outputs (1).png" alt="" width="375"><figcaption></figcaption></figure>

#### Using the JSON editor

Now, **the JSON editor can reduce the time for modelling the I/O model** by simple copy and paste. You can provide the input and output model in JSON format from any other source. In our case, use the following format to copy and paste in your editor:&#x20;

{% tabs %}
{% tab title="Input Model" %}
```json
{
  "nda": {
    "originatingParty": {},
    "disclousingParty": {},
    "receivingParty": {},
    "text": {}
  }
}
```
{% endtab %}

{% tab title="Output Model" %}
```json
{
  "terms": {
    "scope_and_definition": {},
    "confidentiality_period_years": {},
    "governing_law": {},
    "notice_period_days": {},
    "reciprocity": {},
    "exclusions": {},
    "permitted_disclosures": {},
    "liability_cap_usd": {},
    "return_of_information_required": {},
    "return_deadline_days": {},
    "residuals_clause": {}
  },
  "reference": {
    "scope_and_definition": {},
    "confidentiality_period_years": {},
    "governing_law": {},
    "notice_period_days": {},
    "reciprocity": {},
    "exclusions": {},
    "permitted_disclosures": {},
    "liability_cap_usd": {},
    "return_of_information_required": {},
    "return_deadline_days": {},
    "residuals_clause": {}
  }
}
```
{% endtab %}
{% endtabs %}

<figure><img src="../../.gitbook/assets/new io model.png" alt=""><figcaption></figcaption></figure>

For now, we are done!

{% hint style="warning" %}
After creating an input and output (I/O) model, we must always confirm the changes with the <mark style="color:orange;background-color:orange;">**Save**</mark> button.
{% endhint %}

{% hint style="info" %}
More information on the JSON editor can be found [<mark style="color:purple;">here</mark>](https://docs.decisionrules.io/doc/decision-tables/input-and-output/json-editor).
{% endhint %}

### 4. Set the configurations of the background

To set the environment where your LLM will operate, switch again, from "Model" to "Designer". Go to the left sidebar and start the configurations according to your requirements.&#x20;

{% hint style="info" %}
The instructions to create a Connector for your LLM are in the introduction to the AI Agent Rule.
{% endhint %}

* **AI Model:** We will show one possible sample. For this instance we choose the Model: _Gemini 3 Flash_. Clearly for the reproduction in your Space you can select any other model in the dropdown.&#x20;
* **Connector:** The LLM already connected to our Space has the named: gemini (connection-vhksg). The options showed to you will depend of the connectors that you already created.
* **Cache AI Response (Toggle):** For the creation and testing of this new rule you can activate the Cache.&#x20;
* **Explainable AI (Toggle):** For this example, the Explainable AI won't be necessary. Its use will be fine in more advanced exercises.&#x20;
* **Data Dictionary:** It is enough to check that you have all the information necessary for building the prompt.

{% hint style="success" %}
**Best Practices:** The Cache will help you to make faster tests and secure analysis with the same input in a short period of time, for this reason it is good to activate for the rule's construction.
{% endhint %}

<figure><img src="../../.gitbook/assets/Configure and Test AI Model for NDA Analysis (2).gif" alt=""><figcaption></figcaption></figure>



### 6. Build the Prompt

Currently, the practices for writing optimal prompts evolve fast, the suggestions in this section will have constantly improvements. What is relevant to notice is to apply the best practices for instructions, using the Data Dictionary in a way that your input model will be used with precision in the prompt.

For this rule, we will make explicit the **Role** assumed by the AI, the **Context** of the analysis, and the **Task** required from the model. A possible example:

{% prompt description="" %}
```markdown
## ROLE
You are a senior legal compliance analyst with deep expertise in NDA review, contract standards enforcement, and commercial contract negotiation.

## CONTEXT
You are analyzing a NDA submitted by {nda.originatingParty} for legal revision and red-line version. The disclousing party of the NDA is {nda.disclousingParty}  and the receiving party is {nda.receivingParty}. 

NDA = {nda.text}

## TASK
Read the NDA and extract all structured fields defined in the output schema. 

terms' fields are expecting a report: whether the data exist; what exact number, name or sentence it is; a judgemnet if the information is not clear.

reference's fields are expecting: the precise words in the text from where you are taking the report for terms. 

Use only the allowed values listed in each field annotation. Extract values directly from the nda.
For every output field that cannot be determined from the report — return null.
For every output field that can be determined and the answer is explicitely negative - return false.
```
{% endprompt %}

As you can see, there are string of data in the form: _{a.b}_. This are the attributes from the input in the data dictionary, and will be filled dynamically, each new payload for the input will give precise new information for the analysis.&#x20;

The most important is the body of the NDA in _{nda.text}_. &#x20;

**Remark:** If required, you can also use attached documents (in pdf or other formats) for the prompt. First, they must be added in the Tab "Attachments", click on Add Attachment and select your document. Next, go back to the "Prompt/Instruction", drag and drop the attachment from the data dictionary, and repeat the logic: locate the attachment in the part of the prompt that better explain the use of that data.&#x20;

### 6. Edit the Annotations

By the relevant role of the Annotations in the AI agent rule, this is the most extensive work. We will cover each detail.&#x20;

In the main panel move from "Prompt/Instruction" to "Annotations".

**You will find three columns:**&#x20;

The first column reflects your **output model**. The second column is for the specification of the **data types** expected in each particular output attribute. The third column is **a description** of what exactly you are expecting and how.  &#x20;

<figure><img src="../../.gitbook/assets/pre annotations.png" alt=""><figcaption></figcaption></figure>

The **data type** of a root will be always {} Object. In this example, change the children of terms to the more convenient data type. Notice that in case of doubt, it is better to select a data type that can cover all the expected outputs and offer a more restrict set of these outputs. This is the given solution for some of them:

| Attribute                      | Data Type |
| ------------------------------ | --------- |
| scope\_and\_definition         | Text      |
| confidentiality\_period\_years | Number    |
| governing\_law                 | Text      |
| liability\_cap\_usd            | Number    |
| permitted\_disclosures         | Boolean   |
| residuals\_clause              | Boolean   |

<figure><img src="../../.gitbook/assets/annotations.png" alt=""><figcaption></figcaption></figure>

In **the description** of the last column for each element of the output, it is a good practice to include the conditions you are expecting to fulfil in order to select just one element of the set of outputs. You can read some possible descriptions in the image above.&#x20;

Regarding the children of reference, all of them must be of type: Text. And the description is the same as well, you can repeat the pattern of the first child in all the others:[^1]

| Attribute                      | Description                                                                                                                                          |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| scope\_and\_definition         | Return a string with the exact words in the text of the nda, where you extracted the info for the ouput above: terms.scope\_and\_definition.         |
| confidentiality\_period\_years | Return a string with the exact words in the text of the nda, where you extracted the info for the ouput above: terms.confidentiality\_period\_years. |

{% hint style="warning" %}
The last column must be filled for every object in the output, including the roots.
{% endhint %}

{% hint style="info" %}
In the description of the roots it is always good to put some limits and minimum of compliance.&#x20;
{% endhint %}

### 7. Test the Agent

Now we can test our rule in Test Bench.

We can click the <mark style="background-color:purple;">**Test Bench**</mark> icon at the beginning of the bottombar. After clicking the icon, the Test Bench will show up at the bottom of the page.&#x20;

Then we can fill in some mock data, some examples of NDAs. In the document below you will find a sample. Use the specifications of the document to complete the input, and remember to paste the text of the NDA in nda.text. Click the <mark style="background-color:green;">**Run**</mark> button and the result will be displayed in right hand side of the Test Bench. Note that you can switch between the **Simple Bench** and the **JSON Bench**.

{% file src="../../.gitbook/assets/Mock_NDA.pdf" %}

<figure><img src="../../.gitbook/assets/testing.png" alt=""><figcaption></figcaption></figure>

## 2nd Part: How to integrate the AI agent rule with a decision flow

In this section we will create a Decision Flow that use the structured data given by the AI agent rule to validate the NDA parameters according the company's standards, and decide which redlines are pertinent.&#x20;

### Logic of the flow

#### IO Model

Our input model captures the data required to run the AI agent rule above, it will replicate the input model of the AI agent rule. The reason for this design are the results from the AI node, which contain all the information required to run the other rules and nodes in the flow.&#x20;

Our output model will be constructed slightly different. It includes `redline` 's validation, the `reference` to accept or reject those redlines in the text, and `error` option to handle drawbacks. In this sample the company has just four minimal standards to accept an NDA (Next example will handle big sets of standards).

{% tabs %}
{% tab title="Input Model" %}
```json
{
  "nda": {
    "originatingParty": {},
    "disclousingParty": {},
    "receivingParty": {},
    "text": {}
  }
}
```
{% endtab %}

{% tab title="Output Model" %}
```jsonl
{
  "redline": {
    "confidentiality_period_years": {},
    "governing_law": {},
    "notice_period_days": {},
    "reciprocity": {}
  },
  "reference": {
    "confidentiality_period_years": {},
    "governing_law": {},
    "notice_period_days": {},
    "reciprocity": {}
  },
  "errors": {
    "types": {},
    "message": {}
  }
}
```
{% endtab %}
{% endtabs %}

#### Flow of the Process

When designing the Decision Flow as a decision process, establishing a logical steps ensures stability and efficiency.&#x20;

1. **AI Analysis**: Start by converting the unstructured data of the NDA text in a typed JSON response. This step allows to extract with precision the attributes from the NDA for evaluation. At this stage, the analysis of the AI is the key to use the other strong predictable rules over the NDA.
2. **Validation of the company's standards**: This is the core of the flow, the standards of the company are saved in Rules inside the Space. The flow will call four rules to evaluate a set of four minimal standards: _The confidentiality period_, _the governing law country_, _the notice period_, and _the reciprocity of the agreement_. Based on these rules, the system decides which sections of the NDA must be redlined or not.
3. **Error handle:** Because the nature of the AI practice, it is not gurantee the NDA gives all necessary data in the first call, and the LLM is not always fast. With a couple of nodes we design a path to follow in case the NDA misses information or you run out of time waiting for the LLM answer. These nodes will give you a warning and a message to solve quickly the problems.
4. **Generating the final redlines**: Use the values from the previous steps to populate the output properties specified in the output model. Additionally, if there are error, send an error message accordingly.

### 1. AI Analysis

It's time for adding first node to the canvas. Start by adding an **AI Agent** node and connect the **Start** node to it. Open the node, click on the dropdown of the Select Agent, and choose the AI agent rule to analyse the NDA. After selecting your rule, its input model will show. We need a mapping from our Data Dictionary to the input of the rule: Drag and drop from the Data Dictionary the root `nda` in the main Decision Flow input, to the section Rule Inputs and the attribute with the same name, it means  `nda` . Save values in the modal.&#x20;

<figure><img src="../../.gitbook/assets/Configure an AI Agent to Analyze NDA Documents.gif" alt=""><figcaption><p>Adding the AI Agent node</p></figcaption></figure>

### 2. Validation of the company's standards

Drag and drop four **Business Rule** nodes onto the canvas, locate them in parallel next to the **AI Agent** node.&#x20;

In the first **Business Rule** we will use the _Reciprocity_ tree (A JSON file with the design of the rule is here below). The standard is simple: **The NDA must be reciprocal**. The logic of the standard can be expressed in a Decision Tree keeping the simplicity:&#x20;

1. **Missed information:** IF the field for the NDA reciprocity report is empty, THEN return error message (Remember the AI can result null if the NDA is not clear).
2. **Reciprocal NDA:** IF the NDA reciprocity report contains true, THEN return passed.
3. **No Reciprocal NDA:** IF the NDA reciprocity report contains false, THEN return failed and the reason.&#x20;

{% file src="../../.gitbook/assets/Reciprocity_v1.json" %}

In the second **Business Rule** we will use the _Notice Period_ tree (A JSON file with the design of the rule is here below). The standard is simple: **We must have minimum 30 days to solve and communicate leaks**. The logic of the standard can be expressed in a Decision Tree keeping the simplicity:&#x20;

1. **Missed information:** IF the field for the NDA notice period is empty, THEN return error message (Remember the AI result null if the NDA misses this information).
2. **Enough Notice Period:** IF the NDA notice period is greater or equal to 30 days, THEN return passed.
3. **Not Enough Notice Period:** IF the NDA notice period is less than 30 days, THEN return failed and the reason.&#x20;

{% file src="../../.gitbook/assets/Notice_Period_v1.json" %}

In the third **Business Rule** we will use the _Confidentiality Period_ tree (A JSON file with the design of the rule is here below). The standard is simple: **We must have maximum 15 years for confidentiality**. The logic of the standard can be expressed in a Decision Tree keeping the simplicity:&#x20;

1. **Missed information:** IF the field for the NDA confidentiality period is empty, THEN return error message (Remember the AI result null if the NDA misses this information).
2. **Under the limit period:** IF the NDA confidentiality period is less or equal to 15 years, THEN return passed.
3. **Over the limit period:** IF the NDA confidentiality period is greater than 15 years, THEN return failed and the reason.&#x20;

{% file src="../../.gitbook/assets/Confidentiality_Period_v1.json" %}

In the fourth **Business Rule** we will use the _Governing Law_ tree (A JSON file with the design of the rule is here below). The standard is simple: **We only accept the governing law from United States**. The logic of the standard can be expressed in a Decision Tree keeping the simplicity:&#x20;

1. **Missed information:** IF the field for the NDA governing law is empty, THEN return error message (Remember the AI can result null if the NDA is not clear).
2. **Under the limit period:** IF the NDA governing law is from US, THEN return passed.
3. **Over the limit period:** IF the NDA governing law is from any other country, THEN return failed and the reason.&#x20;

{% file src="../../.gitbook/assets/Governing_Law_v1.json" %}

The AI Agent node has two hooks, connect the green one to the four Decision Trees recently set.&#x20;

<figure><img src="../../.gitbook/assets/four trees.png" alt=""><figcaption></figcaption></figure>

### 3. Error handle

Drop an **Assign** node below the column of **Business Rule** nodes, and connect the red hook of the **AI Agent** node to it. The red path runs for times out waiting for the AI. Open the **Assign** and create a target to report the error of the LLM, e.g. `AnalyzerError.code` . And write an error code like: AI\_PROCESSING\_ERROR.&#x20;

<figure><img src="../../.gitbook/assets/assign.png" alt="" width="563"><figcaption></figcaption></figure>

Drop on the right of your design an **Append** node and connect all the nodes on the last column of parallel nodes to it. So far there are two kind of errors, the AI time out and the empty fields in the report of the NDA. This node will store one array with all errors from both kind. Please, create a target array called `errors` and drag all the attributes reporting errors to the values to append.&#x20;

<figure><img src="../../.gitbook/assets/append.png" alt="" width="375"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/errro handle.png" alt=""><figcaption></figcaption></figure>

Finally, drop a **Switch** node and connect it from the **Append**. Open it and create a case for Errors in the evaluation. The condition is: IF the error array from the **Append** is not empty, THEN there are errors so go to the mapping for errors, OTHERWISE go to the mapping for redlines. The case configuration requires to drag and drop the object `errors` created in the **Append** node to the condition. Use the function Contains Text and write the text: ERROR. The Default case will cover the 'otherwise' option of the condition. &#x20;

<figure><img src="../../.gitbook/assets/Set Up Conditional Branching for AI Evaluation Errors.gif" alt=""><figcaption></figcaption></figure>

### 4. Generating the final redlines

Now that we have gathered all the necessary values, we can create the final redlines, which will include the validation of the four minimal standards and the references in the original text. To map these values for display in the Decision Flow output, we'll utilize an **Assign** node. In the modal we will map all the information to output properties.

Connect the "Default" option of the **Switch** node to the **Assign** node. Open the node. Put on the "Target" side all output attributes for redlines and references, eight in total. For the redlines, map on the "Source" the results from the four Decision Trees. For the references, map on the "Source" the corresponding results from the AI rule.&#x20;

<figure><img src="../../.gitbook/assets/final assignment.png" alt=""><figcaption><p>Assigning values to Decision Flow Output</p></figcaption></figure>

We'll utilize another **Assign** node to handle the errors. Connect the "AI error in the evaluation" option of the **Switch** node to the _new_ **Assign** node and to the _last_ **Assign** node. If any errors were stored in our errors array, the **Switch** node will direct the flow to the redline **Assign** node to give any processed information, but also it will direct to a node for message error. &#x20;

Put on the "Target" side the output attributes for errors, two in total. For output.errors.types you can map the errors array from the **Append**. For output.errors.message we can use a customised message with the originating party and instructions to deal with the errors:

```
Please check the list of errors.types . 
If some of the rules are mentioned, it means {input.nda.originatingParty} didn't give enough information in the NDA to evaluate the standard, request them to complete the NDA please.
If the type is AI_PROCESSING_ERROR, verify your connection to the LLM and run the rule again.
```

<figure><img src="../../.gitbook/assets/two assign nodes.png" alt=""><figcaption><p>Detail of Switch node directing the process</p></figcaption></figure>

Congratulations! :tada: You've completed the Decision Flow, which might look something like this:

<figure><img src="../../.gitbook/assets/decisionflow with AI (1).png" alt=""><figcaption><p>Decision Flow overview</p></figcaption></figure>

In the next section, we’ll test the Decision Flow with some inputs to ensure it’s functioning correctly. Before proceeding, please double-check that all Decision Flow nodes are fully configured and properly connected.

### 3. Testing the Decision Flow and the AI Agent Rule

Now we can test our rule in Test Bench.

We can click the <mark style="background-color:purple;">**Test Bench**</mark> icon at the beginning of the bottombar. After clicking the icon, the Test Bench will show up at the bottom of the page.&#x20;

Then we can fill in some mock data. We can use the same mock example from above. You can download the document here below as well. Use the specifications of the document to complete the input, and remember to paste the entire text of the NDA in nda.text. Click the <mark style="background-color:green;">**Run**</mark> button and the result will be displayed in right hand side of the Test Bench. Note that you can switch between the **Simple Bench** and the **JSON Bench**.

{% file src="../../.gitbook/assets/Mock_NDA.pdf" %}

<figure><img src="../../.gitbook/assets/proving.png" alt=""><figcaption></figcaption></figure>

{% tabs %}
{% tab title="Testing Input" %}
```json
//Complete the input with the Mock_NDA
{
  "nda": {
    "originatingParty": "Zenith Logic Pty Ltd",
    "disclousingParty": "Vanguard Analytics Inc.",
    "receivingParty": "Zenith Logic Pty Ltd",
    "type": "NDA for PoC information",
    "text": [
      "MUTUAL NON-DISCLOSURE AGREEMENT This Mutual Non-Disclosure Agreement (the \"Agreement\") is entered into as of October 25",
      " 2023 (the \"Effective Date\")",
      " by and between: Vanguard Analytics Inc.",
      " a corporation organized under the laws of Delaware",
      " etc, etc, etc..."
    ]
  }
}
```
{% endtab %}

{% tab title="Testing Output" %}
```json
[
  {
    "redline": {
      "confidentiality_period_years": "passed",
      "governing_law": "failed, governing law is not from US",
      "notice_period_days": "failed, it requires notice in less than 30 days",
      "reciprocity": "passed"
    },
    "reference": {
      "confidentiality_period_years": "continue for a period of ten (10) years",
      "governing_law": "governed by... the laws of New South Wales, Australia",
      "notice_period_days": "providing twenty (20) days prior written notice",
      "reciprocity": "Mutual Non-Disclosure Agreement... Vanguard and Zenith may exchange"
    },
    "errors": {
      "types": {},
      "message": {}
    }
  }
]
```
{% endtab %}
{% endtabs %}

### Summary

The rules of this tutorial were designed to be called by a user when a new NDA arrives and the team want to decide the necessary redlines in real time. The goal was to automate the process such that the system sends the NDA to DecisionRules and retrieve the evaluation of the document with the redlines that must be pointed out. The main features in DecisionRules to achieve this goal are the **AI Agent Rule** and the **Decision Flow**. In this tutorial, we built an **AI Agent Rule** for the analysis of the unstructured data given in the new NDA, getting back the data of the NDA in structured JSON format. The attributes of the JSON were designed to be precise and some of them required by the standards to be evaluated. The second part of this section was the elaboration of a **Decision Flow** to complete the goal in a predictable way. The flow uses the results of the AI rule and runs:

* The evaluation of precise NDA attributes, according to the standards of the company, using **Decision Trees**.
* Because the original NDA is unstructured, the data in the flow may misbehave, and so, the detection of information gaps and the report of times out.
* The presentation of the redlines, with the corresponding references, and in case of misbehaviours, error messages for the solution of relevant gaps or the solution of the connected LLM performance.   &#x20;

To wrap up, let’s go over the management and maintenance of this Decision Flow. Once the rules are built, the Business Users only have to manage the **Decision Trees**. In fact, the Business User not just know the company's standards, but these users have the decision capacity and knowledge to change those standards, so when some of the standards must be changed, for example:

* **The NDA must be reciprocal - to - It is not relevant if the NDA is reciprocal.**
* **We must have minimum 30 days to solve and communicate leaks - to - 20 days.**
* **We must have maximum 15 years for confidentiality - to - 20 years.**
* **We only accept the governing law from United States - to - the law from Australia.**

These changes can be done directly by them, just changing values on Decision Trees, for instance from 15 to 20. See that the roles of the users can be very different, but everyone collaborate to directly on the hand of the right expert, the capacity to make changes in the company's applications for prediction, transparency and velocity. &#x20;

[^1]: 
