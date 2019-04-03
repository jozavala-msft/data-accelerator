Services and Web send AppInsight telemetry.  To access it, you can go to the portal.azure.com and open up the Appinsight instance.  Then, use the Search button to access the query engine.  

Useful queries:
traces
| where operation_ParentId contains"DataX-Service"
| orderby timestamp desc
​
exceptions
| orderby timestamp desc

You can turn on and off additional telemetry in <>.cs.  This will require a redeployment of the services
