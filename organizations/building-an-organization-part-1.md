---
description: >-
  On this page, we will build a sample Organization to learn how to use and
  navigate each section of the Organization menu.
---

# Building an Organization Part 1

The options in your menu are:

* [Members](building-an-organization-part-1.md#members)
* [Resources](building-an-organization-part-1.md#resources)
* [Departments](building-an-organization-part-1.md#departments)
* [Policies](building-an-organization-part-2.md#policies)
* [Statistics](building-an-organization-part-2.md#statistics)
* [Settings](building-an-organization-part-1.md#settings)

On this page, you will learn to use each of these options directly through the creation of a concrete mock Organization. To offer clarity on the main building blocks, you will find a group of useful definitions at the beginning of each section.

We can start by [creating a new Organization](what-is-an-organization.md#new-organization) called: _**orgAcademy**_. We will focus on a possible use case for Risk; for this mock example, we will require 5 users and 3 Spaces.&#x20;

{% hint style="info" %}
For detailed technical specifications regarding these functionalities, please refer to the official [documentation](https://docs.decisionrules.io/doc/organization/members).&#x20;
{% endhint %}

## Members

#### Definitions

* **Members:** A member is a user with access to some of the Spaces in your organization or to the settings of the organization. The access is given through the user's email address.&#x20;
* **Status:** Each member is at each time only in one of the three main status: Active, Inactive, Pending. This status describes the existence of the member in the Organization.&#x20;
* **Organizations Roles:** The [four possible roles](building-an-organization-part-1.md#four-organization-roles) within an organization define the four set of permissions a specific member can receive.

#### Construction

People are the heart of any Organization, so we will start by adding all the users who will participate.

First, click on "Members" in the left-hand menu. On the new screen, navigate to the far right and click the button in the top corner:  <mark style="background-color:purple;">**+ Invite Member**</mark> .&#x20;

Now, you can fill in the information to register your first user. In this example, the user is a risk manager who will update risk standards in Decision Tables. You will need:

1. Email address: (e.g. user.one@decisionrules.io)
2. Role of the user at the Organization level: (e.g. Member)

Don’t worry about the "Team" field for now; simply select **"Invite."** You are all set!&#x20;

<figure><img src="../.gitbook/assets/Invite a New Member to Your Organization.gif" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
A notification will pop up after the invitaion to confirm that you understand the steps your users must follow to accept the invitation.
{% endhint %}

You can follow these same steps to invite the remaining members.

| User description                                                        | Email Address               | Organizations Role |
| ----------------------------------------------------------------------- | --------------------------- | ------------------ |
| A risk consultant that change the risk standards on the Decision Tables | user.two@decisionrules.io   | Member             |
| A risk director in charge of the approvals                              | user.three@decisionrules.io | Admin              |
| A developer in charge of the integrations                               | user.four@decisionrules.io  | Member             |
| A developer in charge of the integrations                               | user.five@decisionrules.io  | Viewer             |

{% hint style="info" %}
**A Note on Terminology:** The term "Member" has two meanings. It is the general name for users within an Organization, but it is also the name of the Role for the most basic permission level.
{% endhint %}

The new members will appear in your list of members, showing their status, role, and other relevant data.

#### Viewing and Modifying Members

* **To View Profiles:** Click on a member's email address. A **details panel will appear**, allowing you to inspect specific user attributes.
* **To Revoke Access:** If you need to remove a user or cancel an invitation, click the **three-dot icon (⋮)** on the right side of the member row and select the remove option from the action menu.

<figure><img src="../.gitbook/assets/remove 1.png" alt=""><figcaption></figcaption></figure>

## Resources

#### Definitions

* **Spaces:** A Space is a container for a set of rules. Visually, it is the interface where you organize your folders and rules in one place. The goal of a Space is to clarify which rules share common settings (such as API Keys or Connectors) and can be connected to one another.
* **Teams:** A Team is a group of members. Teams offer an advantage because they save time and effort; instead of setting up members one by one, you can simply change a Team's configuration and all members will automatically inherit the new properties.
* **Space Roles:** The two default roles (Editor and Reader) define two basic sets of permissions for members within a Space. At the Space level, you can also create more granular roles according to your preferences.

#### Construction

#### Creating Spaces

The second step is to create the Workspaces where your members will manage the rules.\
Click on "Resources" in the left-side menu. The first tab you will see on this screen is "Spaces". Navigate to the far right and click the button in the top corner:  <mark style="background-color:purple;">**+ Add Space**</mark> .&#x20;

To give existence to your Space, only one field is mandatory: The Space Name.&#x20;

We will call the first Space: **Risk Development**. Although the other two fields are optional, we can establish a stable structure by assigning members right away. For this Space, all five members will have access with the **Editor** role. Once this is done, select "Create".

{% hint style="info" %}
Note: The options available in the Team and Role dropdown lists depend on your configurations in the Teams and Space Roles tabs.
{% endhint %}

<figure><img src="../.gitbook/assets/Create a New Space and Assign Member Roles.gif" alt=""><figcaption></figcaption></figure>

Repeat the process for the other two Spaces:

| Space Name      | Members and roles                                                                                                                                              |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Risk Testing    | <p>user.one@decisionrules.io: Editor<br>user.four@decisionrules.io: Editor</p><p>user.three@decisionrules.io: Editor<br>user.five@decisionrules.io: Editor</p> |
| Risk Production | <p>user.three@decisionrules.io: Editor<br>user.five@decisionrules.io: Editor</p>                                                                               |

{% hint style="info" %}
If you want more restrictions, some members can be assigned as a **Reader** (as the name suggests, they can see rules but lack permission to make changes).&#x20;
{% endhint %}

#### Managing Teams

Thinking of future use cases, we want to create a team for Developers to help build Spaces faster. Switch from the "Spaces" tab to the "Teams" tab. Again, go to the far right and select  <mark style="background-color:purple;">**+ Add Team**</mark> in the top corner. Only the Name and Color of the Team are mandatory. For this instance, our team will use the purple color and the name: **Devs**.

<figure><img src="../.gitbook/assets/Create a New Team and Add Members.gif" alt=""><figcaption></figcaption></figure>

Description, Department, and Members are optional (in fact, teams can be empty). After the team is created, you can always edit these fields, including the name and color.

#### Defining Advanced Space Roles

Finally, switch to the "Space Roles" tab. Go to the top right corner and click  <mark style="background-color:purple;">**+ Add Role**</mark> . We want to create a specific new role, called: **Trees Master**.&#x20;

In the role editor, begin by entering the name. Since we want a highly customised set of permissions, switch from "Simple Permissions" to "Advanced Permissions". We will enable the following capabilities for this role:

* _Basic Rule Permissions:_ Create Rule, Import Rule, View Rule settings.
* _Decision Trees:_ (All permissions).
* _Test Bench:_ Run Test Bench.
* _Tests:_ Create/Edit Test, View Test Run.

Select "Create" and our new role is ready.&#x20;

<figure><img src="../.gitbook/assets/Create a Custom Role with Specific Permissions.gif" alt=""><figcaption></figcaption></figure>

From now on, you can assign this Space role to any of your members.

## Departments

#### Definitions

* **Departments:** A department is a subset of the resources within the Organization. It provides management control over a specific group of Spaces, including control over teams and roles restricted to that group.

#### Four Organization Roles:

* Definitions for each role:
  * **Member:** The entry-level role. A user with this role cannot see any Organization-level information; they are limited to receiving Space roles and working within those assigned Spaces.
  * **Viewer:** This role has the same permissions as a Member, plus the ability to view Organization settings.
  * **Admin:** This role includes Viewer permissions, plus the ability to manage members, resources, and policies throughout the Organization.
  * **Owner:** This role has the same permissions as an Admin, plus the ability to view and change Billing information, the Organization’s name, and other core settings.
* **Manager:** This is a specialized role designed to grant Admin permissions to a user with a Viewer role, but only within specific departments.&#x20;

#### Construction

For our sample Organization: _**orgAcademy**_, we will create a demonstration department called: **Non-prod environments**.

Click on **"Departments"** in the left-side menu. Navigate to the far right and click the top-corner button:  <mark style="background-color:purple;">**+ Add Department**</mark> . To give existence to your department, only the Department Name field is mandatory. Once named, the department can be created.

<figure><img src="../.gitbook/assets/Create a New Department in Your Organization.gif" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
You do not always have to assign a Manager, because any Admin in the Organization already has the authority to control any department.
{% endhint %}

#### Step-by-Step: Assigning Spaces to Departments

Now, click on the department's name and **a new panel will open** with tabs similar to the [Resources](building-an-organization-part-1.md#resources) section. From here, you can either repeat the previous process to create new Spaces for this department, or you can edit existing Spaces to assign them here. We will demonstrate the latter.

1. Click on "Resources" in the left-side menu.
2. Select the Space you want to edit. A new window displaying the users of that Space will appear.
3. Go to the far right and click the top-corner button: **Update Space**.
4. In the settings module that pops up, change the Department option to **Non-prod environments**.
5. Select **"Update"** and the process is complete.

By grouping Spaces into Departments, you can now apply more granular administrative controls and keep your decision-making environment organized.

<figure><img src="../.gitbook/assets/Assign a Department to a Workspace.gif" alt=""><figcaption></figcaption></figure>

**Congrats!** The basic settings for your Risk Spaces are complete and your team can begin rule creation right away. Before checking the Rule features, however, we will finish our tour of the Organization menu on the next page to understand the sources of reports and core information.

***
