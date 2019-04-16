Following steps will guide you through the steps that need to be followed in order to locally debug the projects

# Services
You will need to import the certificate used by your Service Fabric cluster to your local box. On azure portal, open the SF keyvault and download the primary/reverseProxy/SSL certificate. Then, import the cert to both - local computer and current user. After the cert has been imported to Local computer, right click on the cert -> select 'All task' -> Manage private keys -> Add 'NETWORK SERVICE'.

To view the parameters set for each service in your DataX environment, open your service fabric resource in azure portal and click on the service fabric explorer link. Expand a service, in this instance lets expand DataX.FlowType and select fabric:/DataX.Flow. On details TAB you should now see the parameters set for DataX.Flow service. Similarly you can view the parameters for the rest of the services.

## DataX.Flow
* Open DataX.Flow.sln in VisualStudio (Run Visual Studio as admin)
* In DataX.Flow project, open Local.1Node.xml file under ApplicationParameters folder
* Set values of the parameters same as that is being used for DataX.Flow in service fabric explorer
* For 'AzureServicesAuthConnectionString' - Look for a secret called 'configgen-azureservicesauthconnectionstring' in your serviceKeyVault. Only copy the 'Value' part here. (eg.: RunAs=App;AppId=<some GUID>;TenantId=<some GUID>;CertificateThumbprint=<Cert Thumbprint>;CertificateStoreLocation=LocalMachine)
* In Flow.ManagementService project, open FlowManagementController.cs file
* Within GetAllFlowsMin method add a breakpoint and comment out the following line
```C#
RolesCheck.EnsureReader(Request, _isLocal);
```
* Set the platform for the solution to x64 and F5
* If prompted, grant Visual Studio permission
* On browser open - http://localhost:8461/api/flow/getall/min

## DataX.Gateway
* Open DataX.Gateway.sln in VisualStudio (Run Visual Studio as admin)
* In DataX.Gateway project, open Local.1Node.xml file under ApplicationParameters folder
* Set values of the parameters same as that is being used for DataX.Gateway in service fabric explorer
* For 'AzureServicesAuthConnectionString' - Look for a secret called 'configgen-azureservicesauthconnectionstring' in your serviceKeyVault. Only copy the 'Value' part here. (eg.: RunAs=App;AppId=<some GUID>;TenantId=<some GUID>;CertificateThumbprint=<Cert Thumbprint>;CertificateStoreLocation=LocalMachine)
* F5
* If prompted, grant Visual Studio permission

## DataX.Metrics
* Open DataX.Metrics.sln in VisualStudio (Run Visual Studio as admin)
* In DataX.Metrics project, open Local.1Node.xml file under ApplicationParameters folder
* Set values of the parameters same as that is being used for DataX.Metrics in service fabric explorer
* For 'AzureServicesAuthConnectionString' - Look for a secret called 'configgen-azureservicesauthconnectionstring' in your serviceKeyVault. Only copy the 'Value' part here. (eg.: RunAs=App;AppId=<some GUID>;TenantId=<some GUID>;CertificateThumbprint=<Cert Thumbprint>;CertificateStoreLocation=LocalMachine)
* Set the platform for the solution to x64 and F5
* If prompted, grant Visual Studio permission

## DataX.SimulatedData
* Open DataX.SimulatedData.sln in VisualStudio (Run Visual Studio as admin)
* In DataX.SimulatedData project, open Local.1Node.xml file under ApplicationParameters folder
* Set values of the parameters same as that is being used for DataX.SimulatedData in service fabric explorer
* For 'AzureServicesAuthConnectionString' - Look for a secret called 'configgen-azureservicesauthconnectionstring' in your serviceKeyVault. Only copy the 'Value' part here. (eg.: RunAs=App;AppId=<some GUID>;TenantId=<some GUID>;CertificateThumbprint=<Cert Thumbprint>;CertificateStoreLocation=LocalMachine)
* **Note:** If you are already using the existing IoTHub to simulate data then you might want to consider to spin up another IoTHub to avoid any data duplication
* Set the platform for the solution to x64 and F5
* If prompted, grant Visual Studio permission

# Links
* [Tutorials](Tutorials)
* [Wiki Home](Home) 