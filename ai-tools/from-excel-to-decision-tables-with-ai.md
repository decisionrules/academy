# From Excel to Decision Tables with AI

Use AI Assistant to turn business requirements from a spreadsheet into a Decision Table you can review, test, and run in DecisionRules.

## Bring Your Business Logic into DecisionRules

Your business rules may already exist in Excel: pricing conditions, eligibility criteria, discount policies, or approval thresholds. You may also have decision tables in another application that you want to bring into DecisionRules.

AI Assistant can help you translate these requirements into a Decision Table. Attach your spreadsheet, explain the decision you want to automate, and let **Decision Table Architect** prepare the rule.

This helps you move from a document describing a decision to a rule your application can execute.

## Watch the Walkthrough

See how an existing loan grading table is exported to Excel and recreated in DecisionRules with AI Assistant. The video also shows how to generate test input and run the resulting table in Test Bench.

{% embed url="https://www.youtube.com/watch?v=0esgD8iwxK8" %}

## 1. Prepare Your Excel File

Start with an Excel file containing the business logic you want to bring into DecisionRules. You can use an existing spreadsheet or export a decision table from another application.

In the video, the source is a loan grading table with 12 rows exported from Decision Center.

Check that your file includes the conditions and expected outcomes needed to understand the decision. If it contains several sheets or unrelated policies, identify the part you want the Assistant to use.

## 2. Ask AI Assistant to Create the Table

Open **AI Assistant** from the **Rules List** and select **Decision Table Architect**. Attach your Excel file, explain what you want the Assistant to create, and send your request.

For example:

> Create a Decision Table from the attached Excel file.
>
> Preserve the conditions, thresholds, and output values from the source table. Ask me if anything is unclear or if the policy does not specify a result for an input.

You do not need to design the table's rows and columns yourself. Focus on the business decision and the behavior you expect.

If the Assistant asks for a missing detail, answer in the same chat so it can continue preparing the table.

## 3. Import and Review the Rule

When the proposal is ready, review its summary and select **Import Rule** to create the Decision Table in your space and open it in the editor.

Compare the generated table with the original spreadsheet. Check its inputs, outputs, conditions, thresholds, calculations, and fallback behavior.

The proposal does not create a rule in your space until you select **Import Rule**.

## 4. Prepare Test Data

You can enter your own input data directly in **Test Bench**, or ask AI Assistant to generate test input for the table.

For example:

> Generate test input for this Decision Table.

Review the generated input, then select **Apply** to place it in Test Bench.

When you already have test cases for the original spreadsheet or rule, use them to check that the new table preserves the expected behavior.

## 5. Run the Test and Check the Result

Select **Run** in Test Bench. Inspect the output and see which rows and conditions matched your input.

Repeat the test with different inputs. Include typical cases, values exactly at a threshold, and inputs that should trigger exceptions or fallback behavior.

Compare the results with the expected outcomes from your original requirements. If you find a difference, review the logic and ask AI Assistant to prepare a correction. Inspect and test any changes before saving or publishing the rule.

## When Your Requirements Need More Than One Rule

Some specifications describe several separate decisions and the order in which they must run.

For these cases, use **Process Architect** to plan and generate multiple rules together with the Decision Flows that connect them. See [Process Architect](process-architect.md) in this section for a worked example.

_For more details, see_ [_Create and Edit Decision Tables in the documentation_](https://docs.decisionrules.io/doc/ai-assistant/ai-assistant-features/decision-tables)_._
