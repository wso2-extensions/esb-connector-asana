# Working with Users in Asana

[[Overview]](#overview)  [[Operation details]](#operation-details)  [[Sample configuration]](#sample-configuration)

### Overview 

The following operations allow you to work with users. Click an operation name to see details on how to use it.
For a sample proxy service that illustrates how to work with users, see [Sample configuration](#sample-configuration).

| Operation        | Description |
| ------------- |-------------|
| [getUser](#retrieving-a-single-user)    | Retrieves the complete user record of the currently authenticated user. |
| [getAllUsers](#retrieving-all-users)      | Retrieves user records of all users in a specific workspace or organization. |

### Operation details

This section provides further details on the operations related to users.

#### Retrieving a single user

The getUser operation retrieves the complete user record of the currently authenticated user.

**getUser**
```xml
<asana.getUser>
    <userId>{$ctx:userId}</userId>
</asana.getUser>
```

**Properties**
* userId: The unique ID of the user.

**Sample request**

Following is a sample request that can be handled by the getUser operation.

```json
{
    "accessToken":"accesstoken",
    "registryPath":"asana",
    "apiUrl":"https://app.asana.com/api",
    "apiVersion":"1.0",
    "refreshToken":"test_0/a0ed35a193f705be60d51cf74c511d4e",
    "clientId":"test_68165755399070",
    "clientSecret":"test_0598930285f5a613983622341fb60cf7",
    "grantType":"refresh_token",
    "redirectUri":"https://www.tumblr.com/blog/rapv4",
    "userId":"67375572029644"
}
```

**Sample response**

Given below is a sample response for the getUser operation.

```json
{
  "data": {
    "workspaces": [
      {
        "id": 1337,
        "gid": "1337",
        "resource_type": "workspace",
        "name": "My Favorite Workspace"
      },
      "~..."
    ],
    "id": 5678,
    "gid": "5678",
    "resource_type": "user",
    "name": "Greg Sanchez",
    "email": "gsanchez@example.com"
  }
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/users#get-single

#### Retrieving all users

The getAllUsers operation retrieves user records of all users in a specific workspace or organization.

**getAllUsers**
```xml
<asana.getAllUsers>
    <workspace>{$ctx:workspace}</workspace>
</asana.getAllUsers>
```

**Properties**
* workspace: The ID of the workspace.

**Sample request**

Following is a sample request that can be handled by the getAllUsers operation.

```json
{
    "accessToken":"accesstoken",
    "registryPath":"asana",
    "apiUrl":"https://app.asana.com/api",
    "apiVersion":"1.0",
    "refreshToken":"test_0/a0ed35a193f705be60d51cf74c511d4e",
    "clientId":"test_68165755399070",
    "clientSecret":"test_0598930085f5a613983622341fb60cf7",
    "grantType":"refresh_token",
    "redirectUri":"https://www.tumblr.com/blog/rapv4",
    "workspace":"65796816841176"
}
```

**Sample response**

Given below is a sample response for the getAllUsers operation.

```json
{
  "data": [
    {
      "id": 1234,
      "gid": "1234",
      "resource_type": "user",
      "name": "Tim Bizarro",
      "email": "tbizarro@example.com"
    },
    {
      "id": 5678,
      "gid": "5678",
      "resource_type": "user",
      "name": "Greg Sanchez",
      "email": "gsanchez@example.com"
    },
    "~..."
  ]
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/users#get-all

### Sample configuration

Following example illustrates how to connect to Asana with the init operation and getUser operation.

1. Create a sample proxy as below :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<proxy xmlns="http://ws.apache.org/ns/synapse"
       name="getUser"
       startOnLoad="true"
       statistics="disable"
       trace="disable"
       transports="http,https">
   <target>
      <inSequence>
         <property expression="json-eval($.apiUrl)" name="apiUrl"/>
         <property expression="json-eval($.apiVersion)" name="apiVersion"/>
         <property expression="json-eval($.refreshToken)" name="refreshToken"/>
         <property expression="json-eval($.clientId)" name="clientId"/>
         <property expression="json-eval($.clientSecret)" name="clientSecret"/>
         <property expression="json-eval($.grantType)" name="grantType"/>
         <property expression="json-eval($.redirectUri)" name="redirectUri"/>
         <property expression="json-eval($.accessToken)" name="accessToken"/>
         <property expression="json-eval($.registryPath)" name="registryPath"/>
         <property expression="json-eval($.userId)" name="userId"/>
         <asana.init>
            <apiUrl>{$ctx:apiUrl}</apiUrl>
            <apiVersion>{$ctx:apiVersion}</apiVersion>
            <refreshToken>{$ctx:refreshToken}</refreshToken>
            <clientId>{$ctx:clientId}</clientId>
            <clientSecret>{$ctx:clientSecret}</clientSecret>
            <grantType>{$ctx:grantType}</grantType>
            <redirectUri>{$ctx:redirectUri}</redirectUri>
            <accessToken>{$ctx:accessToken}</accessToken>
            <registryPath>{$ctx:registryPath}</registryPath>
         </asana.init>
      <asana.getUser>
        <userId>{$ctx:userId}</userId>
      </asana.getUser>
         <respond/>
      </inSequence>
      <outSequence>
         <log/>
         <send/>
      </outSequence>
   </target>
   <description/>
</proxy>
```
2. Create an json file named getUser.json and copy the configurations given below to it:

```json
{
    "accessToken":"accesstoken",
    "registryPath":"asana",
    "apiUrl":"https://app.asana.com/api",
    "apiVersion":"1.0",
    "refreshToken":"test_0/a0ed35a193f705be60d51cf74c511d4e",
    "clientId":"test_68165755399070",
    "clientSecret":"test_0598930285f5a613983622341fb60cf7",
    "grantType":"refresh_token",
    "redirectUri":"https://www.tumblr.com/blog/rapv4",
    "userId":"67375572029644"
}
```

3. Replace the credentials with your values.

4. Execute the following curl command:

```bash
curl http://localhost:8280/services/getUser -H "Content-Type: application/json" -d @getUser.json
```
5. Asana returns an json response similar to the one shown below:
 
```json
{
  "data": {
    "workspaces": [
      {
        "id": 1337,
        "gid": "1337",
        "resource_type": "workspace",
        "name": "My Favorite Workspace"
      },
      "~..."
    ],
    "id": 5678,
    "gid": "5678",
    "resource_type": "user",
    "name": "Greg Sanchez",
    "email": "gsanchez@example.com"
  }
}
```