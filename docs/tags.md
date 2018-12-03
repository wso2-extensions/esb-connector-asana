# Working with Tags in Asana

[[Overview]](#overview)  [[Operation details]](#operation-details)  [[Sample configuration]](#sample-configuration)

### Overview 

The following operations allow you to work with tags. Click an operation name to see details on how to use it.
For a sample proxy service that illustrates how to work with tags, see [Sample configuration](#sample-configuration).

| Operation        | Description |
| ------------- |-------------|
| [createTag](#creating-a-new-tag)    | Creates a new tag in a workspace or organization.  |
| [getSingleTag](#retrieving-a-single-tag)      | Retrieves the complete tag record for a single tag.  |
| [updateTag](#updating-a-tag)      | Updates the properties of a tag. |
| [queryForTags](#querying-for-tags)      | Retrieves tag records based on the specified filter criteria.  |
| [getTasksWithTag](#retrieving-tasks-with-a-specific-tag)      | Retrieves task records of all tasks with a specific tag.  |

### Operation details

This section provides further details on the operations related to tags.

#### Creating a new tag

The createTag operation creates a new tag in a workspace or organization.

**createTag**
```xml
<asana.createTag>
    <name>{$ctx:name}</name>
    <workspace>{$ctx:workspace}</workspace>
</asana.createTag>
```

**Properties**
* name: The name of the tag.
* workspace: The workspace or organization where you want to create the tag.

**Sample request**

Following is a sample request that can be handled by the createTag operation.

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
    "workspace":"67377290416636"
}
```

**Sample response**

Given below is a sample response for the createTag operation.

```json
{
   "data":{
      "gid":"826159578811281",
      "id":826159578811281,
      "created_at":"2018-09-18T08:20:27.886Z",
      "name":"",
      "notes":"",
      "workspace":{
         "gid":"823749000161232",
         "id":823749000161232,
         "name":"University Of Jaffna"
      },
      "color":null,
      "followers":[

      ]
   }
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/tags#create

#### Retrieving a single tag

The getSingleTag operation retrieves a complete tag record based on the specified tag ID.

**getSingleTag**
```xml
<asana.getSingleTag>
    <tagId>{$ctx:tagId}</tagId>
</asana.getSingleTag>
```

**Properties**
* tagId: The tag ID to retrieve the complete tag record.

**Sample request**

Following is a sample request that can be handled by the getSingleTag operation.

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
    "tagId":"81165988446923"
}
```

**Sample response**

Given below is a sample response for the getSingleTag operation.

```json
{
  "data": {
    "id": 1331,
    "gid": "1331",
    "resource_type": "tag",
    "name": "Things to Buy",
    "null": "..."
  }
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/tags#get-single

#### Updating a tag

The updateTag operation updates properties of a tag. 

**updateTag**
```xml
<asana.updateTag>
    <tagId>{$ctx:tagId}</tagId>
    <name>{$ctx:name}</name>
</asana.updateTag>
```

**Properties**
* tagId: The ID of a tag you want to update.
* name: The name of the tag you want to update.

**Sample request**

Following is a sample request that can be handled by the updateTag operation.

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
    "tagId":"81249141470707",
    "name":"For testTag again"
}
```

**Sample response**

Given below is a sample response for the updateTag operation.

```json
{
  "data": {
    "null": "...",
    "id": 1331,
    "gid": "1331",
    "resource_type": "tag",
    "name": "Things to Sell"
  }
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/tags#update

#### Querying for tags

The queryForTags operation retrieves tag records based on the specified filter criteria.

**queryForTags**
```xml
<asana.queryForTags>
    <workspace>{$ctx:workspace}</workspace>
</asana.queryForTags>
```

**Properties**
* workspace: The ID of the workspace to filter tags.

**Sample request**

Following is a sample request that can be handled by the queryForTags operation.

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
    "workspace":"67377290416636"
}
```

**Sample response**

Given below is a sample response for the queryForTags operation.

```json
{
  "data": {
    "id": 1331,
    "gid": "1331",
    "resource_type": "tag",
    "name": "Things to Buy",
    "null": "..."
  }
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/tags#query

#### Retrieving tasks with a specific tag

The getTasksWithTag operation retrieves all task records related to a specific tag.

**getTasksWithTag**
```xml
<asana.getTasksWithTag>
    <tagId>{$ctx:tagId}</tagId>
</asana.getTasksWithTag>
```

**Properties**
* tagId: The ID of the tag to retrieve tasks.

**Sample request**

Following is a sample request that can be handled by the getTasksWithTag operation.

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
    "tagId":"81165988446923"
}
```

**Sample response**

Given below is a sample response for the getTasksWithTag operation.

```json
{
  "data": [
    {
      "id": 2001,
      "gid": "2001",
      "resource_type": "task",
      "name": "Catnip"
    },
    {
      "id": 2002,
      "gid": "2002",
      "resource_type": "task",
      "name": "Kitty litter"
    },
    "~..."
  ]
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/tags#get-tasks

### Sample configuration

Following example illustrates how to connect to Asana with the init operation and createTag operation.

1. Create a sample proxy as below :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<proxy xmlns="http://ws.apache.org/ns/synapse"
       name="createTag"
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
         <property expression="json-eval($.name)" name="name"/>
         <property expression="json-eval($.workspace)" name="workspace"/>
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
         <asana.createTag>
            <name>{$ctx:name}</name>
            <workspace>{$ctx:workspace}</workspace>
        </asana.createTag>
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
2. Create an json file named createTag.json and copy the configurations given below to it:

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
    "workspace":"67377290416636"
}
```

3. Replace the credentials with your values.

4. Execute the following curl command:

```bash
curl http://localhost:8280/services/createTag -H "Content-Type: application/json" -d @createTag.json
```
5. Asana returns an json response similar to the one shown below:
 
```json
{
   "data":{
      "gid":"826159578811281",
      "id":826159578811281,
      "created_at":"2018-09-18T08:20:27.886Z",
      "name":"",
      "notes":"",
      "workspace":{
         "gid":"823749000161232",
         "id":823749000161232,
         "name":"University Of Jaffna"
      },
      "color":null,
      "followers":[

      ]
   }
}
```