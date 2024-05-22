Creating an Azure Runbook

Introduction
Azure Automation Runbooks allow for the automation of repetitive tasks within Azure, improving efficiency and reducing manual intervention. This documentation provides a comprehensive guide to creating an Azure Runbook using the Azure Portal.
Prerequisites

Before creating an Azure Runbook, ensure you have:

    An active Azure subscription.
    Sufficient permissions to create resources in your Azure subscription.
    Azure Automation account created.
    For convenience, you may want to either add a service account credential or turn on system assigned identity and assign your automation account the proper permissions

Steps to Create an Azure Runbook
1. Access the Azure Portal

    Navigate to the Azure Portal.
    Log in with your Azure account credentials.

2. Navigate to Automation Accounts

    In the left-hand menu, select All services.
    In the search bar, type Automation Accounts and select it from the list.
    Choose the appropriate Automation Account or create a new one if needed.

3. Create a New Runbook

    Within your Automation Account, select Runbooks from the left-hand menu.
    Click on + Create a runbook.

4. Configure the Runbook

    In the Add Runbook pane, enter the following details:
        Name: Provide a meaningful name for the Runbook.
        Runbook type: Select PowerShell or Python based on your scripting preference.
        Description: Optionally, add a description to explain the purpose of the Runbook.
    Click Create to proceed.

5. Author the Runbook

    After creating the Runbook, you will be redirected to the Edit PowerShell Runbook or Edit Python Runbook page.
    Use the editor to write your automation script. For example, a PowerShell Runbook might look like this:

    Powershell:
 ```powershell
###This starts the example load balancer in an example subscription.###
###Connect to Azure
Connect-AzAccount -Identity
###Select the Azure Subscription named app-example-001
Select-AzSubscription -SubscriptionName ‘examplesubscription’
###Select the example application gateway
$AppGw = Get-AzApplicationGateway -Name examplename -ResourceGroupName exampleresourcegroup
###Start the app gateway
Start-AzApplicationGateway -ApplicationGateway $AppGw
```


  Click Save to store your script.

6. Test the Runbook

    To ensure your Runbook works as expected, click Test pane.
    In the Test pane, click Start to execute the Runbook.
    Observe the output and make any necessary adjustments to the script.

7. Publish the Runbook

    Once you are satisfied with the script, click Publish to make the Runbook available for use.
    Confirm the publishing action in the dialog box.

8. Schedule or Start the Runbook

    To schedule the Runbook, navigate to the Runbook's page and click on Schedules.
    Click + Add a schedule to set up a new schedule, specifying the start time, recurrence, and time zone.
    To start the Runbook manually, click Start on the Runbook's page.

Managing Runbooks

    Monitor Runbooks: Use the Jobs tab to monitor the status of Runbook executions.
    Modify Runbooks: Edit the script of existing Runbooks as needed to adapt to changing requirements.
    Assign Permissions: Control access to Runbooks by managing user roles and permissions within the Automation Account.

Best Practices

    Version Control: Maintain version control of your Runbook scripts to track changes and revert if necessary.
    Error Handling: Implement error handling in your scripts to manage exceptions and ensure reliability.
    Testing: Thoroughly test Runbooks in a non-production environment before deployment.
    Documentation: Document your Runbooks with clear descriptions and comments within the scripts for maintainability.

Conclusion

Creating an Azure Runbook involves several steps from configuring and authoring to testing and publishing. Following this guide ensures a streamlined process for automating tasks within your Azure environment, contributing to operational efficiency and consistency.
