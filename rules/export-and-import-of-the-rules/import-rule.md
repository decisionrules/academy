# Import Rule

When importing a rule, you can create a new rule, a new version of an existing rule, or overwrite an existing rule version.

{% hint style="info" %}
_For Decision Tables, the rule file can have the formats: <mark style="color:purple;">JSON</mark> or <mark style="color:purple;">XLSX</mark>. Other rule types: Decision Tree, Scripting Rule, Decision Flow and Integration Flow have a single export option - <mark style="color:purple;">JSON</mark> format._
{% endhint %}

### Importing a new rule

Create a new rule in three places:

1. Import the rule in the folders structure directly. Open "Rules" on the side menu. In the folders structure of your Rule List you can find the  <mark style="background-color:purple;">**...**</mark>  button next to  <mark style="background-color:purple;">**+ Create**</mark>  in the search bar. Click on the  <mark style="background-color:purple;">**...**</mark>  and press  <mark style="background-color:purple;">**Import**</mark> . A new rule will be created immediately.&#x20;

<figure><img src="../../.gitbook/assets/Import 1.png" alt=""><figcaption><p><mark style="color:purple;">Import a Rule in Folder Structure</mark></p></figcaption></figure>

When you click on “Import”, you will be prompted to drop or choose a file from your system containing the rule.

<figure><img src="../../.gitbook/assets/Import create.png" alt=""><figcaption></figcaption></figure>

Once your rule file has been selected, click the <mark style="background-color:purple;">Import</mark> button.

{% hint style="info" %}
_You can import one file at a time._
{% endhint %}

### Import a new version or overwrite an existing version

#### Import to:

You can import a rule as a new version of an existing rule, when you import the rule through a currently existing rule:

1. For using an existing rule you have two methods. First, Open "Rules" on the side menu. In the folders structure of your Rule List you can find a  <mark style="background-color:purple;">**...**</mark>  button corresponding to each rule. Click on the correspondent  <mark style="background-color:purple;">**...**</mark>  and press  <mark style="background-color:purple;">**Import**</mark> . Now, you can either create a new version of the rule or overwrite over the existing version.&#x20;

<figure><img src="../../.gitbook/assets/Import 2.png" alt=""><figcaption><p><mark style="color:purple;">Import a Rule in Folder Structure</mark></p></figcaption></figure>

2. Or just open your particular rule. Go to the top bar menu and select  <mark style="background-color:purple;">**...**</mark>  next to  <mark style="background-color:purple;">**+ Integrations**</mark> . A dropdown menu will appear. Select  <mark style="background-color:purple;">**Import**</mark> , and you have two options, create a new version of the rule or overwrite over the existing version.&#x20;

<figure><img src="../../.gitbook/assets/Import 3.png" alt=""><figcaption><p><mark style="color:purple;">Import a Rule in Business Rules</mark></p></figcaption></figure>

**Import version**

When you click on “Import”, “Import version dialog” will appear. There you select if you want to import the file to:

1. Create a new version of the rule
2. Overwrite an existing version

{% hint style="danger" %}
_Overwriting the version is an irreversible action, the overwritten rule is lost. Please use this option wisely._
{% endhint %}

After selecting the method of import drop or choose a file from your system containing the rule.

<figure><img src="../../.gitbook/assets/Import Overwrite.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
_You can import one file at a time._
{% endhint %}

{% hint style="info" %}
_These are manual methods of exporting rules. Using Management API methods and external tools you can export rules in one click. More information about API functioning can be found in documentation link_ [_<mark style="color:purple;">here</mark>_](https://app.gitbook.com/s/-MN4F4-qybg8XDATvios/api/api-introduction)
{% endhint %}
