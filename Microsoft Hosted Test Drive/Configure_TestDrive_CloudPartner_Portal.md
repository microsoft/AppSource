# Configure Microsoft Hosted Test Drive in Cloud Partner Portal

1. Login to Cloud Partner Portal - https://cloudpartner.azure.com
2. If you are not able to access the above link, you need to submit a request [here](https://appsource.microsoft.com/en-us/partners/list-an-app) to publish your application. Once we review the request, you will be granted access to start the publish process. 
3. Navigate to existing offer or create a new offer.
4. Select the Test Drive in Editor to see the Test Drive Template. 
5. Select 'Yes' for 'Enable a Test Drive' option.

![](https://github.com/Microsoft/AppSource/blob/patch-1/Images/EnableTestDrive.PNG)

![](https://github.com/Microsoft/AppSource/blob/patch-1/Images/TestDriveTemplateInCPP.PNG)

6. Update the following Technical configuration values -
    * Type of Test Drive - Choose Microsoft Hosted option
    * Provide the Max Concurrent Test Drives number.
    * Provide the Test Drive experience duration to user in Hours.
    * Provide the Instance URL.
    * Provide the Azure Tenant ID. Login to Azure portal and navigate to AAD from Panel -> Select Properties from menu blade -> Get the Directory ID.
    * Create a new App to get the Azure App details using [linK](https://github.com/Microsoft/AppSource/blob/patch-1/Microsoft%20Hosted%20Test%20Drive/Setup-your-Azure-subscription-for-Dynamics365-Microsoft-Hosted-Test-Drives.md) 
    * Provice Azure AD App Id, Azure AD App key and Azure AD Tenant Name
    * Provide the Instance Web API Url - Odata API to access the shared Instance data during provisioning and deporivisiong.
    *. Provide the Role Name. Example - "salesperson"
    
