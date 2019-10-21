# Configure Microsoft Hosted Test Drive for Business Central in Cloud Partner Portal

1. Login to Cloud Partner Portal: https://partner.microsoft.com
2. If you are not able to access the above link, you need to submit a request [here](https://appsource.microsoft.com/en-us/partners/list-an-app) to publish your application. Once we review the request, you will be granted access to start the publish process. 
3. Navigate to existing 'Dynamics 365 Business Central' offer or create a new 'Dynamics 365 Business Central' offer.
4. Enable Test Drive and save the form. </br></br> ![](https://github.com/microsoft/AppSource/blob/master/Images/BC_OfferSetup.JPG)
*    **Type of Test Drive**: Choose 'Microsoft Hosted (Dynamics 365 for Business Central)' option. This indicates that Microsoft will host and maintain the service that performs the Test Drive user provisioning and deprovisioning. 

5. Grant AppSource permission to provision and deprovision Test Drive users in your tenant using the instructions located [here](https://github.com/Microsoft/AppSource/blob/master/Microsoft%20Hosted%20Test%20Drive/Setup-your-Azure-subscription-for-Dynamics365-Financials-Microsoft-Hosted-Test-Drives.md). In this step you will generate the 'Azure AD App Id' and 'Azure AD App Key' values mentioned below.

6. Provide the following fields in the 'Technical Configuration' section. </br> </br>![](https://github.com/microsoft/AppSource/blob/master/Images/BC_TestDriveConfiguration.JPG)   
    
    *    **Max Concurrent Test Drives**: Set this field to the number of concurrent users that can have an active Test Drive at any given point of time. Be aware that each user will consume a Dynamics license while their Test Drive is active, so you will need to ensure you have at least this many Dynamics licenses available for Test Drive users. Recommended value of 3-5.
    *    **Test Drive Duration (hours)**: Set this field to the number of hours the users Test Drive will be active for. After this many hours, the user will be deprovisioned from your tenant. Recommended value of 2-24 hours depending on the complexity of your App. The user can always request another Test Drive if they run out of time and want to access the Test Drive again.
    *    **Instance URL**: Provide an URL that the Test Drive user will initially be navigated to when they start the Test Drive. This is typically the URL of your Dynamics 365 instance that has your App and sample data installed onto. Example Value: https://<span></span>testdrive.crm.dynamics.com
    *    **Azure AD Tenant Id**: Provide the ID of the Azure Tenant for your Dynamics 365 Instance. To retrieve this value, login to Azure portal and navigate to 'Azure Active Directory' -> Select Properties from menu blade -> Copy the Directory ID. Example value: 72f988bf-86f1-41af-91ab-2d7cd0111234
    *    **Azure AD App Id**: ID of the Azure AD App you created in step 7.<br />Example Value: 53852862-a2ae-4e43-9461-faa49650a096
    *    **Azure AD App Key**: Secret for the Azure AD App created in step 7.<br />Example Value: IJUgaIOfq9b9LbUjeQmzNBW4VGn6grr1l/n3aMrnfdk=
    *    **Azure AD Tenant Name**: Provide the name of the Azure Tenant for your Dynamics 365 Instance. Use the format of \<tenantname>.onmicrosoft.com. Example Value: testdrive.onmicrosoft.com
    *    **Role name**: Provide the name of the custom Dynamics 365 Security Role you have created for Test Drive. This is the role that will be assigned to users during their Test Drive. Example Value: testdriverole
    
    
7. Provide the Marketplace listing details. Click on Language value in Marketplace listing to see further required fields -</br></br> ![](https://github.com/microsoft/AppSource/blob/master/Images/CE_MarketListing.JPG)

    *    **Description**: Provide an overview of your Test Drive. This text will be shown to the user while the Test Drive is being provisioned. This field supports HTML if you want to provide formatted content.
    *    **User Manual**: Upload a detailed user manual (file of type .pdf) which helps Test Drive users understand how to use your App. 
    *    **Test Drive Demo Video**: Optionally upload a video that showcases your App. 

