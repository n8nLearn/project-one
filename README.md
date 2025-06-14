# Project: Personalized Lead Follow-up Automation

## Introduction

This is your first major project and it will combine everything you've learned so far about n8n, from understanding the interface and nodes to handling data and credentials. You are going to build a practical, real-world automation that takes a list of sales leads, sends each one a personalized follow-up email, and updates your tracking sheet automatically.

This project will test your ability to connect different services and manipulate data to create a dynamic and useful workflow. While the individual steps use concepts you've already covered, combining them to build a functioning, multi-step automation is the real challenge. It is up to you to figure out how to implement the requirements.

## Assignment

You can find the starter assets for this project, including the lead list (`leads.xlsx`), in the root of this GitHub repository.

Your task is to build an n8n workflow that accomplishes the following:

1.  **Set up your workflow and data source.** Your workflow should be triggered manually for now. Add a node that can read all the data from the provided `leads.xlsx` file.

2.  **Isolate and process a single lead.** Before trying to automate the whole list, your workflow should correctly process just the *first* lead from the spreadsheet. Inspect the output of your sheet-reading node to understand the JSON data structure.

3.  **Construct a dynamic email message.** Add a step to your workflow that prepares the email. This step must use an expression to generate a personalized opening line. If the lead's `job_title` contains the word "Manager", the message should begin with "Hi [FirstName], as a manager at [Company], you understand the importance of...". Otherwise, it should begin with the more generic "Hi [FirstName], I'm reaching out because...". The body of the email should be professional and concise.

4.  **Send the personalized email.** Using your Gmail credentials, add a node that sends the email you constructed in the previous step. The email should be sent to the lead's email address from the spreadsheet, and the subject line should be "Following up".

5.  **Log the result.** After an email is successfully sent, your workflow must update the spreadsheet. Add a node that writes the text "Email Sent" into the `status` column for the corresponding lead's row.

6.  **Process all leads.** Modify your workflow so that it no longer processes just the first lead. It must now iterate through every lead from the spreadsheet, performing the personalization, sending, and logging steps for each one.

7.  **Address potential issues.** Ensure your workflow is robust.
    * The workflow should not fail if it encounters an empty row in the spreadsheet.
    * The workflow should not attempt to send an email if the `email` field for a lead is blank.
    * Make sure that if you run the workflow again, it does not re-send emails to leads who already have "Email Sent" in their `status` column.
