# Setup your Azure subscription for Test Drives

1.	Login to you Azure management portal
2.	Create a new tenant in AAD (if not available already)
      *    Navigate to https://portal.azure.com
      *    Click on + New ->  (Search for Azure Active Directory)

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub1.jpg)

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub2.jpg)

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub3.jpg)

3. 	Register an application in azure to help for single sign on login

      *    Navigate to the newly created directory
      *    And select Azure Active directory in the filter pane.
      *    Search “App registrations” and click on “Add”
      *    Provide an application name.
      *    Select the Type of as “Web application”
      *    Click create.
      *    After the application has been created, go to  Properties -> Set the application as multi-tenant and hit Save
      *    Under keys, add a Key Description, set the duration to two years.
      *    Click Save. This should generate the ClientSecret. 
      *    Click on Required Permissions
             * Click on Windows Azure Active Directory.
             * Select application permissions for: Read and write directory data, Read directory data.
             * Hit Save.
      *    Navigate back to the Azure AD blade.
      *    Click on Users and create a new admin admin@yournewtenant.onmicrosoft.com 
      *    Make the user a global admin and save.
      *    Login as the above user and change the admin password
      
![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub4.jpg)

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub5.jpg)

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub6.jpg)

4.	Share subscription information 
      *    Create a new subscription or login to an existing Azure subscription you want to use for trials. Its recommended to use a new subscription for resource isolation.
      *    Filter on Subscriptions, find the right subscription and click Manage.
      *    Click on Edit directory and change it so that it points to the new AD.
      *    Navigate to Subscriptions, select subscription, edit directory.
      *    Choose the directory created in 1.

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub7.jpg)

5.	Share client ID and client cert 
6.	Make the new app a “Company Administrator”
      *    Install AzureAD powershell extension.
      *    Connect-MsolService (and login as the administrator of the new tenant)
      *    Get-MsolServicePrincipal and look for the app name.
      *    Copy the ObjectId.
      *    Add-MsolRoleMember -RoleName 'Company Administrator' -RoleMemberType ServicePrincipal -RoleMemberObjectId '<ObjectId>'

Given, we’re using the application to deploy to the subscription, we need to add the application as a contributor on the subscription. The instructions for these are as below:
1.	Navigate https://portal.azure.com
2.	Navigate to the subscriptions blade and select the appropriate subscription.
3.	Click on Access Control (IAM)
4.	Hit + Add in the new blade.

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub8.jpg)

5.	Set the role as Contributor.
6.	Select the AAD application to assign the role. 

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/SetupSub9.jpg)

7.	Click on Save.

