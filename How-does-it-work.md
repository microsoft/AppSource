# How does it work? #


As a partner, you can bring your application assets and integrate with the AppSource Test Drive framework to enable Test Drive for your applications. The approach you take for enabling test drives will be dictated by the profile of your application. 
Since apps on AppSource is targeted for business users, you need to enable Azure Active Directory single-sign-on (AAD SSO) for your application. 

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/HowDoesItWork1.png)

Once you enabled AAD SSO for your application, the next step you take will be determined by the profile of your application. 
If your application does not deploy any extensions to business application and if you deploy assets to customers Azure subscription, then you can integrate your ARM template with our test drive framework to enable the trial experience. See below the steps to enable test drive for an app build on Azure:

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/HowDoesItWork2.png)
![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/HowDoesItWork3.png)

If your application deploys extensions to Microsoft business application like Dynamics 365, then you build your application, author your provision, assign, de-provision Logic Apps and integrate that with AppSource test drive framework. See detailed steps below: 

![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/HowDoesItWork4.png)
![](https://github.com/Azure/AzureTestDrive/blob/master/AzureTestDriveImages/HowDoesItWork5.png)

Refer to this section to learn more about what happens in the background with your test drives. 

***

See also:

* [What does the test drive framework give me?](https://github.com/Microsoft/AppSource/blob/master/What-does-the-test-drive-framework-give-me.md)
* [How do I get started?](https://github.com/Microsoft/AppSource/blob/master/GettingStarted.md)
