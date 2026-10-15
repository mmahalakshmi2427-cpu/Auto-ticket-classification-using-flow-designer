Auto Ticket Classification Using Flow Designer
1. Project Overview

Auto Ticket Classification Using Flow Designer is an automation project developed using ServiceNow Flow Designer. The project automatically classifies IT support tickets based on the information provided in the ticket's short description and description fields.

The primary goal is to reduce manual effort, improve ticket classification consistency, and help IT support teams process incidents more efficiently.

The classification can be implemented using predefined keyword-based conditions or enhanced with ServiceNow Predictive Intelligence for machine-learning-based classification.

2. Objectives
Automatically classify newly created incident tickets.
Reduce manual intervention in ticket categorization.
Improve the consistency and accuracy of ticket classification.
Update incident categories automatically.
Notify users or support teams when required.
Improve the efficiency of IT service management.
3. Technologies Used
Platform: ServiceNow
Automation Tool: Flow Designer
Module: Incident Management
Table: Incident [incident]
Workflow Components: Triggers, conditions, actions, and record updates
Optional AI Enhancement: Predictive Intelligence
4. Problem Statement

In a traditional IT support system, support agents manually review incoming tickets and assign appropriate categories. This process consumes time and may lead to inconsistent classification or delays in ticket assignment.

This project automates the classification process by analyzing ticket information and identifying the appropriate category using predefined rules or a trained machine-learning model.

5. Proposed Solution

The proposed solution uses ServiceNow Flow Designer to trigger an automated workflow whenever a new incident ticket is created.

The workflow reads the incident details, determines the appropriate category, updates the incident record, and optionally sends a notification.

Workflow Process
A user creates an incident ticket.
Flow Designer detects the newly created incident.
The flow reads the short description and description fields.
The classification logic identifies the appropriate category.
The incident record is updated with the selected category.
An optional notification is sent to the user or support team.

Workflow:

Incident Created → Read Ticket Details → Classify Ticket → Update Category → Send Notification

6. Ticket Classification Logic

The following table illustrates an example of keyword-based classification rules.

Keywords or issue	Assigned category
Wi-Fi, internet, network connection	Network
Keyboard, monitor, printer, hardware	Hardware
Password reset, login failure, account access	Software or account-related category, depending on configuration
Slow computer, system lag, performance issue	Performance-related category

Note: These are illustrative classification rules. Configure the categories to match the actual choices available in your ServiceNow instance.

7. Flow Designer Implementation
Step 1: Create a New Flow
Log in to your ServiceNow instance.
Navigate to Process Automation → Flow Designer or Workflow Studio, depending on your release.
Select New → Flow.
Enter the flow name: Auto Ticket Classification.
Add a suitable description and save the flow configuration.
Step 2: Configure the Trigger

Configure the flow to run when a new incident is created.

Trigger type: Record
Trigger condition: Created
Table: Incident [incident]

This trigger starts the workflow whenever a new incident record is created.

Step 3: Configure Classification Logic

Choose one of the following approaches:

Option A: Keyword-based classification

Add conditions to check the short description or description.
Use If/Else branches to identify matching keywords.
Select the corresponding category for each condition.
Define a default category for tickets that do not match any rule.

Option B: Machine-learning-based classification

Configure a trained and active ServiceNow Predictive Intelligence classification solution.
Add the Classification Prediction action.
Provide the incident record as the input.
Use the prediction result to determine the category.

The machine-learning approach requires the relevant plugins, permissions, and a trained classification solution.

Step 4: Update the Incident Record

Add an Update Record action.

Configure the action as follows:

Record: Incident record from the trigger.
Table: Incident [incident].
Field to update: Category.
Value: The category identified by the classification logic.

Ensure that the selected category is a valid choice for the incident category field.

Step 5: Configure Notifications (Optional)

Add an email notification action if the project requires it.

The notification can inform the requester or support team that the incident has been classified. Include the incident number and category where appropriate.

Step 6: Save and Activate
Review the trigger and all actions.
Save the flow.
Activate the flow.
Create test incidents to verify the classification behavior.

For machine-learning-based implementation details, refer to the official ServiceNow Predictive Intelligence Flow Designer documentation.

8. Example

Input ticket

Short description: Wi-Fi is not working in the office
Description: The user cannot connect to the office wireless network.

Expected output

Detected issue: Network connectivity
Assigned category: Network, if configured as a valid category
Result: The incident record is updated automatically.
9. Testing

Test the flow using different incident descriptions and verify the resulting category.

Test case	Input	Expected result
TC01	Wi-Fi is not working	Network
TC02	Printer is not responding	Hardware
TC03	Computer is running slowly	Performance-related category
TC04	Password reset required	Account-related category
TC05	Unrecognized issue description	Default category or manual review

These test cases should be adjusted to match the actual classification rules and configured category choices.

10. Key Features
Automated incident classification.
Reduced manual ticket processing.
Consistent application of classification rules.
Automatic incident record updates.
Optional email notifications.
Flexible workflow configuration.
Potential integration with machine-learning-based classification.
11. Benefits
Saves time for IT support agents.
Reduces repetitive manual work.
Improves consistency in incident categorization.
Supports faster ticket triage.
Provides a foundation for further IT service management automation.
12. Future Enhancements

The project can be extended with the following capabilities:

Machine-learning-based ticket classification.
Automatic priority assignment.
Automatic assignment to support groups.
Subcategory prediction.
Integration with virtual agents and email channels.
Confidence-based classification with manual review for uncertain predictions.
Reporting dashboards for classification accuracy and workflow performance.
13. Limitations
Keyword-based classification depends on the configured rules.
Ambiguous descriptions may be classified incorrectly.
New issue types may require additional rules or model training.
Machine-learning classification depends on the quality of the training data and the availability of the required ServiceNow capabilities.
14. Expected Outcome

After successful implementation, newly created incident tickets are classified automatically according to the configured rules or machine-learning predictions. The corresponding incident category is updated, reducing manual effort and improving the consistency of the incident management process.

15. Conclusion

The Auto Ticket Classification Using Flow Designer project demonstrates how ServiceNow workflow automation can simplify IT incident management. By automating ticket classification and incident record updates, the solution helps support teams reduce repetitive tasks, improve consistency, and process incoming tickets more efficiently.

The project can be further enhanced with Predictive Intelligence, automated assignment, and priority prediction to create a more intelligent IT support workflow.
documentation link:
https://drive.google.com/file/d/1YiDj5Id8A6rriC8Dro0G3-QIw2jpWbjp/view?usp=sharing
demo link:
https://drive.google.com/file/d/13EArT4EHqitgv-65avueHPohhcMt-9Nm/view?usp=sharing
