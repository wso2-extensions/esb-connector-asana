# Working with Attachments in Asana

[[Overview]](#overview)  [[Operation details]](#operation-details)  [[Sample configuration]](#sample-configuration)

### Overview 

The following operations allow you to work with attachments. Click an operation name to see details on how to use it.
For a sample proxy service that illustrates how to work with attachments, see [Sample configuration](#sample-configuration).

| Operation        | Description |
| ------------- |-------------|
| [getSingleAttachment](#retrieving-a-single-attachment)    | Retrieves a single attachment by ID. |
| [getAllAttachments](#retrieving-all-attachments)      | Retrieves all attachments related to a particular task. |

### Operation details

This section provides further details on the operations related to attachments.

#### Retrieving a single attachment

The getSingleAttachment operation retrieves a single attachment based on the specified ID.

**getSingleAttachment**
```xml
<asana.getSingleAttachment>
    <attachmentId>{$ctx:attachmentId}</attachmentId>
</asana.getSingleAttachmentProperties>
```

**Properties**
* attachmentId: The ID of an attachment.

**Sample request**

Following is a sample request that can be handled by the getSingleAttachment operation.

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
    "attachmentId":"79029564149023"
}
```

**Sample response**

Given below is a sample response for the getSingleAttachment operation.

```json
{
  "data": {
    "name": "Screenshot.png",
    "resource_type": "attachment",
    "parent": {
      "id": 1337,
      "gid": "1337",
      "resource_type": "task",
      "name": "My Task"
    },
    "view_url": "https://www.dropbox.com/s/1234567890abcdef/Screenshot.png",
    "created_at": "2018-10-12T03:34:50Z",
    "download_url": "https://www.dropbox.com/s/1234567890abcdef/Screenshot.png?dl=1",
    "host": "dropbox",
    "id": 5678,
    "gid": "5678"
  }
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/attachments#get-single

#### Retrieving all attachments

The getAllAttachments operation retrieves all attachment related to specific task.

**getAllAttachments**
```xml
<asana.getAllAttachments>
    <taskId>{$ctx:taskId}</taskId>
</asana.getAllAttachments>
```

**Properties**
* taskId: The ID of the task.

**Sample request**

Following is a sample request that can be handled by the getAllAttachments operation.

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
    "taskId":"78999896872769"
}
```

**Sample response**

Given below is a sample response for the getAllAttachments operation.

```json
{
  "data": [
    {
      "id": 5678,
      "gid": "5678",
      "resource_type": "attachment",
      "name": "Background.png"
    },
    {
      "id": 9012,
      "gid": "9012",
      "resource_type": "attachment",
      "name": "New Design Draft.pdf"
    },
    "~..."
  ]
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/attachments#get-all-task

### Sample configuration

Following example illustrates how to connect to Asana with the init operation and getSingleAttachment operation.

1. Create a sample proxy as below :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<proxy xmlns="http://ws.apache.org/ns/synapse"
       name="getSingleAttachment"
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
         <property expression="json-eval($.attachmentId)" name="attachmentId"/>
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
         <asana.getSingleAttachment>
            <attachmentId>{$ctx:attachmentId}</attachmentId>
         </asana.getSingleAttachment>
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
2. Create an json file named getSingleAttachment.json and copy the configurations given below to it:

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
    "attachmentId":"79029564149023"
}
```

3. Replace the credentials with your values.

4. Execute the following curl command:

```bash
curl http://localhost:8280/services/getSingleAttachment -H "Content-Type: application/json" -d @getSingleAttachment.json
```
5. Asana returns an json response similar to the one shown below:
 
```json
{
  "data": {
    "name": "Screenshot.png",
    "resource_type": "attachment",
    "parent": {
      "id": 1337,
      "gid": "1337",
      "resource_type": "task",
      "name": "My Task"
    },
    "view_url": "https://www.dropbox.com/s/1234567890abcdef/Screenshot.png",
    "created_at": "2018-10-12T03:34:50Z",
    "download_url": "https://www.dropbox.com/s/1234567890abcdef/Screenshot.png?dl=1",
    "host": "dropbox",
    "id": 5678,
    "gid": "5678"
  }
}
```