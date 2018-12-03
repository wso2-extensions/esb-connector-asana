# Working with Workspaces in Asana

[[Overview]](#overview)  [[Operation details]](#operation-details)  [[Sample configuration]](#sample-configuration)

### Overview 

The following operations allow you to work with workspaces. Click an operation name to see details on how to use it.
For a sample proxy service that illustrates how to work with workspaces, see [Sample configuration](#sample-configuration).

| Operation        | Description |
| ------------- |-------------|
| [addUser](#adding-a-user)    | Adds user to a workspace.  |
| [getAllWorkspaces](#retrieving-all-workspaces)      | Retrieves all workspaces.  |
| [getWorkspace](#retrieving-a-workspace)      | Retrieves a specific workspace. |
| [updateWorkspace](#updating-a-workspace )      | Updates a workspace.  |
| [typeaheadSearch](#retrieving-objects-from-a-workspace)      | Retrieves objects from a workspace.  |

### Operation details

This section provides further details on the operations related to workspaces.

#### Adding a user

The addUser operation adds a user to a workspace.

**addUser**
```xml
<asana.addUser>
    <workspace>{$ctx:workspace}</workspace>
    <user>{$ctx:user}</user>
</asana.addUser>
```

**Properties**
* workspace: The ID of the workspace.
* user:The user ID.

**Sample request**

Following is a sample request that can be handled by the addUser operation.

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
    "name":"new Tag again",
    "workspace":"65796816841176",
    "user":"dayasha1006@gmail.com" 
}
```

**Sample response**

Given below is a sample response for the addUser operation.

```json
{
   "data":{
      "gid":"85705335517470",
      "id":85705335517470,
      "name":"dayasha1006@gmail.com",
      "email":"dayasha1006@gmail.com",
      "workspaces":[
         {
            "gid":"823749000161232",
            "id":823749000161232,
            "name":"University Of Jaffna"
         }
      ],
      "photo":null
   }
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/workspaces#user-mgmt

#### Retrieving all workspaces

The getAllWorkspaces operation retrieves all workspaces.

**getAllWorkspaces**
```xml
<asana.getAllWorkspaces/> 
```

**Sample request**

Following is a sample request that can be handled by the getAllWorkspaces operation.

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
    "redirectUri":"https://www.tumblr.com/blog/rapv4"
}
```

**Sample response**

Given below is a sample response for the getAllWorkspaces operation.

```json
{
   "data":[
      {
         "id":823749000161232,
         "gid":"823749000161232",
         "name":"University Of Jaffna"
      }
   ]
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/workspaces#get

#### Retrieving a workspace

The getWorkspace operation retrieves a workspace based on the specified workspace ID.

**getWorkspace**
```xml
<asana.getWorkspace>
    <workspace>{$ctx:workspace}</workspace>
</asana.getWorkspace>
```

**Properties**
* workspace: The ID of the workspace you want to retrieve.

**Sample request**

Following is a sample request that can be handled by the getWorkspace operation.

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

Given below is a sample response for the getWorkspace operation.

```json
{
   "data":{
      "id":823749000161232,
      "gid":"823749000161232",
      "email_domains":[

      ],
      "is_organization":false,
      "name":"University Of Jaffna"
   }
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/workspaces#get

#### Updating a workspace 

The updateWorkspace operation updates an existing workspace.

**updateWorkspace**
```xml
<asana.updateWorkspace>      
    <workspace>{$ctx:workspace}</workspace>
    <name>{$ctx:name}</name>
</asana.updateWorkspace>
```

**Properties**
* workspace: The ID of the workspace.
* name:The name of the workspace.

**Sample request**

Following is a sample request that can be handled by the updateWorkspace operation.

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
    "workspace":"67377290416636",
    "name":"University Of Jaffna" 
}
```

**Sample response**

Given below is a sample response for the updateWorkspace operation.

```json
{
   "data":{
      "gid":"823749000161232",
      "id":823749000161232,
      "name":"University Of Jaffna",
      "is_organization":false,
      "email_domains":[

      ]
   }
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/workspaces#update

#### Retrieving objects from a workspace

The typeaheadSearch operation retrieves objects from a workspace based on an autocomplete/typeahead search algorithm.

**typeaheadSearch**
```xml
<asana.typeaheadSearch>
    <workspace>{$ctx:workspace}</workspace>
    <type>{$ctx:type}</type>
    <query>{$ctx:query}</query>
    <count>{$ctx:count}</count>
</asana.typeaheadSearch>
```

**Properties**
* workspace :  The ID of the workspace.
* type:The type of values that the typeahead should return.
* query:The query string that should be used to search for objects.
* count: The maximum number of results to return.

**Sample request**

Following is a sample request that can be handled by the typeaheadSearch operation.

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
    "workspace":"65796816841176",
    "type":"user",
    "query":"d",
    "count":"10"
}
```

**Sample response**

Given below is a sample response for the typeaheadSearch operation.

```json
{
   "data":[
      {
         "id":823747606996969,
         "gid":"823747606996969",
         "name":"task"
      },
      {
         "id":823747606996963,
         "gid":"823747606996963",
         "name":"Task 1"
      }
   ]
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/workspaces#typeahead

### Sample configuration

Following example illustrates how to connect to Asana with the init operation and updateWorkspace operation.

1. Create a sample proxy as below :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<proxy xmlns="http://ws.apache.org/ns/synapse"
       name="updateWorkspace"
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
         <property expression="json-eval($.workspace)" name="workspace"/>
         <property expression="json-eval($.name)" name="name"/>
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
      <asana.updateWorkspace>
        <workspace>{$ctx:workspace}</workspace>
        <name>{$ctx:name}</name>
     </asana.updateWorkspace>
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
2. Create an json file named updateWorkspace.json and copy the configurations given below to it:

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
    "workspace":"67377290416636",
    "name":"University Of Jaffna" 
}
```

3. Replace the credentials with your values.

4. Execute the following curl command:

```bash
curl http://localhost:8280/services/updateWorkspace -H "Content-Type: application/json" -d @updateWorkspace.json
```
5. Asana returns an json response similar to the one shown below:
 
```json
{
   "data":{
      "gid":"823749000161232",
      "id":823749000161232,
      "name":"University Of Jaffna",
      "is_organization":false,
      "email_domains":[

      ]
   }
}
```