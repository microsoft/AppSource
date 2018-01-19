Azure Functions offers built-in integration with Azure Application Insights for monitoring functions. We recommend deploying Application Insights with your Test Drive deployment to make troubleshooting of any potential issues easier.

**Deploy Application Insights**
1. Log into the Azure Portal (https://portal.azure.com) with an account that has permission to deploy to the Azure Subscription the Test Drive Resources are deployed to.

2. Deploy an Application Insights resource to your Test Drive resource group

![](https://github.com/Microsoft/AppSource/blob/master/Images/AppInsights/createAppInsights.png)

  * Click '+ New' to create a new Azure Resource
  * Search for and select 'Application Insights'
  * Create a new Application Insights resource with the following values
    * Name: pick any valid value
    * Application Type: Select 'General'
    * Subscription: Select the Azure subscription your test drive resources are deployed into
    * Resource Group: Select 'Use existing' and select the same resource group your other test drive resources are deployed into
    * Location: Select the same Azure region your other test drive resources are deployed into
  * Click 'Create' to deploy the resource
  * Wait for the resource deployment to complete before proceeding. This usually takes 1-2 minutes, and you will receive a notification from Azure Portal when it is complete.

**Connect Application Insights to your Test Drive Function App**

3. Copy the Instrumentation Key for your Application Insights 

![](https://github.com/Microsoft/AppSource/blob/master/Images/AppInsights/getAppInsightsKey.png)

  * Navigate to your Application Insights resource
  * Select the 'Overview' tab
  * Expand the 'Essentials' section of the page
  * Copy the 'Instrumentation Key' field

4. Connect your Azure Function App to your Application Insights

![](https://github.com/Microsoft/AppSource/blob/master/Images/AppInsights/setAppInsightsKey.png)

* Navigate to your 'App Service' test drive resource
* Click on 'Application Settings'
* Click on 'Add new setting' button and fill it with the below key/value
  * Name: APPINSIGHTS_INSTRUMENTATIONKEY
  * Value: <paste the Instrumentation Key you retrieved in step 2>
* Click save to create the application setting

Your Test Drive App Service is now connected to your Application Insights resource. Telemetry data will now flow from the Test Drive App Service into the Application Insights service to provide easier troubleshooting and monitoring of your Test Drive deployment. 

The cost to deploy Application Insights is very low:
https://azure.microsoft.com/en-us/pricing/details/application-insights/ 

Additional Information:
https://blogs.msdn.microsoft.com/appserviceteam/2017/04/06/azure-functions-application-insights/
