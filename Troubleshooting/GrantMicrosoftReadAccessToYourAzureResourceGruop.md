If your Dynamics 365 Test Drive is deployed to Azure, but not functionally correctly, you may need to engage Microsoft Test Drive developer team for assistance. 

Since the Azure Functions and Azure Logic Apps are hosted in your Azure Subscription, Microsoft Test Drive developers cannot see how your Test Drive resources are configured, or gain access to any of your Logic App or Function logs.

Rather than having to manually pull the logs yourself and send to Microsoft, or schedule a call with Microsoft to troubleshoot the issue, you can leverage Azure RBAC (Role Based Access Control) to grant Microsoft Test Drive developer team read access to your Azure Resource Group that contains your Test Drive resources. This allows Microsoft Test Drive developer team to easily your configuration and execution logs to help mitigate the issue.
