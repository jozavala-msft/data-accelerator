Following steps will guide you through the steps that need to be followed in order to locally debug the projects

# DataX Services
You will need to import the certificate used by your Service Fabric cluster to your local box. On azure portal, open the SF keyvault and download the primary/reverseProxy/SSL certificate. Then, import the cert to both - local computer and current user. After the cert has been imported to Local computer, right click on the cert -> select 'All task' -> Manage private keys -> Add 'NETWORK SERVICE'.

To view the parameters set for each service in your DataX environment, open your service fabric resource in azure portal and click on the service fabric explorer link. Expand a service, in this instance lets expand DataX.FlowType and select fabric:/DataX.Flow. On details TAB you should now see the parameters set for DataX.Flow service. Similarly you can view the parameters for the rest of the services.

### DataX.Flow
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

### DataX.Gateway
* Open DataX.Gateway.sln in VisualStudio (Run Visual Studio as admin)
* In DataX.Gateway project, open Local.1Node.xml file under ApplicationParameters folder
* Set values of the parameters same as that is being used for DataX.Gateway in service fabric explorer
* For 'AzureServicesAuthConnectionString' - Look for a secret called 'configgen-azureservicesauthconnectionstring' in your serviceKeyVault. Only copy the 'Value' part here. (eg.: RunAs=App;AppId=<some GUID>;TenantId=<some GUID>;CertificateThumbprint=<Cert Thumbprint>;CertificateStoreLocation=LocalMachine)
* F5
* If prompted, grant Visual Studio permission

### DataX.Metrics
* Open DataX.Metrics.sln in VisualStudio (Run Visual Studio as admin)
* In DataX.Metrics project, open Local.1Node.xml file under ApplicationParameters folder
* Set values of the parameters same as that is being used for DataX.Metrics in service fabric explorer
* For 'AzureServicesAuthConnectionString' - Look for a secret called 'configgen-azureservicesauthconnectionstring' in your serviceKeyVault. Only copy the 'Value' part here. (eg.: RunAs=App;AppId=<some GUID>;TenantId=<some GUID>;CertificateThumbprint=<Cert Thumbprint>;CertificateStoreLocation=LocalMachine)
* Set the platform for the solution to x64 and F5
* If prompted, grant Visual Studio permission

### DataX.SimulatedData
* Open DataX.SimulatedData.sln in VisualStudio (Run Visual Studio as admin)
* In DataX.SimulatedData project, open Local.1Node.xml file under ApplicationParameters folder
* Set values of the parameters same as that is being used for DataX.SimulatedData in service fabric explorer
* For 'AzureServicesAuthConnectionString' - Look for a secret called 'configgen-azureservicesauthconnectionstring' in your serviceKeyVault. Only copy the 'Value' part here. (eg.: RunAs=App;AppId=<some GUID>;TenantId=<some GUID>;CertificateThumbprint=<Cert Thumbprint>;CertificateStoreLocation=LocalMachine)
* **Note:** If you are already using the existing IoTHub to simulate data then you might want to consider to spin up another IoTHub to avoid any data duplication
* Set the platform for the solution to x64 and F5
* If prompted, grant Visual Studio permission

# Website: DataX Website

### Environment Setup
1. Install NodeJs from http://nodejs.org, version 10.6.0 or later

2. Install VS Code extension to get consistent code formatting on Save from https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode

3. Set the following environment variable. The ```key vault name``` should point to the Azure key vault service which back your DataX instance.
```
set DATAX_KEYVAULT_NAME=<key vault name>
```

4. Set the following environment variable. The ```secret name prefix``` should point to the secret name prefix in the Azure key vault service which back your DataX instance.
```
set DATAX_KEYVAULT_SECRET_PREFIX=<secret name prefix>
```

### Build and run a local Website instance

1. Install all dependency packages of this website.
```
npm install
```

2. Build non-optimized version website using ```npm run dev```. While the website tend to be larger in size and slow down your web experience, you benefit
this by getting a better development experience when debugging the sources on the browser of your choice. 
```
npm run dev
```

3. Start website
```
npm start
```

4. You should see the following message. Follow what it said and login to allow the local web app use your credential to access key vault. NOTE: the AAD account you login should have access to the azure keyvault service.
```
To sign in, use a web browser to open the page https://microsoft.com/devicelogin and enter the code <a temporary code> to authenticate.
```

5. View website on http://localhost:2020

### Building website
When you have changes to the website or one of its dependency packages changes. You will have to rebuild the website. You have 2 options

#### Manually rebuilding 
Run this command everytime you want to rebuild website.
```
npm run dev
```

#### Automatically rebuilding
Run this command which will automatically rebuild website if it detects that any of its files changes or files under node_modules (dependency packages) changes
```
npm run devwatch
```

# Website: DataX NPM Packages

### Quick start to developing this package

1. Run ```npm install``` to install all dependency package of this NPM package.

2. Run ```npm run dev``` to build non-optimized bundles. While the packages tend to be larger in size and slow down your web experience, you benefit
this by getting a better development experience when debugging the sources on the browser of your choice.

3. When you are done developing your package, increment the version number of your NPM package in the ```package.json``` file.

4. Run ```npm run build``` to build optimized bundles (obfuscated, minified and other compiler optimizations) leading to smaller output sizes and 
faster performance for production consumption.

5. Run ```npm publish```

### Tips and Tricks
1. For your website, run ```npm run devwatch``` which will put your website into listening mode for file changes. Every time a file that the website
depends on under its folder and ```node_modules``` dependency folder changes, it will automatically re-compile.

2. Run ```npm run devpatch``` to build development bundles and this command will automatically execute a batch script to xcopy the built bundles
to our website's ```node_modules``` folder. This will cause your website to recompile itself to pick up the changes. 
This ```localdevpatch.bat``` script assumes that the website GIT repo and this packages GIT repo share the same parent folder.
If this is not the case, please change the paths of the script locally on your computer.

# Links
* [Tutorials](Tutorials)
* [Wiki Home](Home) 