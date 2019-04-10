# Diagnose and monitor the backend services and Data-Accelerator's Data Processing components using ApplicationInsights
For diagnosing an issue, it is extremely useful to add telemetry via [ApplicationInsights](https://docs.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview#what-does-application-insights-monitor).
Currently, the backend services and DataAccelerator's DataProcessing component send ApplicationInsights telemetry.  
To access the logs, you can go to the portal.azure.com and open up the Applicationinsights instance--> click on Analytics  

## Scenario 1: GetSchema
In the Data Accelerator portal if you are trying to [GetSchema](https://github.com/Microsoft/data-accelerator/wiki/Creating-your-first-pipeline-in-5-minutes!#steps-to-follow) generated, you can look at the ApplicationInsights logs and get details for this call (especially in case you run into an error). For that you need to go to the Azure portal --> ApplicationInsights resource and click on [Analytics](https://docs.microsoft.com/en-us/azure/azure-monitor/app/analytics).
## Useful queries:
  - Look at the Error logs:
    ```
    exceptions
    | order by timestamp desc
    ```
  - Look at the traces logs:
    ```
    traces 
    | order by timestamp desc 
    | where operation_ParentId contains "datax-service" 
    | where operation_Name  contains "POST SchemaInference/GetInputSchema"
    ```

** Want to enhance what's getting logged in the backend services?**
We are using the ILogger implementation and the ILogger instance (_logger) is available in each of the classes in the backend services. 
Example: 
  ```
  _logger.LogInformation($"Event count = {events.Count}");
  ```
**Want to filter telemetry that is being sent?**
For DataX.Flow services You can filter additional telemetry in Startup.cs. This will require a redeployment of the services.
More details on ILogger and ApplicationInsights at the below links:
  - [ILogger](https://docs.microsoft.com/en-us/azure/azure-monitor/app/ilogger)
  - [Filter Rules in code](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/logging/?view=aspnetcore-2.2#filter-rules-in-code)