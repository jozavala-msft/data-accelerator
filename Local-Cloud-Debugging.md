Following steps will guide you through the steps that need to be followed in order to locally debug the projects

# DataX.Flow
* Open DataX.Flow.sln in VisualStudio (Run Visual Studio as admin)
* In DataX.Flow project, open Local.1Node.xml file under ApplicationParameters folder
* Set values for the following parameters:
  * AppInsightsIntrumentationKey - Eg.: configgen-aiInstrumentationKey
  * cosmosDBConfigCollectionName - Eg.: configgenConfigs
  * cosmosDBConfigConnectionString - Eg.: keyvault://<your services keyvault name>/configgen-configgenconfigs
  * cosmosDBConfigDatabaseName - Eg.: keyvault://<your services keyvault name>/configgen-configgenconfigsdatabasename
  * ServiceKeyvaultName - Eg.: kvServicesdx123
  * AzureServicesAuthConnectionString - Look for a secret called 'configgen-azureservicesauthconnectionstring'. Only copy the 'Value' part here. (eg.: RunAs=App;AppId=<some GUID>;TenantId=<some GUID>;CertificateThumbprint=<Cert Thumbprint>;CertificateStoreLocation=LocalMachine)

# Links
* [Tutorials](Tutorials)
* [Wiki Home](Home) 