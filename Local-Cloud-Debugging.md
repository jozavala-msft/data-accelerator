Following steps will guide you through the steps that need to be followed in order to locally debug the projects

# Services
You will need to import the certificate used by your Service Fabric cluster to your local box. On azure portal, open the SF keyvault and download the primary/reverseProxy/SSL certificate. Then, import the cert to both - local computer and current user. After the cert has been imported to Local computer, right click on the cert -> select 'All task' -> Manage private keys -> Add 'NETWORK SERVICE'.

To view the parameters set for each service in your DataX environment, open your service fabric resource in azure portal and click on the service fabric explorer link. Expand a service, in this instance lets expand DataX.FlowType and select fabric:/DataX.Flow. On details TAB you should now see the parameters set for DataX.Flow service.

## DataX.Flow
* Open DataX.Flow.sln in VisualStudio (Run Visual Studio as admin)
* In DataX.Flow project, open Local.1Node.xml file under ApplicationParameters folder
* Set values for the following parameters:
  * AppInsightsIntrumentationKey - Eg.: configgen-aiInstrumentationKey
  * cosmosDBConfigCollectionName - Eg.: configgenConfigs
  * cosmosDBConfigConnectionString - Eg.: keyvault://<your services keyvault name>/configgen-configgenconfigs
  * cosmosDBConfigDatabaseName - Eg.: keyvault://<your services keyvault name>/configgen-configgenconfigsdatabasename
  * ServiceKeyvaultName - Eg.: kvServicesdx123
  * AzureServicesAuthConnectionString - Look for a secret called 'configgen-azureservicesauthconnectionstring'. Only copy the 'Value' part here. (eg.: RunAs=App;AppId=<some GUID>;TenantId=<some GUID>;CertificateThumbprint=<Cert Thumbprint>;CertificateStoreLocation=LocalMachine)
* In Flow.ManagementService project, open FlowManagementController.cs file
* Within GetAllFlowsMin method add a breakpoint and comment out the following line
```C#
RolesCheck.EnsureReader(Request, _isLocal);
```
* Set the platform for the solution to x64 and F5
* On browser open - http://localhost:8461/api/flow/getall/min

## DataX.Gateway
* Open DataX.Gateway.sln in VisualStudio (Run Visual Studio as admin)
* In DataX.Gateway project, open Local.1Node.xml file under ApplicationParameters folder
* Set values for the following parameters:
  * AllowedUserRoles - DataXReader,DataXWriter
  * AppInsightsIntrumentationKey - configgen-aiInstrumentationKey
  * Audience
  * ClientId
  * ReverseProxySslThumbprint
  * ServiceKeyvaultName
  * SSL_Cert_Thumbprint
  * Tenant

# Links
* [Tutorials](Tutorials)
* [Wiki Home](Home) 