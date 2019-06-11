Following are the steps to upgrade Data Accelerator components from v1.0 to v1.1 

### Update DataProcessing engine (CP): 
* Download the new jars
  * Unpack [Microsoft.DataX.Spark v1.1.0](https://www.nuget.org/packages/Microsoft.DataX.Spark/1.1.0) and copy .jar from lib folder
  * Upload the .jar into the default storage account (location default/datax/bin)
* Update cosmosDb
  * In commons collection, update the document with name ‘DataXDirect’ with following new jars

```
"name" : "${sparkJobName}",
"file" : "wasbs:///datax/bin/datax-host_2.3_2.11-1.1.0.jar",
"className" : "datax.app.DirectStreamingApp",
"args" : [
  "conf=${sparkJobConfigFilePath}",
  "driverLogLevel=${sparkJobDriverLogLevel}"
],
"jars" : [
  "wasbs:///datax/bin/datax-core_2.3_2.11-1.1.0.jar",
  "wasbs:///datax/bin/datax-utility_2.3_2.11-1.1.0.jar",
  "wasbs:///datax/bin/applicationinsights-core-2.2.1.jar",
  "wasbs:///datax/bin/azure-documentdb-1.16.1.jar",
  "wasbs:///datax/bin/azure-eventhubs-1.2.1.jar",
  "wasbs:///datax/bin/azure-eventhubs-spark_2.11-2.3.6.jar",
  "wasbs:///datax/bin/azure-keyvault-webkey-1.1.jar",
  "wasbs:///datax/bin/datax-keyvault_2.3_2.11-1.1.0-with-dependencies.jar",
  "wasbs:///datax/bin/java-uuid-generator-3.1.5.jar",
  "wasbs:///datax/bin/proton-j-0.31.0.jar",
  "wasbs:///datax/bin/scala-java8-compat_2.11-0.9.0.jar"
],
```
  * In the configgenConfigs collection, update the binaryName array in the document
```
"binaryName" : [
   "datax/bin/datax-utility_2.3_2.11-1.1.0.jar",
   "datax/bin/datax-host_2.3_2.11-1.1.0.jar",
   "datax/bin/datax-core_2.3_2.11-1.1.0.jar"
],
```
* Re-deploy flows
### Update Web
* Download and unpack [Microsoft.DataX.Web v1.1.0](https://www.nuget.org/packages/Microsoft.DataX.Web/1.1.0) nuget package
* Deploy Web ([Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest) is required)
  * After unpacking the [Microsoft.DataX.Web v1.1.0](https://www.nuget.org/packages/Microsoft.DataX.Web/1.1.0) nuget package, from …\lib\bin folder run the following Azure CLI command
```
az login
az account set --subscription "<Your DataX Azure Subscription Name>"
az webapp deployment source config-zip --resource-group <Your DataX ResourceGroupName> --name "<Your DataX  AppService Name>" --src deployment.zip
```
* Restart the AppService using following Azure CLI command or you could directly restart the AppService from Azure portal
```
az webapp restart --resource-group <Your DataX ResourceGroupName> --name "<Your DataX  AppService Name>"
```
### Update Services
Clone [data-accelerator](https://github.com/microsoft/data-accelerator) git hub repo (stable branch)

You will need to import the certificate used by your Service Fabric cluster to your local box. On azure portal, open the SF keyvault and download the primary/reverseProxy/SSL certificate. Then, import the cert to both - local computer and current user. After the cert has been imported to Local computer, right click on the cert -> select 'All task' -> Manage private keys -> Add 'NETWORK SERVICE'.

To view the parameters set for each service in your Data Accelerator environment, open your service fabric resource in azure portal and click on the service fabric explorer link. Expand a service, in this instance lets expand DataX.FlowType and select fabric:/DataX.Flow. On details TAB you should now see the parameters set for DataX.Flow service. Similarly you can view the parameters for the rest of the services.

For each service (DataX.Flow, DataX.Gateway, DataX.Metrics, DataX.SimulatedData):
* Run Visual Studio as Admin. Open the .sln for the service that you intend to update
* Update cloud.xml under ApplicationParameters/Cloud.xml with the parameter value as fetched from service fabric explorer 
* Update cloud.xml under PublishProfiles/Cloud.xml with following ClusterConnectionParameters
```
<ClusterConnectionParameters ConnectionEndpoint="<your SF cluster client connection endpoint eg.: mycluster.westus.cloudapp.azure.com:19000>"
  X509Credential="true"
  ServerCertThumbprint="<Your primary cert thumbprint>"
  FindType="FindByThumbprint"
  FindValue="<Your primary cert thumbprint>"
  StoreLocation="CurrentUser"
  StoreName="My" />
```
* Right Click the SF project and deploy
