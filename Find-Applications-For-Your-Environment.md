For DataX processing, we need two AAD apps clientapp-* and serviceapp-*.

To see the details on your apps, please follow the steps below.

# Find Application Id
1. Open Azure Portal https://ms.portal.azure.com
2. Click All services and select Resource groups
3. Select your DataX resource group. You will see 5 Key vault resources.
4. Select the one starts with kvServices
5. Once the Key vault page is opened, select Secrets. You will see two secrets which have clientId: **configgen-clientId** and **web-clientId**
6. To get the appId for the service app, select **configgen-clientId**.
7. Click Show Secret Value button
8. Do the step 6 and 7 for **web-clientId** if you want to see the one for the website.


# Find Application Name
1. Make sure you already have the appIds using the steps above.
2. Open Azure Portal https://ms.portal.azure.com
3. Click All services and select Azure Active Directory
4. Click App registrations
5. Change to All apps from my apps
6. In "Search by name or AppId" textbox, search for your app by typing your appId.
7. Click the app