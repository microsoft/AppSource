# Setup your Azure subscription for Dynamics 365 Test Drives

1.	Login to your Azure management portal
2.	Create a new tenant in AAD (if not available already)
      *    Navigate to https://portal.azure.com
      *    Click on + New ->  (Search for Azure Active Directory)

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub1.jpg)

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub2.jpg)

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub3.jpg)

3. 	Register an application in azure. We will use this application to perform operations on your Dynamics 365 instance including adding and removing users etc. 

      *    Navigate to the newly created directory or already existing directory and select Azure Active directory in the filter pane.
      *    Search “App registrations” and click on “Add”
      *    Provide an application name.
      *    Select the Type of as “Web application”
      *    Click create.
      *    After the application has been created, go to  Properties -> Set the application as multi-tenant and hit Save.
      *    Under keys, add a Key Description, set the duration to two years or as appropriate. Do remember to update this before the key expires, else your test drives will be broken. 
      *    Click Save. This should generate the ClientSecret. 
      *    Navigate back to the Azure AD blade.
      *    Click on Users and create a new admin admin@yournewtenant.onmicrosoft.com 
      *    Make the user a global admin and save.
      *    Login as the above user and change the admin password
      *    Click on Required Permissions
      *    Click on Windows Azure Active Directory.
      *    Select application permissions for: Read and write directory data, Read directory data.
      *    Click on Grant Permissions.
      *    Hit Save.

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub4.jpg)

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub5.jpg)

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub6.jpg)

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/TestDrive_GrantPermission.png)

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/TestDriveGrantPermissions.PNG)

5. Given, we’re using the application to deploy to the subscription, we need to add the application as a contributor on the subscription. The instructions for these are as below:
      *    Navigate https://portal.azure.com
      *    Navigate to the subscriptions blade and select the appropriate subscription.
      *    Click on Access Control (IAM)
      *    Hit + Add in the new blade.
      *    Set the role as Contributor.
      *    Select the AAD application to assign the role. 
      *    Click on Save.
      
![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub8.jpg)

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub9.jpg)

