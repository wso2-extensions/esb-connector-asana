# Working with Typeahead in Asana

The query operation retrieves typeahead search results. 

**query**
```xml
<asana.query>
    <workspace>{$ctx:workspace}</workspace>
    <type>{$ctx:type}</type>
    <query>{$ctx:query}</query>
    <count>{$ctx:count}</count>
</asana.query>
```

**Properties**
* workspace: The ID of the workspace.
* type: The type of object to lookup. 
* query: The value to lookup.
* count: The maximum number of results to return.

**Sample request**

Following is a sample request that can be handled by the query operation.

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
    "workspace":"65796816841176",
    "type":"user",
    "query":"test_username",
    "count":"10"
}
```

**Sample response**

Given below is a sample response for the query operation.

```json
{
  "data": [
  {
    "id": 999,
    "resource_type": "user"
    "name": "Greg Sanchez",
    ...
  },
  ...
  ]
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/typeaheads#query

### Sample configuration

Following example illustrates how to connect to Asana with the init operation and query operation.

1. Create a sample proxy as below :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<proxy xmlns="http://ws.apache.org/ns/synapse"
       name="query"
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
         <property expression="json-eval($.type)" name="type"/>
         <property expression="json-eval($.query)" name="query"/>
         <property expression="json-eval($.count)" name="count"/>
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
       <asana.query>
        <workspace>{$ctx:workspace}</workspace>
        <type>{$ctx:type}</type>
        <query>{$ctx:query}</query>
        <count>{$ctx:count}</count>
     </asana.query>
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
2. Create an json file named query.json and copy the configurations given below to it:

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
    "workspace":"65796816841176",
    "type":"user",
    "query":"test_username",
    "count":"10"
}
```

3. Replace the credentials with your values.

4. Execute the following curl command:

```bash
curl http://localhost:8280/services/query -H "Content-Type: application/json" -d @query.json
```
5. Asana returns an json response similar to the one shown below:
 
```json
{
  "data": [
  {
    "id": 999,
    "resource_type": "user"
    "name": "Greg Sanchez",
    ...
  },
  ...
  ]
}
```