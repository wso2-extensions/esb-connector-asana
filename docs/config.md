# Configuring Asana Operations

[[Prerequisites]](#Prerequisites) [[Initializing the Connector]](#initializing-the-connector)

## Prerequisites

### Get User Credentials

Create an Asana account using URL: https://app.asana.com/

1. Follow the below mentioned steps to generate the access token

2. Login to the created Asana account and go to https://asana.com/developers/documentation/getting-started/auth#register-an-app 

3. Click on “visit your Account Settings dialog”

4. Click on Developer create application or Manage Developer App

5. Give proper values for
   
   * App Name - New application name
   * App URL - Enter any sample URL
   * Redirect URL -  Enter the Callback URL
   
6. Click on create and get client Id, client Secret. Store them for future use

7. Get the Authorization code from Azure Access Control Service Construct the authorization url as: ``` https://app.asana.com/-/oauth_authorize?client_id=<client_Id>&redirect_uri=<redirect_url>&response_type=code&state=somerandomstate ```
   
8. Asana Online site redirects the browser back to the redirect URI that was specified when the app was registered in step 5. It also includes the authorization code as a query string. The redirect URL is structured like: ``` https://redirect_url?code=<authorization_code>&state=somerandomstate ```. Extract query string value code from the url and it will be used in next step.

9. Get the access token and refresh token from code, construct the post request URL: ``` https://app.asana.com/-/oauth_token?client_id=<client_id>&client_secret=<client_secret>&redirect_uri=<redirect_uri>&code=<authorization_code>&grant_type=authorization_code ```

10. Get the access token from refresh token:
    
    This step is almost similar to step 9, except two differences. Here the differences are that we use:
    * grant_type as refresh_token and
    * refresh_token instead of code in step 9 and use the refresh token which we have saved in step 9.<br/>
    URL:  ``` https://app.asana.com/-/oauth_token?client_id=<client_id>&client_secret=<client_secret>&redirect_uri=<redirect_uri>&refresh_token=<refresh_token>&grant_type=refresh_token ```

## Initializing the Connector

To use the Asana connector, add the <asana.init> element in your configuration before carrying out any other Asana operations.

Asana uses OAuth 2.0 authentication to authorize API calls. For more information on authentication, see https://asana.com/developers/documentation/getting-started/auth.

**init**
```xml
<asana.init>
    <apiUrl>{$ctx:apiUrl}</apiUrl>
    <apiVersion>{$ctx:apiVersion}</apiVersion>
    <accessToken>{$ctx:accessToken}</accessToken>
    <refreshToken>{$ctx:refreshToken}</refreshToken>
    <clientId>{$ctx:clientId}</clientId>
    <clientSecret>{$ctx:clientSecret}</clientSecret>
    <grantType>{$ctx:grantType}</grantType>
    <redirectUri>{$ctx:redirectUri}</redirectUri>
    <registryPath>{$ctx:registryPath}</registryPath>
</asana.init>
```
**Properties** 
* apiUrl: The URL of the Asana REST API.
* apiVersion:The version of the Asana REST API.
* accessToken: The token used to authorize requests that come into the API.
* refreshToken: A long­-lived token that is used to get new access tokens when old tokens expire.
* clientId: The ID, which uniquely identifies the application that makes the request.
* clientSecret: The client secret of the app, which can be found in the details pane of the developer console.
* grantType:  Specify the value of the refreshToken.
* redirectUri: The URI to redirect to at the time of success or error. This should match the Redirect URL specified in the application settings.
* registryPath: The registry path of the connector.

Now that you have connected to Asana, use the information in the following topics to perform various operations with the connector:

[Working with Attachments in Asana](attachments.md)

[Working with Events in Asana](events.md)

[Working with Projects in Asana](projects.md)

[Working with Stories in Asana](stories.md)

[Working with Tags in Asana](tags.md)

[Working with Tasks in Asana](tasks.md)

[Working with Typeahead in Asana](typeahead.md)

[Working with Users in Asana](users.md)

[Working with Workspaces in Asana](workspaces.md)
