# How do I get started? #

### Steps to follow for Azure based application 


1. Develop and test your application 
2. Enable Azure Active Directory single-sign-on. Steps to enable AAD SSO: 
    *  https://docs.microsoft.com/ azure/active-directory/develop/active-directory-devhowto-appsource-certified
    *  [Documentation to Integrate your application with Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-integrating-applications#adding-an-application)
3.	Define the demo scenario and create the demo data
    * This is a critical step to your success in the marketplace, you want to land the test drive user in to a test drive instance that is pre-setup with all the ‘Wow’ or ‘elevator pitch’ scenarios. Therefore, you need to prep the demo scenarios and data sets for the scenario, you want the user to try. 
    * It’s strongly recommended that you enable walkthroughs for your application so that the business users have a guided tour when they land in your application. 
4.	Once you complete these steps you need to [create an ARM template](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-authoring-templates) for your application. 
5.	You can find a sample ARM template for an app that is powered by a website and an ARM template [here](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/main-template.json). Additional ARM template parameters: 
    * Use MSDeploy to package your code assets and provide the link in the packageURI. ARM will deploy your code packages during provisioning of your app. 

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/HowDoesItWork5.5.png)


    * Outputs in the ARM templates: 
        1. As you can see below the App Uri tells AppSource where to redirect the user when the user clicks on Test Drive 
        2. If you have custom provisioning steps outside of ARM to complete the deployment, then these needs to be defined as Outputs in the ARM template as shown below. These can either be a callback URI that you host or an Azure function. You can find details on how to develop and test an Azure function [here](https://github.com/Azure/AzureTestDrive/wiki/Custom-configurations-using-Azure-functions). 
        3. Marketplace: this needs to be retained as “AppSource”
        4. PublisherContactLink needs to be link to you listing in AppSource

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/HowDoesItWork6.png)

6.	Identify a subscription you want to use for providing test drives. 
7.	Follow the steps in this [article](https://github.com/Azure/AzureTestDrive/wiki/Setup-your-Azure-subscription-for-Test-Drives) to set up the app in your subscription 
8.	Start the publish process and complete all the mandatory step and push your app to staging. 
    * Become a Publisher: Please see [Understanding the Publishing Portal](https://github.com/Azure/AzureTestDrive/wiki/Understanding-the-Publishing-Portal) if you are not already a Microsoft Publisher.
    * 	Create a New Offer: Once you are a Publisher, starting a new Test Drive offer is explained [here](https://github.com/Azure/AzureTestDrive/wiki/Create-a-New-Offer).
    * 	Connect your Azure Account: It is required to have an Azure Service Principal and Azure Subscription to publish your Test Drive. Learn how to configure these [here](https://github.com/Azure/AzureTestDrive/wiki/Connect-your-Azure-Account).
    * 	Add Marketing to your Offer: Your Test Drive needs a support contact and a user manual, videos and offer detail descriptions. Set all of that up [here](https://github.com/Azure/AzureTestDrive/wiki/Add-Marketing-to-your-Offer).
    * 	Lead management: Mark the lead management to None
    * 	Configuration

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/config4.png)

*	<b>Trial Enabled</b> – Sets your test drive to either Enabled (Yes) or Disabled (No). For test drives in Production, switching to Disabled will hide the test drive from being able to be deployed. If there are any test drives actively used by users, those test drives will continue to run until the session expires.

*	<b>Number of Hours Per Trial</b> –  Duration for how long the test drive deployment will stay active, in # of hours. (Test drive terminates automatically after this time period ends).

*	<b>Number of Hot Instances</b> – Number of test drive instances that are already deployed and awaiting access. Customers can instantly access rather than waiting for a deployment.
 
*	<b>Maximum Number of Instances Per User _**[Deprecated]**_</b> – The number limit on how many test drives each unique user/customer can deploy.

*	<b>Maximum Number Concurrent Instances</b> – The number limit on how many test drive deployments can be active at the same time across all users. (Any integer between 0 and 100. Must be greater or equal than the "NUMBER OF HOT INSTANCES" + "NUMBER OF WARM SESSIONS")

*	<b>Average Deployment Time in Seconds _**[Deprecated]**_</b> – The amount of time in seconds it takes for the test drive to fully deploy in Azure. 

*	<b>Escalation Email</b> – The email address where test drive error notifications will be sent. You can also use comma separated email addresses/distribution list(s) in this field.


*	<b>Approval Email _**[Deprecated]**_</b> – The email address(es) that approval requests will be sent to – for customers who have exceeded the test drive launch limit.


*	<b>Number of Warm Sessions</b> – Number limit for how many stopped test drive cloud sessions to keep.

*	<b>Deployment Regions</b> – Select the Region(s) in which you want/need to deploy the test drive ARM template in.
  (Note: If your test drive uses <b>custom images</b>, make sure you select the same region in which the custom images are stored – otherwise it will fail.)
*	<b>Deployment Artifacts</b> – Upload your test drive ARM template here, in a .zip file. This is the file you offered in the previous section.
![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/config6.png)

  You must upload a zip file containing the Azure Resource Manager (ARM) template to deploy the solution. Please name the main template file: “main-template.json”. 

  (Note: Make sure your ARM template contains Output Parameters for key variables that are needed!)
9.	Now you are ready to publish your offer! Please proceed to the section called [Test, Publish, Push to Production](https://github.com/Azure/AzureTestDrive/wiki/Test,-Publish,-Push-to-Production).

### Business applications 
If you are interested to enable test drives that use business applications complete this survey and we will be in touch: https://aka.ms/listmyapp
