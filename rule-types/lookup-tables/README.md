# Lookup Tables

## Introduction

Lookup Tables are not rules in the proper sense; however, they are a fundamental component of many business logic workflows because they store the data used during the execution of other rule types.

The first step in understanding this key element is distinguishing it from two similar concepts: our **Decision Tables** and the term "lookup table" as it is used in general data structure practices. Let’s start with Decision Tables:

By comparison, Decision Tables act as a **Decision Engine**, whereas Lookup Tables serve as a **Retrieval Engine**. The former evaluates complex conditions using calculations and variables to get results, while the latter is designed for fast and efficient data retrieval. Lookup Tables serve as a repository for your data; Decision Tables process that data to reach a specific decision. Even though both tables may look similar externally, they have different goals, which in turn drive their specific design and performance.

It is also important to distinguish this from similar concepts in other fields. In general data literature, the term "lookup table" is actually closer to our Decision Tables than the Lookup Tables presented here. Traditionally, a "lookup table" is a data structure that replaces runtime calculations with a table of pre-calculated results. By replacing mathematical operations with direct memory access, it increases speed. However, this usually implies a mapping from multiple inputs to multiple outputs. Lookup Tables in DecisionRules are different: the only way to retrieve the data in a row is through a single value—the **Primary Key**.

In conclusion, a Lookup Table is a structured way to store and retrieve reference data using a high-performance key-value approach.

<figure><img src="../../.gitbook/assets/lookup tables.png" alt=""><figcaption></figcaption></figure>

## Look up Table Designer

Externally, a Lookup Table also resembles an Excel spreadsheet; it is divided into columns and rows where you can enter values into cells. However, it is simpler because it does not use functions. The table is conceptually divided into two parts: the column for the Primary Key and the columns storing all the data related to each key.

Because of the architectural differences mentioned above, these tables do not use an Input/Output model. Instead, the only attributes used to call the rule are the **Primary Key** and, optionally, a specific **Output Column**. If the output column is not specified, the rule retrieves values from all columns associated with that key.

<figure><img src="../../.gitbook/assets/input lookup.png" alt=""><figcaption></figcaption></figure>

#### Adding and building columns

The columns in a Lookup Table define the "shape" and structure of your data. Instead of "If" and "Then" columns, you simply define a Primary Key and as many standard data columns as your use case requires.

Setting up this structure is a visual and intuitive process. To expand your table, simply click the "**+**" sign located next to your rightmost column. If you need to rename a column to better reflect your data, you can do so instantly by _double-clicking_ the header or using the _right-click_ context menu.

The designer also allows for easy organization; if you decide a different column order would be more readable, you can _click and drag_ headers to reposition them. To remove a column, just select **Delete Column** from the header’s dropdown menu and continue with your design.

{% hint style="warning" %}
**The Primary Key Rule:**\
The Primary Key column is the "anchor" of your table and is always pinned to the far left. To ensure data integrity, it cannot be moved, deleted, or changed once the table is established. If your project requires a different Primary Key, you will need to create a new Lookup Table.
{% endhint %}

<figure><img src="../../.gitbook/assets/better columns.png" alt=""><figcaption></figcaption></figure>

#### Adding and building rows

Once your structure is in place, the body of the table is where you bring your data to life. Adding a single record is as simple as clicking the  <mark style="background-color:purple;">**+ Add Row**</mark>  button in the bottom toolbar, which generates an empty row at the end of your list.

For more complex data management, the designer offers a suite of Row Operations accessible via a _right-click_ on any row header. From here, you can **Duplicate** a row to quickly create similar records, or **Insert** new rows exactly where you need them—either above or below your current selection. If you are handling large datasets, you can save time by editing **multiple rows at once**; simply hold **Ctrl** (or **Cmd**) to select specific rows, or use **Shift** to highlight an entire range.

<figure><img src="../../.gitbook/assets/better row.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
For more details on the Lookup Table Designer, please consult our [official documentation](https://docs.decisionrules.io/doc/rules/lookup-table/lookup-table-designer).&#x20;
{% endhint %}

#### Primary Key Validation

Because Lookup Tables are built for absolute precision, the **Primary Key** is the most critical element of your table. To prevent errors in your decision logic, the designer acts as a guardian, automatically validating your keys in real-time as you type.

If you accidentally enter a key that already exists, the cell will immediately turn **red**, and a validation error will notify you of the **Duplicate Detection**. Similarly, the system ensures you never leave a "blind spot" in your data; because every row must be findable, the **Empty Key** validation will highlight any blank primary key cells that require attention.

To keep your workflow smooth, you cannot save a version of the table that contains errors. If you are working with thousands of rows, you don't need to hunt for mistakes manually—simply use the **Error Navigator** in the toolbar to jump directly to any row that needs a correction.
