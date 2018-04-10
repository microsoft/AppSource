# Configure Microsoft Hosted Test Drive in Cloud Partner Portal

1. Login to Cloud Partner Portal - https://cloudpartner.azure.com
2. If you are not able to access the above link, you need to submit a request [here](https://appsource.microsoft.com/en-us/partners/list-an-app) to publish your application. Once we review the request, you will be granted access to start the publish process. 
3. Navigate to existing offer or create a new offer.
4. Select the Test Drive in Editor to see the Test Drive Template. 
5. Select 'Yes' for 'Enable a Test Drive' option.

![](https://github.com/Microsoft/AppSource/blob/patch-1/Images/EnableTestDrive.PNG)

6. Add an appropriate description of your application. Like what your application is doing, so the customers get to know about your application and go for Test Drive.
7. Upload a detailed user manual which helps customers to understand how to use your application. 
8. Upload Test Drive demo video. However, it is an optional field, but demo video will give better clarity about your application, so the customer can easily build the understanding.

9. Update following Technical configuration details about Test Drive.

    *    Type of Test Drive - Choose Microsoft Hosted option
    *    Provide Max Concurrent Test Drives number. The provided number will allow the same count of simultaneous users to do Test Drive.
    *    Provide Test Drive experience duration to a user in Hours. Once the provided time is over, the customer will get removed from the instance. So you need to identify a sufficient time duration to understand your application.
    *    Provide the Instance URL. A Dynamics 365 instance URL where you want to add Test Drive users and the invitation link will be sent to the same. Follow link to know more about instance URL [link](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/edit-properties-instance).
    *    Provide the Azure Tenant ID. Login to Azure portal and navigate to AAD from Panel -> Select Properties from menu blade -> Get the Directory ID.
    *    Create a new App to get the Azure App details using [linK](https://github.com/Microsoft/AppSource/blob/patch-1/Microsoft%20Hosted%20Test%20Drive/Setup-your-Azure-subscription-for-Dynamics365-Microsoft-Hosted-Test-Drives.md) 
    *    Provice Azure AD App Id, Azure AD App key and Azure AD Tenant Name
    *    Provide the Instance Web API Url - Microsoft Dynamics 365 Web API to access the shared Instance data during provisioning and deporivisiong of Test Drives. You can get the same by - Login to Microsoft Dynamics 365 instance url -> Setting -> Customization -> Developer Resources -> Instance Web API (Copy this URL).
    *    Provide a Role Name. The same role is going to be assigned to Test Drive user and he will have the privileges according to the role. Recommended option is to create a custom Test drive role with appropriate privilages and provide the same here.
    
![](https://github.com/Microsoft/AppSource/blob/patch-1/Images/InstanceWebApiUrl.png)

![](https://github.com/Microsoft/AppSource/blob/patch-1/Images/TestDriveTemplateInCPP.PNG)   
