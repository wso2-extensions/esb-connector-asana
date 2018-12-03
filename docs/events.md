# Working with Events in Asana

The getEventsOnResource operation returns a complete record of all events that take place with regard to a particular resource from the time the sync token is created.

**getEventsOnResource**
```xml
<asana.getEventsOnResource>
    <resource>{$ctx:resource}</resource>
    <sync>{$ctx:sync}</sync>
</asana.getEventsOnResource>
```

**Properties**
* resource: The resource ID for which you want to retrieve events.
* sync: The sync token obtained from the last request. If it is the first sync specify none.

**Sample request**

Following is a sample request that can be handled by the getEventsOnResource operation.

```json
{
    "accessToken":"accesstoken",
    "registryPath":"asana",
    "apiUrl":"https://app.asana.com/api",              
    "apiVersion":"1.0",
    "refreshToken":"test_0/d75771b603e2205c236a79348325d5db",
    "clientId":"test_33494404050100",
    "clientSecret":"test_a6904447b431b44a7b1f7bf5cfeeafcd",
    "grantType":"refresh_token",
    "redirectUri":"https://www.tumblr.com/blog/rapv4",
    "resource":"80998315044485",
    "sync":"dfed15a1e67e3a4a05bc443040f70d4c:0"
}
```

**Sample response**

Given below is a sample response for the getEventsOnResource operation.

```json
{
  "data": [
    {
      "resource": {
        "id": 1337,
        "gid": "1337",
        "name": "My Task",
        "resource_type": "task",
        "resource_subtype": "default_task"
      },
      "parent": null,
      "created_at": "2013-08-21T18:20:37.972Z",
      "user": {
        "id": 1123,
        "gid": "1123",
        "name": "Tom Bizarro",
        "resource_type": "user"
      },
      "action": "changed",
      "type": "task"
    },
    {
      "resource": {
        "id": 1338,
        "gid": "1338",
        "resource_type": "task",
        "resource_subtype": "default_task",
        "name": "My Other Task"
      },
      "parent": null,
      "created_at": "2013-08-21T18:22:45.421Z",
      "user": {
        "id": 1428,
        "gid": "1428",
        "resource_type": "user",
        "name": "Greg Sanchez"
      },
      "action": "changed",
      "type": "task"
    }
  ],
  "sync": "edfc0896b370b7a479886d316131bf5c:0"
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/events#get-all

### Sample configuration

Following example illustrates how to connect to Asana with the init operation and getEventsOnResource operation.

1. Create a sample proxy as below :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<proxy xmlns="http://ws.apache.org/ns/synapse"
       name="getEventsOnResource"
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
         <property expression="json-eval($.resource)" name="resource"/>
         <property expression="json-eval($.sync)" name="sync"/>
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
         <asana.getEventsOnResource>
            <resource>{$ctx:resource}</resource>
            <sync>{$ctx:sync}</sync>
        </asana.getEventsOnResource>
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
2. Create an json file named getEventsOnResource.json and copy the configurations given below to it:

```json
{
    "accessToken":"accesstoken",
    "registryPath":"asana",
    "apiUrl":"https://app.asana.com/api",              
    "apiVersion":"1.0",
    "refreshToken":"test_0/d75771b603e2205c236a79348325d5db",
    "clientId":"test_33494404050100",
    "clientSecret":"test_a6904447b431b44a7b1f7bf5cfeeafcd",
    "grantType":"refresh_token",
    "redirectUri":"https://www.tumblr.com/blog/rapv4",
    "resource":"80998315044485",
    "sync":"dfed15a1e67e3a4a05bc443040f70d4c:0"
}
```

3. Replace the credentials with your values.

4. Execute the following curl command:

```bash
curl http://localhost:8280/services/getEventsOnResource -H "Content-Type: application/json" -d @getEventsOnResource.json
```
5. Asana returns an json response similar to the one shown below:
 
```json
{
  "data": [
    {
      "resource": {
        "id": 1337,
        "gid": "1337",
        "name": "My Task",
        "resource_type": "task",
        "resource_subtype": "default_task"
      },
      "parent": null,
      "created_at": "2013-08-21T18:20:37.972Z",
      "user": {
        "id": 1123,
        "gid": "1123",
        "name": "Tom Bizarro",
        "resource_type": "user"
      },
      "action": "changed",
      "type": "task"
    },
    {
      "resource": {
        "id": 1338,
        "gid": "1338",
        "resource_type": "task",
        "resource_subtype": "default_task",
        "name": "My Other Task"
      },
      "parent": null,
      "created_at": "2013-08-21T18:22:45.421Z",
      "user": {
        "id": 1428,
        "gid": "1428",
        "resource_type": "user",
        "name": "Greg Sanchez"
      },
      "action": "changed",
      "type": "task"
    }
  ],
  "sync": "edfc0896b370b7a479886d316131bf5c:0"
}
```