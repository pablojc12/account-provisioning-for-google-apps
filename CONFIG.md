## Google Apps domain configuration guide

Follow these steps to configure your Google Apps domain to work with the Account provisioning for Google Apps API.

### 1. Create a Developers Project

Login to your Google Apps domain with an admin account and go to https://console.developers.google.com/project.

Create a new project, e.g. My project.

![create project][createProject]

Copy the **Project Name** you provided somewhere as you will use it later.

The project dashboard will automatically open once the project is created.

![Dashboard][dash]

### 2. Create an OAuth client ID

On the left side panel go to `Credentials > Create credentials` and click on the option *OAuth client ID*.

![New OAuth client ID][cred]

Under *Application type* select **Other**, then type a name and click on *Create*.

![Select app type][appTypeOther]

The *OAuth account* is now created.

![Client ID generated][clientID]

Copy the **Client ID** and **Client Secret** fields somewhere as you will use them later.

### 3. Create a Service Account

On the left side panel go to `Credentials > Create credentials` and click on the option *Service account key*.

![New Service Account][serviceAccount]

In `Service account` select the option that has the name of the project, in `Key type` select **P12** option, then click on *Create*.

![Create Service Account][createServiceAccount]

A P12 file will download. e.g. `My project-84d807544f50.p12`. You will use this file later.

![Generate new P12 key][serviceAccountData]

On the left side panel go to `Credentials` and click on the link *Manage service accounts*.

![Manage Service Accounts][manageServiceAccounts]

Copy the **Service account ID** of your project in somewhere as you will use it later. This is the **Email address** of your project.

![Copy Client Email][getClientEmail]

### 4. Enable the Admin SDK API

On the left side panel go to `Overview > Google APIs` and search for *admin sdk*. Click on the **Admin SDK** result

![admin sdk api][adminsdkapi]

Click on **Enable**

![enable api][enableapi]

### 5. Enable the OAuth consumer key

Go to https://admin.google.com and navigate to `Security > Advanced settings > Manage OAuth domain key`

> If you don't see the *Advanced settings* click on *Show more*

![oauth key][oauthkey]

Check the **Enable this consumer key** box

![oauth enabled][oauthset]

### 6. Authorize the Admin SDK API for your Service Account Client

Finally, navigate to `Security > Advanced settings > Manage OAuth domain key`

![Manage OAuth domain key][manageclient]

Enter the **Client ID** that was created in [step 2][step2] in the *Client Name* input box. In the *One or More API Scopes* input box enter `https://www.googleapis.com/auth/admin.directory.user`. Click on **Authorize**

![authorize service][authorizeservice]

### 7. Fill out the API configuration fields

Awesome! You now have everything you need to configure the API.

Open the `config.properties` file and fill out the following fields:


##### `apis.GoogleAPIs.domain`
Enter your Google Apps domain. Example:
```properties
apis.GoogleAPIs.domain=yourdomain.com
```

-------------

##### `apis.GoogleAPIs.authUser`
Enter your Google Apps account. This is the account you used to sign in and create the developers project in [step 1][step1]. Example:
```properties
apis.GoogleAPIs.authUser=you@yourdomain.com
```

-------------

##### `apis.GoogleAPIs.keyPath`
Move the P12 file you created in [step 3][step3] to the location where the `appsProvisioning-0.0.1.jar` file is located. Set the `keyPath` value to your P12 file location. Example:
```properties
apis.GoogleAPIs.keyPath=./My project-84d807544f50.p12
```

-------------

##### `apis.GoogleAPIs.serviceAccountEmail`
Enter the Service account **Email address** you created in [step 3][step3]. Example: 
```properties
apis.GoogleAPIs.serviceAccountEmail=1234567890123-abcdefghijklmnopqrstuvwxz01234567@developer.gserviceaccount.com
```

-------------

##### `apis.GoogleAPIs.appName`
Provide the **Project Name** you created in [step 1][step1]. Example:

```properties
apis.GoogleAPIs.appName=My project
```

<br/>

Great! The configuration is now complete. You can now start using the Account provisioning for Google Apps API in your Google Apps domain.

[step1]: #1-create-a-developers-project
[step2]: #2-create-an-oauth-client-id
[step3]: #3-create-a-service-account
[authorizeservice]: https://hallowed-scene-147511.appspot.com/public/authorizeservice.png
[serviceAccountData]: https://hallowed-scene-147511.appspot.com/public/serviceAccountData.png
[manageclient]: https://hallowed-scene-147511.appspot.com/public/manageclient.png
[oauthset]: https://hallowed-scene-147511.appspot.com/public/oauthset.png
[oauthkey]: https://hallowed-scene-147511.appspot.com/public/oauthkey.png
[enableapi]: https://hallowed-scene-147511.appspot.com/public/enableapi.png
[adminsdkapi]: https://hallowed-scene-147511.appspot.com/public/adminsdkapi.png
[serviceAccount]: https://hallowed-scene-147511.appspot.com/public/serviceAccount.png
[clientID]: https://hallowed-scene-147511.appspot.com/public/clientID.png
[dash]: https://hallowed-scene-147511.appspot.com/public/dash.png
[cred]: https://hallowed-scene-147511.appspot.com/public/cred.png
[createProject]: https://hallowed-scene-147511.appspot.com/public/createProject.png
[appTypeOther]: https://hallowed-scene-147511.appspot.com/public/appTypeOther.png
[createServiceAccount]: https://hallowed-scene-147511.appspot.com/public/createServiceAccount.png
[manageServiceAccounts]: https://hallowed-scene-147511.appspot.com/public/manageServiceAccounts.png
[getClientEmail]: https://hallowed-scene-147511.appspot.com/public/getClientEmail.png
