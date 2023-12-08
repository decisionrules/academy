---
description: This tutorial will walk you through the creation of a simple Decision Tree.
---

# Create Simple Decision Tree

## How to create a simple decision tree

Let's advance one step at a time.

### 1. Log in

Becoming a superhero is a fairly straightforward process. After entering our [<mark style="color:purple;">login page</mark>](https://app.decisionrules.io/auth/login), you will be able to pass your credentials and log in.

<figure><img src="../../.gitbook/assets/spaces_-MN4F4-qybg8XDATvios_uploads_qLewOTJelEMoVeRYkiu6_image (1).webp" alt=""><figcaption></figcaption></figure>

There are multiple options for user login. If you do not have an account yet, you can [<mark style="color:purple;">create one</mark>](https://app.decisionrules.io/auth/register?type=true-registration). After logging in to the application, the [<mark style="color:purple;">Dashboard</mark>](../../spaces/space-dashboard.md) will be displayed.

<figure><img src="../../.gitbook/assets/spaces_-MN4F4-qybg8XDATvios_uploads_JC9aflM8S2oyWAuEy7CM_image (1).webp" alt=""><figcaption></figcaption></figure>

### 2. Go to Create rule

To display the rule creation pop-up click the <mark style="background-color:purple;">**Create Rule**</mark> button on the sidebar.

<figure><img src="../../.gitbook/assets/spaces_-MN4F4-qybg8XDATvios_uploads_9KAQhbrnEZ6Dfvp2jBTm_image.webp" alt=""><figcaption></figcaption></figure>

### 3. Create a New Decision Tree

You will be prompted to provide a name and choose between **SAMPLE RULE** or **EMPTY RULE.** For now, name the rule as you wish and choose the EMPTY RULE. The new rule will be created and its detail will be displayed. We will continue in the Rule Settings tab.

{% hint style="success" %}
In our case, we will choose an empty tree to walk you through the whole process.
{% endhint %}

### 4. Create First If Block

Click on create business condition.

<figure><img src="../../.gitbook/assets/spaces_-MN4F4-qybg8XDATvios_uploads_KvhgD1xcRYrdSSKJq3iT_image.webp" alt=""><figcaption></figcaption></figure>

### 5. Specify Condition Inside If Block

1\. Click on the first add button inside the if block.&#x20;

<figure><img src="../../.gitbook/assets/spaces_-MN4F4-qybg8XDATvios_uploads_PzMZA4R8lqoGztfkvflh_image.webp" alt=""><figcaption></figcaption></figure>

2\. Dropdown will be shown.

<figure><img src="../../.gitbook/assets/spaces_-MN4F4-qybg8XDATvios_uploads_Wnp0oOc92Cgqp06RD6M0_image.webp" alt=""><figcaption></figcaption></figure>

3\. Click on condition.

<figure><img src="../../.gitbook/assets/spaces_-MN4F4-qybg8XDATvios_uploads_mXXhgSSXDojjVOvHwa6P_image.webp" alt=""><figcaption></figcaption></figure>

4\. Click on the orange dropdown. Here you will choose an input attribute that will later be evaluated when solving the decision tree.

<figure><img src="../../.gitbook/assets/spaces_-MN4F4-qybg8XDATvios_uploads_UpQpLGDipInC7anHL6j7_image.webp" alt=""><figcaption></figcaption></figure>

5\. For simplicity sake, the only input attribute is the "Input attribute" created automatically, when choosing the empty decision tree. Click on the "Input attribute".

{% hint style="success" %}
To learn more about the Input/Output Model, click [<mark style="color:purple;">here</mark>](https://docs.decisionrules.io/doc/decision-tables/input-and-output)
{% endhint %}

<figure><img src="../../.gitbook/assets/spaces_-MN4F4-qybg8XDATvios_uploads_T4wkUTNYwL86tBmf5QQ2_image.webp" alt=""><figcaption></figcaption></figure>

6\. Now click on the empty... text to edit the value.

<figure><img src="../../.gitbook/assets/spaces_-MN4F4-qybg8XDATvios_uploads_AvfY3vL8Vq0fbpNJALaV_image.webp" alt=""><figcaption></figcaption></figure>

7\. Now type in a value to which we will compare the input once solving the decision tree. Let's write "learning" for example. To save the value either click on the save button or press enter.

<figure><img src="../../.gitbook/assets/spaces_-MN4F4-qybg8XDATvios_uploads_pJy8IGmqg23uqAnHrnnl_image.webp" alt=""><figcaption></figcaption></figure>

8\. Now click on the second add button inside the if block.

<figure><img src="../../.gitbook/assets/spaces_-MN4F4-qybg8XDATvios_uploads_vR7xUVZl6Hx0RI70Uifv_image.webp" alt=""><figcaption></figcaption></figure>

9\. Click on then.

<figure><img src="../../.gitbook/assets/spaces_-MN4F4-qybg8XDATvios_uploads_v3zfog39taZlQqEeiCoX_image.webp" alt=""><figcaption></figcaption></figure>

10\. Click on add result.

<figure><img src="../../.gitbook/assets/spaces_-MN4F4-qybg8XDATvios_uploads_SXoqJdaYIeOYwpoTuVJd_image.webp" alt=""><figcaption></figcaption></figure>

11\. Once again, click on the orange button saying "not set" and choose the only Output attribute which was automatically created and is called "Output attribute".

<figure><img src="../../.gitbook/assets/spaces_-MN4F4-qybg8XDATvios_uploads_diQoWMVx9Zfsqz8Nc8Kj_image.webp" alt=""><figcaption></figcaption></figure>

12\. Click on the empty... text and fill in the result value as with the if condition.

<figure><img src="../../.gitbook/assets/spaces_-MN4F4-qybg8XDATvios_uploads_OQ4U5NSwq1D05sG0kJmO_image.webp" alt=""><figcaption></figcaption></figure>

Great, you now know how to create a simple condition :tada:.

### 6. Create Second If Block

To simplify the process, you can click on the settings icon of the first If block and select clone.

<figure><img src="../../.gitbook/assets/spaces_-MN4F4-qybg8XDATvios_uploads_LjhWuZWBXEDotrQXS7Oc_image.webp" alt=""><figcaption></figcaption></figure>

This will create an exact copy of the If block down below.

The only thing to do now is to change the values inside the newly created If block.

<figure><img src="../../.gitbook/assets/spaces_-MN4F4-qybg8XDATvios_uploads_rcFj11smQDb7MQbIkiNM_image.webp" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
These two If blocks are very similar to the If and Else If behavior, if you are familiar with programming concepts.
{% endhint %}

### 7. Create Else Block

Finally we create an Else block. The Else block will be executed whenever none of the above If blocks evaluate to true. In our case, if the Input Attribute is anything else than the value "learning" and "procrastinating".

Now click on the <mark style="background-color:purple;">**Add**</mark> button under the Else If block and add another Else block.

<figure><img src="../../.gitbook/assets/spaces_-MN4F4-qybg8XDATvios_uploads_aYu8VF04qVB9H1mf154P_image.webp" alt=""><figcaption></figcaption></figure>

Now inside the last Else block simply add Then block and fill it out with whatever value you like.

<figure><img src="../../.gitbook/assets/spaces_-MN4F4-qybg8XDATvios_uploads_wE9fz7LEyvynY8tLpwE2_image.webp" alt=""><figcaption></figcaption></figure>

### 8. Test It!

Simply click on the <mark style="background-color:green;">**Test bench**</mark> in the bottom bar.

Type "learning" in the Input Property and click on <mark style="background-color:green;">**Run**</mark> .

<figure><img src="../../.gitbook/assets/spaces_-MN4F4-qybg8XDATvios_uploads_o3h7Ok940biB1jOSbU1u_image.webp" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
You can see that the first block was evaluated.
{% endhint %}

Inputting the word "procrastinating" will return "mission failed".

<figure><img src="../../.gitbook/assets/spaces_-MN4F4-qybg8XDATvios_uploads_QxxjiAlMwrpCd5oKaebC_image.webp" alt=""><figcaption></figcaption></figure>

Finally inputting anything else than these two word will return "unexpected output".

<figure><img src="../../.gitbook/assets/spaces_-MN4F4-qybg8XDATvios_uploads_0vQ5E6yQQLcIOA26NmYy_image.webp" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
More information can be found [<mark style="color:purple;">here</mark>](https://docs.decisionrules.io/doc/decision-trees/decision-tree-designer).
{% endhint %}
