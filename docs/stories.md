# Working with Stories in Asana

[[Overview]](#overview)  [[Operation details]](#operation-details)  [[Sample configuration]](#sample-configuration)

### Overview 

The following operations allow you to work with stories. Click an operation name to see details on how to use it.
For a sample proxy service that illustrates how to work with stories, see [Sample configuration](#sample-configuration).

| Operation        | Description |
| ------------- |-------------|
| [getStoriesOnObject](#retrieving-stories-on-a-task)    | Retrieves all stories related to a specific task. |
| [getSingleStory](#retrieving-a-single-story)      | Retrieves a single story by ID. |
| [commentOnObject](#adding-a-comment-on-an-object)      | Adds a comment to a task. |

### Operation details

This section provides further details on the operations related to stories.

#### Retrieving stories on a task

The getStoriesOnObject operation retrieves all stories related to a specific task.

**getStoriesOnObject**
```xml
<asana.getStoriesOnObject>
    <taskId>{$ctx:taskId}</taskId>
</asana.getStoriesOnObject>
```

**Properties**
* taskId: The ID of the task for which you need to retrieve all stories.

**Sample request**

Following is a sample request that can be handled by the getStoriesOnObject operation.

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
    "taskId":"80998315044486"
}
```

**Sample response**

Given below is a sample response for the getStoriesOnObject operation.

```json
{
  "data": [
    {
      "id": 2001,
      "gid": "2001",
      "resource_type": "story",
      "resource_subtype": "added_to_project",
      "text": "added to Things To Buy",
      "created_at": "2011-12-21T23:23:01.259Z",
      "type": "system",
      "created_by": {
        "id": 5678,
        "gid": "5678",
        "resource_type": "user",
        "name": "Greg Sanchez"
      }
    },
    {
      "id": 2002,
      "gid": "2002",
      "resource_type": "story",
      "resource_subtype": "comment_added",
      "text": "Again? Wow, we really go through this stuff fast.",
      "created_at": "2012-01-02T21:32:40.112Z",
      "type": "comment",
      "created_by": {
        "id": 1234,
        "gid": "1234",
        "resource_type": "user",
        "name": "Tim Bizarro"
      }
    }
  ]
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/stories#get-all

#### Retrieving a single story

The getSingleStory operation retrieve a single story based on the specified story ID.

**getSingleStory**
```xml
<asana.getSingleStory>
    <storyId>{$ctx:storyId}</storyId>
</asana.getSingleStory>
```

**Properties**
* storyId: The story ID.

**Sample request**

Following is a sample request that can be handled by the getSingleStory operation.

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
    "storyId":"80998315044488"
}
```

**Sample response**

Given below is a sample response for the getSingleStory operation.

```json
{
  "data": {
    "id": 2001,
    "gid": "2001"
    "resource_type": "story",
    "resource_subtype": "comment_added",
    "target": {
      "id": 1234,
      "gid": "1234",
      "resource_type": "task",
      "name": "Buy catnip"
    },
    "text": "Yes, please!",
    "created_at": "2012-02-22T02:06:58.147Z",
    "created_by": {
      "id": 1123,
      "gid": "1123",
      "resource_type": "user",
      "name": "Mittens"
    },
    "source": "web",
    "type": "comment",
    "is_edited": false,
    "is_pinned": false
  }
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/stories#get-single

#### Adding a comment on an object 

The commentOnObject operation adds a comment to a task.

**commentOnObject**
```xml
<asana.commentOnObject>
    <taskId>{$ctx:taskId}</taskId>
    <text>{$ctx:text}</text>
</asana.commentOnObject>
```

**Properties**
* taskId: The ID of the task for which you need to add a comment.
* text: The comment you want to add.

**Sample request**

Following is a sample request that can be handled by the commentOnObject operation.

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
    "taskId":"80998315044486",
    "text":"This is a test comment."
}
```

**Sample response**

Given below is a sample response for the commentOnObject operation.

```json
{
  "data": {
    "id": 2001,
    "gid": "2001"
    "resource_type": "story",
    "resource_subtype": "comment_added",
    "target": {
      "id": 1001,
      "gid": "1001",
      "resource_type": "task",
      "name": "Buy catnip"
    },
    "text": "This is a very nice comment.",
    "created_at": "2011-12-21T23:23:01.259Z",
    "created_by": {
      "id": 5678,
      "gid": "5678",
      "resource_type": "user",
      "name": "Greg Sanchez"
    },
    "source": "api",
    "type": "comment",
    "is_edited": false,
    "is_pinned": false
  }
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/stories#post-comment


### Sample configuration

Following example illustrates how to connect to Asana with the init operation and commentOnObject operation.

1. Create a sample proxy as below :

```xml
<proxy xmlns="http://ws.apache.org/ns/synapse"
       name="commentOnObject"
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
      <property expression="json-eval($.taskId)" name="taskId"/>
      <property expression="json-eval($.text)" name="text"/>
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
      <asana.commentOnObject>
        <taskId>{$ctx:taskId}</taskId>
        <text>{$ctx:text}</text>
      </asana.commentOnObject>
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
2. Create an json file named commentOnObject.json and copy the configurations given below to it:

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
    "taskId":"80998315044486",
    "text":"This is a test comment."
}
```

3. Replace the credentials with your values.

4. Execute the following curl command:

```bash
curl http://localhost:8280/services/commentOnObject -H "Content-Type: application/json" -d @commentOnObject.json
```
5. Asana returns an json response similar to the one shown below:
 
```json
{
  "data": {
    "id": 2001,
    "gid": "2001"
    "resource_type": "story",
    "resource_subtype": "comment_added",
    "target": {
      "id": 1001,
      "gid": "1001",
      "resource_type": "task",
      "name": "Buy catnip"
    },
    "text": "This is a very nice comment.",
    "created_at": "2011-12-21T23:23:01.259Z",
    "created_by": {
      "id": 5678,
      "gid": "5678",
      "resource_type": "user",
      "name": "Greg Sanchez"
    },
    "source": "api",
    "type": "comment",
    "is_edited": false,
    "is_pinned": false
  }
}
```