Following steps will guide you through the steps that need to be followed in order to locally debug the projects

# Services
You will need to import the certificate used by your Service Fabric cluster to your local box. On azure portal, open the SF keyvault and download the primary certificate. Then, import the cert to both - local computer and current user. After the cert has been imported to Local computer, right click on the cert -> select 'All task' -> Manage private keys -> Add 'NETWORK SERVICE'.

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

# Links
* [Tutorials](Tutorials)
* [Wiki Home](Home) 