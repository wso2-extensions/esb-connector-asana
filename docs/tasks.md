# Working with Tasks in Asana

[[Overview]](#overview)  [[Operation details]](#operation-details)  [[Sample configuration]](#sample-configuration)

### Overview 

The following operations allow you to work with tasks. Click an operation name to see details on how to use it.
For a sample proxy service that illustrates how to work with tasks, see [Sample configuration](#sample-configuration).

| Operation        | Description |
| ------------- |-------------|
| [createTask](#creating-a-new-task)    | Creates a new task.   |
| [getTask](#retrieving-a-task)      | Retrieves a single task.   |
| [updateTask](#updating-a-task)      | Updates the properties of a tasks. |
| [deleteTask](#deleting-a-task)      | Deletes an existing task.  |
| [queryForTask](#querying-for-tasks)      | Retrieves the compact task records based on the specified filter criteria. |
| [getAllSubtasks ](#retrieving-all-subtasks)      | Retrieves a compact representation of all subtasks of a particular task.  |
| [createSubTask](#creating-a-subtask)      | Creates a new subtask and adds it to the parent task.  |
| [changeParentOfTask](#changing-the-parent-task-of-a-subtask)      | Changes the parent of a task.  |
| [getAllStoriesOfTask](#retrieving-all-stories-of-a-task)    | Retrieves a compact representation of all stories of a particular task.  |
| [createCommentToTask](#adding-a-comment-to-a-task)      | Adds a comment to a task.   |
| [addTaskToProject](#adding-a-task-to-project)      | Adds a task to a specified project.  |
| [getProjectDetailsOfTask](#retrieving-project-details-of-a-task)      | Retrieve a compact representation of all the projects that a particular task belongs to. |
| [removeTaskFromProject](#removing-a-task-from-a-project)      | Removes an existing task from a specified project.  |
| [getTagsOfTask](#retrieving-tags-of-a-task)      | Retrieves a compact representation of all the tags that a task has. |
| [createTagToTask](#creating-a-tag-for-a-task)      | Adds a tag to a task.   |
| [removeTagFromTask](#removing-a-tag-from-a-task)    | Removes a tag from a task.  |
| [createFollowersToTask](#adding-followers-to-a-task)      | Adds the specified followers to a task.   |
| [removeFollowersFromTask](#removing-followers-from-a-task)      | Removes specified followers from a task. |

### Operation details

This section provides further details on the operations related to tasks.

#### Creating a new task

The createTask operation creates a new task in a specific workspace.

**createTask**
```xml
<asana.createTask>
    <assignee>{$ctx:assignee}</assignee>
    <notes>{$ctx:notes}</notes>
    <followers>{$ctx:followers}</followers>
    <name>{$ctx:name}</name>
    <workspace>{$ctx:workspace}</workspace>
</asana.createTask>
```

**Properties**
* assignee: The user to whom the task should be assigned. If you do not want to assign the task to a particular user, specify null.
* followers: An array of users who want to follow the task.
* notes: Detailed textual information associated with the task.
* workspace: The workspace that the task is associated with.
* name:The name of the task.

**Sample request**

Following is a sample request that can be handled by the createTask operation.

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
    "assignee":"me",
    "notes":"first task",
    "followers[0]":"kwwwa@gmail.com",
    "name":"first Task",
    "Workspace":"67377290416636"
}
```

**Sample response**

Given below is a sample response for the createTask operation.

```json
{
  "data": {
    "created_at": "2012-02-22T02:06:58.158Z",
    "name": "Hello, world!",
    "parent": null,
    "completed_at": null,
    "notes": "How are you today?",
    "modified_at": "2012-02-22T02:06:58.158Z",
    "assignee_status": "inbox",
    "assignee": {
      "id": 1235,
      "gid": "1235",
      "resource_type": "user",
      "name": "Tim Bizarro"
    },
    "completed": false,
    "followers": [
      {
        "id": 5678,
        "gid": "5678",
        "resource_type": "user",
        "name": "Greg Sanchez"
      }
    ],
    "workspace": {
      "id": 14916,
      "gid": "14916",
      "resource_type": "workspace",
      "name": "My Favorite Workspace"
    },
    "due_on": null,
    "id": 1001,
    "gid": "1001",
    "resource_type": "task",
    "projects": [
      {
        "id": 14641,
        "gid": "14641",
        "resource_type": "project",
        "name": "Cat Stuff"
      }
    ]
  }
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/tasks#create

#### Retrieving a task   

The getTask operation retrieves a task record based on the task ID that you specify.

**getTask**
```xml
<asana.getTask>
    <taskId>{$ctx:taskId}</taskId>
</asana.getTask>
```
**Properties**
* taskId: The unique ID of the task you want to retrieve. 

**Sample request**

Following is a sample request that can be handled by the getTask operation.

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

Given below is a sample response for the getTask operation.

```json
{
  "data": {
    "assignee": {
      "id": 1234,
      "gid": "1234",
      "resource_type": "user",
      "name": "Tim Bizarro"
    },
    "created_at": "2012-02-22T02:06:58.158Z",
    "...": "..."
  }
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/tasks#get

#### Updating a task

The updateTask operation updates the properties of an existing task.

**updateTask**
```xml
<asana.updateTask>
    <taskId>{$ctx:taskId}</taskId>                             
    <assignee>{$ctx:assignee}</assignee>
</asana.updateTask>
```

**Properties**
* taskId:The unique ID of the task you want to update.
* assignee: The user to whom the task is assigned.

**Sample request**

Following is a sample request that can be handled by the updateTask operation.

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
    "assignee":"dharshi@gmail.com" 
}
```

**Sample response**

Given below is a sample response for the updateTask operation.

```json
{
  "data": {
    "assignee": {
      "id": 1234,
      "gid": "1234",
      "resource_type": "user",
      "name": "Tim Bizarro"
    },
    "id": 1001,
    "gid": "1001",
    "resource_type": "task",
    "...": "..."
  }
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/tasks#update

#### Deleting a task

The deleteTask operation deletes an existing task.

**deleteTask**
```xml
<asana.deleteTask>
   <taskId>{$ctx:taskId}</taskId>
</asana.deleteTask>
```

**Properties**
* taskId: The unique ID of the task you want to delete. 
  
**Sample request**

Following is a sample request that can be handled by the deleteTask operation.

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
    "taskId":"80998315044519"
}
```

**Sample response**

Given below is a sample response for the deleteTask operation.

```json
{
  "data": {}
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/tasks#delete

#### Querying for tasks

The queryForTasks operation retrieves compact task records based on a set of specified filter criteria.

**queryForTasks**
```xml
<asana.queryForTasks>
    <workspace>{$ctx:workspace}</workspace>
    <assignee>{$ctx:assignee}</assignee>
    <completedSince>{$ctx:completedSince}</completedSince>
    <modifiedSince>{$ctx:modifiedSince}</modifiedSince>
</asana.queryForTasks>
```

**Properties**
* workspace:The ID of the workspace.
* assignee:The user to whom the task is assigned.
* completedSince: The date and time of completion of the task.
* modifiedSince:The date and time that the task was modified.

**Sample request**

Following is a sample request that can be handled by the queryForTasks operation.

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
    "assignee":"dharshi@gmail.com" 
}
```

**Sample response**

Given below is a sample response for the queryForTasks operation.

```json
{
  "data": [
    {
      "id": 1248,
      "gid": "1248",
      "resource_type": "task",
      "name": "Buy catnip"
    },
    {
      "id": 24816,
      "gid": "24816",
      "resource_type": "task",
      "name": "Reflect on role of kittens in society"
    },
  ]
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/tasks#query

#### Retrieving all subtasks

The getAllSubtasks operation retrieves a compact representation of all subtasks of a task.

**getAllSubtasks**
```xml
<asana.getAllSubtasks>
    <taskId>{$ctx:taskId}</taskId>
</asana.getAllSubtasks>
```

**Properties**
* taskId:The unique ID of the task for which you need to retrieve subtasks.

**Sample request**

Following is a sample request that can be handled by the getAllSubtasks operation.

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

Given below is a sample response for the getAllSubtasks operation.

```json
{
  "data": [
    {
      "id": 5005,
      "gid": "5005",
      "resource_type": "task",
      "name": "Steal Underwear"
    },
    {
      "id": 6709,
      "gid": "6709",
      "resource_type": "task",
      "name": "???"
    },
    {
      "id": 9812,
      "gid": "9812",
      "resource_type": "task",
      "name": "Profit"
    }
  ]
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/tasks#query

#### Creating a subtask

The createSubtask operation creates a new subtask and adds it to a parent task. 

**createSubtask**
```xml
<asana.createSubtask>
    <taskId>{$ctx:taskId}</taskId>
    <assignee>{$ctx:assignee}</assignee>
    <notes>{$ctx:notes}</notes>
    <name>{$ctx:name}</name>
</asana.createSubtask>
```

**Properties**
* taskId: The unique ID of the parent task for which you want to create a sub task.
* assignee: The user to whom the task is assigned.
* name:The name of the project.
* notes:Additional detailed textual information associated with the project.

**Sample request**

Following is a sample request that can be handled by the createSubtask operation.

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
    "taskId": "764125809931027",
    "notes": "create_a_task",
    "followers": [
      "me",
      "ray@gmail.com"
    ],
    "name": "rocktask",
    "assignee": "john@gmail.com"
}
```

**Sample response**

Given below is a sample response for the createSubtask operation.

```json
{
  "data": {
    "created_at": "2012-02-22T02:06:58.158Z",
    "name": "Tell Luke",
    "parent": {
      "id": 2272,
      "gid": "2272",
      "resource_type": "task",
      "name": "Tell kids I am their father."
    },
    "completed_at": null,
    "notes": "He's going to be upset.",
    "modified_at": "2012-02-22T02:06:58.158Z",
    "assignee_status": "inbox",
    "assignee": {
      "id": 1235,
      "gid": "1235",
      "resource_type": "user",
      "name": "Darth Vader"
    },
    "completed": false,
    "followers": [
      {
        "id": 5678,
        "gid": "5678",
        "resource_type": "user",
        "name": "Emperor Palpatine"
      }
    ],
    "workspace": {
      "id": 14916,
      "gid": "14916",
      "resource_type": "workspace",
      "name": "Star Wars"
    },
    "due_on": null,
    "id": 1001,
    "gid": "1001",
    "resource_type": "task",
    "projects": []
  }
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/tasks#subtasks

#### Changing the parent task of a subtask

The changeParentOfTask operation changes the parent of a task. Each task can only be a subtask of a single parent.

**changeParentOfTask**
```xml
<asana.changeParentOfTask>
    <taskId>{$ctx:taskId}</taskId>
    <parent>{$ctx:parent}</parent>
</asana.changeParentOfTask>
```

**Properties**
* taskId: The unique ID of the subtask.
* parent:The ID of the new parent task.

**Sample request**

Following is a sample request that can be handled by the changeParentOfTask operation.

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
    "taskId":"764125809931027",
    "Parent":"76410690056503"
}
```

**Sample response**

Given below is a sample response for the changeParentOfTask operation.

```json
{
  "data": {
    "...": "...",
    "id": 2272,
    "gid": "2272",
    "resource_type": "task",
    "parent": [
      {
        "id": 1331,
        "gid": "1331",
        "resource_type": "task",
        "name": "Tell kids I am their father"
      }
    ],
    "name": "Tell Luke"
  }
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/tasks#subtasks

#### Retrieving all stories of a task

The getAllStoriesOfTask operation retrieves a compact representation of all stories associated with a particular task.

**getAllStoriesOfTask**
```xml
<asana.getAllStoriesOfTask>
    <taskId>{$ctx:taskId}</taskId>
</asana.getAllStoriesOfTask>
```
**Properties**
* taskId : The unique ID of the task for which you need to retrieve associated stories.

**Sample request**

Following is a sample request that can be handled by the getAllStoriesOfTask operation.

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

Given below is a sample response for the getAllStoriesOfTask operation.

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

#### Adding a comment to a task

The createCommentToTask operation adds a new comment to a task.

**createCommentToTask**
```xml
<asana.createCommentToTask>
    <taskId>{$ctx:taskId}</taskId>
    <text>{$ctx:text}</text>
</asana.createCommentToTask>
```

**Properties**
* taskId:The unique ID of the task for which you need to add a comment.
* text:The content that you want to add as a comment in plain text format.

**Sample request**

Following is a sample request that can be handled by the createCommentToTask operation.

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
    "taskId":"7641250239931027",
    "text":"wow nice work"
}
```

**Sample response**

Given below is a sample response for the createCommentToTask operation.

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

#### Adding a task to project

The addTaskToProject operation adds a task to a specified section in a specific project. If a section is not specified, the task is added to the beginning of the project.

**addTaskToProject**
```xml
<asana.addTaskToProject>
    <taskId>{$ctx:taskId}</taskId>
    <project>{$ctx:project}</project>
    <insertAfter>{$ctx:insertAfter}</insertAfter>
    <insertBefore>{$ctx:insertBefore}</insertBefore>
    <section>{$ctx:section}</section>
</asana.addTaskToProject>
```

**Properties**
* taskId: The unique ID of the task you want to add to a project.
* section:The section in the project to add the task.
* insertBefore:An existing task in the project before which you want to insert the task that you add.
* insertAfter:An existing task in the project after which you want to insert the task that you add.
* project:The ID of the project to which you want to add the task.
  
**Sample request**

Following is a sample request that can be handled by the addTaskToProject operation.

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
    "taskId":"80998315044519" ,
    "insertAfter":"95136270017091",
    "section":"95127840098592"
}
```

**Sample response**

Given below is a sample response for the addTaskToProject operation.

```json
{
  "data": {}
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/tasks#projects

#### Retrieving project details of a task

The getProjectDetailsOfTask operation retrieves a compact representation of all projects that a particular task belongs to.

**getProjectDetailsOfTask**
```xml
<asana.getProjectDetailsOfTask>
    <taskId>{$ctx:taskId}</taskId>
</asana.getProjectDetailsOfTask>
```

**Properties**
* taskID: The unique ID of the task for which you want to retrieve associated project details

**Sample request**

Following is a sample request that can be handled by the getProjectDetailsOfTask operation.

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
    "taskId":"67377290416636"
}
```

**Sample response**

Given below is a sample response for the getProjectDetailsOfTask operation.

```json
{
  "data": [
    {
      "id": 1331,
      "gid": "1331",
      "resource_type": "project",
      "name": "Things To Buy"
    },
    {
      "id": 14641,
      "gid": "14641",
      "resource_type": "project",
      "name": "Cat Stuff"
    }
  ]
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/tasks#projects

#### Removing a task from a project

The removeTaskFromProject operation removes a specified task from a specific project.

**removeTaskFromProject**
```xml
<asana.removeTaskFromProject>
    <taskId>{$ctx:taskId}</taskId>
    <project>{$ctx:project}</project>
</asana.removeTaskFromProject>
```

**Properties**
* taskId:The unique ID of the task for which you  want to remove from the project.
* project: The ID of the project from which you want to remove the task.

**Sample request**

Following is a sample request that can be handled by the removeTaskFromProject operation.

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
    "taskId":"78999896872769",
    "project":"332222222"
}
```

**Sample response**

Given below is a sample response for the removeTaskFromProject operation.

```json
{
  "data": {}
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/tasks#projects

#### Retrieving tags of a task

The getTagsOfTask operation retrieves a compact representation of all tags related to a particular task.

**getTagsOfTask**
```xml
<asana.getTagsOfTask>
    <taskId>{$ctx:taskId}</taskId>
</asana.getTagsOfTask>
```

**Properties**
* taskId: The unique ID of the task for which you want retrieve related tags.


**Sample request**

Following is a sample request that can be handled by the getTagsOfTask operation.

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
    "taskId": "764125809931027"
}
```

**Sample response**

Given below is a sample response for the getTagsOfTask operation.

```json
{
  "data": [
    {
      "id": 1331,
      "gid": "1331",
      "resource_type": "tag",
      "name": "orange"
    },
    {
      "id": 1771,
      "gid": "1771",
      "resource_type": "tag",
      "name": "fluffy"
    }
  ]
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/tasks#tags

#### Creating a tag for a task

The createTagToTask operation creates a tag for a particular task.

**createTagToTask**
```xml
<asana.createTagToTask>
    <taskId>{$ctx:taskId}</taskId>
    <tag>{$ctx:tag}</tag>
</asana.createTagToTask>
```

**Properties**
* taskId:  The unique ID of the task for which you want to create a tag.
* tag:The tag to add to the task.

**Sample request**

Following is a sample request that can be handled by the createTagToTask operation.

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
    "taskId":"7641250239931027",
    "Tag":"85709047483371" 
}
```

**Sample response**

Given below is a sample response for the createTagToTask operation.

```json
{
  "data": {}
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/tasks#tags

#### Removing a tag from a task  

The removeTagFromTask operation removes a specified tag from a particular task.

**removeTagFromTask**
```xml
<asana.removeTagFromTask>
    <taskId>{$ctx:taskId}</taskId>
    <tag>{$ctx:tag}</tag>
</asana.removeTagFromTask>
```
**Properties**
* taskID: The unique ID of the task from which you want to remove the tag.
* tag: The tag that you want to remove from the task.

**Sample request**

Following is a sample request that can be handled by the removeTagFromTask operation.

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
    "taskId":"67377290416636",
    "Tag":"85709047483371" 
}
```

**Sample response**

Given below is a sample response for the removeTagFromTask operation.

```json
{
  "data": {}
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/tasks#tags

#### Adding followers to a task

The createFollowersToTask operation adds one or more followers to a particular task.

**createFollowersToTask**
```xml
<asana.createFollowersToTask>
    <taskId>{$ctx:taskId}</taskId>     
    <followers>{$ctx:followers}</followers>
</asana.createFollowersToTask>
```

**Properties**
* taskId: The unique ID of the task to which you want to add followers.
* followers: The followers you want to add to the task.

**Sample request**

Following is a sample request that can be handled by the createFollowersToTask operation.

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
    "taskId":"7641250239931027",
    "followers":["janan@gmail.com","nirthika@gmail.com"] 
}
```

**Sample response**

Given below is a sample response for the createFollowersToTask operation.

```json
{
  "data": {
    "followers": [
      {
        "id": 1235,
        "gid": "1235",
        "resource_type": "user",
        "name": "Darth Vader"
      }
    ],
    "id": 1001,
    "gid": "1001",
    "resource_type": "task",
    "...": "..."
  }
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/tasks#followers

#### Removing followers from a task

The removeFollowersFromTask operation removes one or more followers from a particular task.

**removeFollowersFromTask**
```xml
<asana.removeFollowersFromTask>
    <taskId>{$ctx:taskId}</taskId>
    <followers>{$ctx:followers}</followers>
</asana.removeFollowersFromTask>
```

**Properties**
* taskId: The unique ID of task from which you want to remove followers.
* followers: .The followers that you want to remove.
  
**Sample request**

Following is a sample request that can be handled by the removeFollowersFromTask operation.

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
    "taskId":"7641250239931027",
    "followers":["janan@gmail.com","nirthika@gmail.com"] 
}
```

**Sample response**

Given below is a sample response for the removeFollowersFromTask operation.

```json
{
  "data": {
    "followers": [],
    "id": 1001,
    "gid": "1001",
    "resource_type": "task",
    "...": "..."
  }
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/tasks#followers

### Sample configuration

Following example illustrates how to connect to Asana with the init operation and getTask operation.

1. Create a sample proxy as below :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<proxy xmlns="http://ws.apache.org/ns/synapse"
       name="getTask"
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
         <asana.getTask>
             <taskId>{$ctx:taskId}</taskId>
         </asana.getTask>
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
2. Create an json file named getTask.json and copy the configurations given below to it:

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

3. Replace the credentials with your values.

4. Execute the following curl command:

```bash
curl http://localhost:8280/services/getTask -H "Content-Type: application/json" -d @getTask.json
```
5. Asana returns an json response similar to the one shown below:
 
```json
{
  "data": {
    "assignee": {
      "id": 1234,
      "gid": "1234",
      "resource_type": "user",
      "name": "Tim Bizarro"
    },
    "created_at": "2012-02-22T02:06:58.158Z",
    "...": "..."
  }
}
```