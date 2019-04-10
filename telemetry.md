# Diagnosing and monitor your application
For diagnosing an issue, it is extremely useful to add telemetry via [ApplicationInsights](https://docs.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview#what-does-application-insights-monitor).
Services and DataAccelerator's DataProcessing component send ApplicationInsights telemetry.  
To access it, you can go to the portal.azure.com and open up the Appinsight instance.  Then, use the Search button to access the query engine.  

## Useful queries:
traces
| where operation_ParentId contains"DataX-Service"
| orderby timestamp desc
​
exceptions
| orderby timestamp desc

For DataX.Flow services You can filter additional telemetry in Startup.cs. This will require a redeployment of the services.

More details on ILogger and ApplicationInsights at the below links:
  - [ILogger](https://docs.microsoft.com/en-us/azure/azure-monitor/app/ilogger)
  - [Filter Rules in code](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/logging/?view=aspnetcore-2.2#filter-rules-in-code)