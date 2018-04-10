# Configure Microsoft Hosted Test Drive in Cloud Partner Portal

1. Login to Cloud Partner Portal - https://cloudpartner.azure.com
2. If you are not able to access the above link, you need to submit a request [here](https://appsource.microsoft.com/en-us/partners/list-an-app) to publish your application. Once we review the request, you will be granted access to start the publish process. 
3. Navigate to existing offer or create a new offer.
4. Select the Test Drive option from the side bar.
5. Select 'Yes' for 'Enable a Test Drive' option.

6. Provide the following fields in the 'Details' section ![](https://github.com/Microsoft/AppSource/blob/patch-1/Images/EnableTestDrive.PNG)

    *    Description: Provide an overview of your Test Drive. This field supports HTML if you want to provide formatted content to your Test Drive experience. 
    *    User Manual: Upload a detailed user manual (file of type .pdf) which helps customers understand how to use your application. 
    *    Test Drive Demo Video: Optionally upload a video that showcases your App. 

7. Create a Azure AD App to grant AppSource permission to provision and deprovision Test Drive users into your tenant using the instructions located [here](https://github.com/Microsoft/AppSource/blob/patch-1/Microsoft%20Hosted%20Test%20Drive/Setup-your-Azure-subscription-for-Dynamics365-Microsoft-Hosted-Test-Drives.md) 

8. Provide the following fields in the 'Technical Configuration' section ![](https://github.com/Microsoft/AppSource/blob/patch-1/Images/TestDriveTemplateInCPP.PNG)   

    *    Type of Test Drive: Choose 'Microsoft Hosted' option
    *    Max Concurrent Test Drives: Set this field to the number of concurrent users that can have an active Test Drive at any given point of time. Be aware that each user will consume a license while their Test Drive is active, so you will need to ensure you have at least this many licenses available for Test Drive users. Recommended value of 3-5
    *    Test Drive Duration (hours): Set this field to the number of hours the users Test Drive will be active for. After this many hours, the user will be deprovisioned from your tenant. Recommended value of 2-24 hours depending on the complexity of your App. The user can always request another Test Drive if they run out of time and want to access the Test Drive again.
    *    Instance URL: Provide an URL that the Test Drive user will be navigated to when they are Test Driving your App. This is typically the URL of your Dynamics 365 instance that has your App and sample data installed onto. Example Value: https://testdrive.crm.dynamics.com
    *    Azure AD Tenant Id: Provide the ID of the Azure Tenant for your Dynamics 365 Instance. To retrieve this value, login to Azure portal and navigate to AAD from Panel -> Select Properties from menu blade -> Copy the Directory ID
    *    Azure AD App Id: ID of the App created in step 9. To retrieve this value, login to Azure portal and navigate to AAD from Panel -> Select Properties from menu blade -> Copy the Directory ID
    *    Azure AD App Key: ID of the App created in step 9. To retrieve this value, login to Azure portal and navigate to AAD from Panel -> Select Properties from menu blade -> Copy the Directory ID
    *    Azure AD Tenant Name: Provide the name of the Azure Tenant for your Dynamics 365 Instance. Use the format of <tenant>.onmicrosoft.com. Example Value: testdrive.onmicrosoft.com
    *    Instance Web API URL: Provide the Web API URL for your Dynamics 365 Instance. You can retrieve this value by logging into your Microsoft Dynamics 365 instance and navigating to Setting -> Customization -> Developer Resources -> Instance Web API (Copy this URL). Example value: https://crmtestdrivem.crm.dynamics.com/api/data/v9.0 
![](https://github.com/Microsoft/AppSource/blob/patch-1/Images/InstanceWebApiUrl.png)
    *    Role name: Provide the name of the custom Dynamics 365 Security Role you have created for Test Drive. This is the role that will be assigned to users during their Test Drive. Example Value: testdriverole
    

