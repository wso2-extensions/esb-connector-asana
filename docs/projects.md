# Working with Projects in Asana

[[Overview]](#overview)  [[Operation details]](#operation-details)  [[Sample configuration]](#sample-configuration)

### Overview 

The following operations allow you to work with projects. Click an operation name to see details on how to use it.
For a sample proxy service that illustrates how to work with projects, see [Sample configuration](#sample-configuration).

| Operation        | Description |
| ------------- |-------------|
| [createProject](#creating-a-project)    | Creates a new project in a workspace or team.   |
| [deleteProject](#deleting-a-project)      | Deletes an existing project.   |
| [getProjectSections](#retrieving-project-sections)      | Retrieves all sections of a specified project.  |
| [getProjectTasks](#retrieving-project-tasks)      | Retrieves all task records of a specific project, ordered by the priority of the task in the project.  |
| [getSingleProject](#retrieving-a-single-project)      | Retrieves the complete project record of a specific project.  |
| [updateProject](#updating-a-project )      | Updates an existing project.  |
| [queryForProjects](#querying-for-projects)      | Retrieves project records of specified projects.   |

### Operation details

This section provides further details on the operations related to projects.

#### Creating a project 

The createProject operation creates a new project in a workspace or team. 

**createProject**
```xml
<asana.createProject>
    <workspace>{$ctx:workspace}</workspace>
    <name>{$ctx:name}</name>
    <notes>{$ctx:notes}</notes>
</asana.createProject>
```

**Properties**
* workspace: The ID of the workspace.
* name: The name of the project.
* notes: Additional information associated with the project. 

**Sample request**

Following is a sample request that can be handled by the createProject operation.

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
    "workspace":"65796816841176",
    "name":"Things to see",
    "notes":"These are things we want to see."
}
```

**Sample response**

Given below is a sample response for the createProject operation.

```json
{
   "data":{
      "gid":"826151180792726",
      "id":826151180792726,
      "created_at":"2018-09-18T08:20:31.929Z",
      "modified_at":"2018-09-18T08:20:31.929Z",
      "owner":{
         "gid":"823742841047779",
         "id":823742841047779,
         "name":"john"
      },
      "due_date":null,
      "current_status":null,
      "public":true,
      "name":"",
      "notes":"",
      "archived":false,
      "workspace":{
         "gid":"823749000161232",
         "id":823749000161232,
         "name":"University Of Jaffna"
      },
      "start_on":null,
      "color":null,
      "members":[
         {
            "gid":"823742841047779",
            "id":823742841047779,
            "name":"john"
         }
      ],
      "followers":[
         {
            "gid":"823742841047779",
            "id":823742841047779,
            "name":"john"
         }
      ]
   }
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/projects#create

#### Deleting a project

The deleteProject operation deletes an an existing project based on the specified project ID.

**deleteProject**
```xml
<asana.deleteProject>
    <projectId>{$ctx:projectId}</projectId>
</asana.deleteProject>
```
**Properties**
* projectId: The unique ID of the project that you want to delete. 

**Sample request**

Following is a sample request that can be handled by the deleteProject operation.

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
    "projectId":"80998315044519"
}
```

**Sample response**

Given below is a sample response for the deleteProject operation.

```json
{
   "data":{
   }
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/projects#delete

#### Retrieving project sections

The getProjectSections operation retrieves records from all sections of a specified project.

**getProjectSections**
```xml
<asana.getProjectSections>
    <projectId>{$ctx:projectId}</projectId>
</asana.getProjectSections>
```

**Properties**
* projectId: The unique ID of the project to retrieve sections.

**Sample request**

Following is a sample request that can be handled by the getProjectSections operation.

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
    "projectId":"80998315044485"
}
```

**Sample response**

Given below is a sample response for the getProjectSections operation.

```json
{
  "data": [
    {
      "id": 2001,
      "gid": "2001",
      "resource_type": "section",
      "name": "High Priority:"
    },
    {
      "id": 2002,
      "gid": "2002",
      "resource_type": "section",
      "name": "Low Priority:"
    },
    "~..."
  ]
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/sections#find-project

#### Retrieving project tasks

The getProjectTasks operation retrieves all task records of a specific project, ordered by the priority of tasks in the project.

**getProjectTasks**
```xml
<asana.getProjectTasks>
    <projectId>{$ctx:projectId}</projectId>
</asana.getProjectTasks>
```

**Properties**
* projectId: The unique ID of the project to retrieve tasks. 

**Sample request**

Following is a sample request that can be handled by the getProjectTasks operation.

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
    "projectId":"80998315044519"
}
```

**Sample response**

Given below is a sample response for the getProjectTasks operation.

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
https://asana.com/developers/api-reference/projects#get-tasks

#### Retrieving a single project

The getSingleProject operation retrieves a complete project record based on the specified project ID. 

**getSingleProject**
```xml
<asana.getSingleProject>
    <projectId>{$ctx:projectId}</projectId>
</asana.getSingleProject> 
```

**Properties**
* projectId: The unique ID of the project.

**Sample request**

Following is a sample request that can be handled by the getSingleProject operation.

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
    "projectId":"80998315044485"
}
```

**Sample response**

Given below is a sample response for the getSingleProject operation.

```json
{
  "data": {
    "notes": "These are things we want to purchase.",
    "null": "...",
    "id": 1331,
    "gid": "1331",
    "resource_type": "project",
    "name": "Things to Buy"
  }
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/projects#get-single

#### Updating a project

The updateProject operation updates an existing project based on the specified details.

**updateProject**
```xml
<asana.updateProject>
    <projectId>{$ctx:projectId}</projectId>
    <name>{$ctx:name}</name>
    <notes>{$ctx:notes}</notes>
</asana.updateProject>
```

**Properties**
* projectId: The unique ID of the project to update.
* name: The name of the project.
* notes: Additional information related to the project.

**Sample request**

Following is a sample request that can be handled by the updateProject operation.

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
    "projectId":"80998315044485",
    "name":"project1",
    "notes":"Testing note1."
}
```

**Sample response**

Given below is a sample response for the updateProject operation.

```json
{
  "data": {
    "notes": "These are things we NEED to purchase.",
    "null": "...",
    "id": 1331,
    "gid": "1331",
    "resource_type": "project",
    "name": "Things to Buy"
  }
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/projects#update

#### Querying for projects

The queryForProjects operation retrieves project records based on the specified project criteria.

**queryForProjects**
```xml
<asana.queryForProjects>
    <workspace>{$ctx:workspace}</workspace>
</asana.queryForProjects> 
```

**Properties**
* workspace:The ID of the workspace.

**Sample request**

Following is a sample request that can be handled by the queryForProjects operation.

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

Given below is a sample response for the queryForProjects operation.

```json
{
  "data": {
    "notes": "These are things we want to purchase.",
    "null": "...",
    "id": 1331,
    "gid": "1331",
    "resource_type": "project",
    "name": "Things to Buy"
  }
}
```
**Related Asana documentation**
https://asana.com/developers/api-reference/projects#query

### Sample configuration

Following example illustrates how to connect to Asana with the init operation and deleteProject operation.

1. Create a sample proxy as below :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<proxy xmlns="http://ws.apache.org/ns/synapse"
       name="deleteProject"
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
         <property expression="json-eval($.projectId)" name="projectId"/>
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
      <asana.deleteProject>
        <projectId>{$ctx:projectId}</projectId>
    </asana.deleteProject>
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
2. Create an json file named deleteProject.json and copy the configurations given below to it:

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
    "projectId":"80998315044519"
}
```

3. Replace the credentials with your values.

4. Execute the following curl command:

```bash
curl http://localhost:8280/services/deleteProject -H "Content-Type: application/json" -d @deleteProject.json
```
5. Asana returns an json response similar to the one shown below:
 
```json
{
   "data":{
   }
}
```