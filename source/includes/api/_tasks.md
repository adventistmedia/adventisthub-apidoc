# Task

A task to be completed by a user. A task can be specific to a contact.

## Fields

Field | Description | Notes
--------- | ------- | -------
title<br>*string* | Title | Required
description<br>*text* | Description
priority<br>*enum*{no_priority, low_priority, high_priority} | Priority of task. Defaults to no_priority
contact_id<br> *integer* | ID of the contact the task belongs too
user_id<br> *integer* | ID of the user the task belongs too | Read-only
due_date<br> *date* | Date the task is due to be completed
status<br>*enum*{active, completed} | Status of task. Defaults to active | Read-only
feedback<br>*text* | Feedback the user provides if a response is required
response_required<br>*boolean* | Whether the user is required to provide a response when completing the task | Read-only
completed_at<br>*datetime* | When the task was completed | Read-only
created_by_id<br> *integer* | ID of the user who created the task | Read-only
created_at<br>*datetime* | When the study was created | Read-only
updated_at<br>*datetime* | When the study was last updated | Read-only

## List Tasks
```shell
curl https://api.adventisthub.com/api/tasks
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1+json"
```

```json
{
  "data": [
    {
      "id": "9",
      "type": "tasks",
      "attributes": {
        "title": "Delivery Beyond the Search",
        "description": "After 3pm ideally",
        "priority": "no_priority",
        "contact_id": 24,
        "user_id": 5,
        "due_date": null,
        "status": "active",
        "feedback": null,
        "response_required": false,
        "completed_at": null,
        "created_by_id": 5,
        "created_at": "2016-11-22T12:39:34.272+11:00",
        "updated_at": "2016-11-29T11:33:31.565+11:00"
      }
    }
  ]
}
```

> Tasks filtered with parameters

```shell
curl -X GET http://api.crm.localhost:3000/api/tasks
-H "Authorization: Bearer cEQcQdo66DUTzdfzJJeJCvd6A2y8xMXqcMApSj99HjBB4rWVBm"
-H "Content-type: application/json"
-d '{"status": "archived", "contact_id":37}'
```
```json
{
  "data": [
    {
      "id": "11",
      "type": "tasks",
      "attributes": {
        "title": "Meet at the blue gum tree",
        "description": "",
        "priority": "no_priority",
        "contact_id": 37,
        "user_id": 5,
        "due_date": null,
        "status": "completed",
        "feedback": null,
        "response_required": false,
        "completed_at": "2017-01-03T08:12:04.577+11:00",
        "created_by_id": 5,
        "created_at": "2017-01-03T08:11:40.740+11:00",
        "updated_at": "2017-01-03T08:12:04.578+11:00"
      }
    }
  ]
}
```

`GET /api/tasks`

An array of tasks for the user.

### Parameters

Parameters can be added to filter tasks.

Parameter | Description | Options
--------- | ----------- | -------
status<br>*string* | Filter by the status of tasks | active, completed
contact_id<br>*integer* | Show tasks for a selected contact the user is assigned to | Any valid contact_id

## Show Task

```shell
curl https://api.adventisthub.com/api/tasks/9
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": {
    "id": "9",
    "type": "tasks",
    "attributes": {
      "title": "Delivery Beyond the Search",
      "description": "After 3pm ideally",
      "priority": "no_priority",
      "contact_id": 24,
      "user_id": 5,
      "due_date": null,
      "status": "active",
      "feedback": null,
      "response_required": false,
      "completed_at": null,
      "created_by_id": 5,
      "created_at": "2016-11-22T12:39:34.272+11:00",
      "updated_at": "2016-11-29T11:33:31.565+11:00"
    }
  }
}
```

`GET /api/tasks/{task-id}`

Show a task.

## Create Task
```shell
curl -X POST https://api.adventisthub.com/api/tasks
-H "Authorization: Bearer token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adventisthub.v1+json"
-d '{"task": {"title": "Send Sally flowers", "contact_id": 46, "due_date": "2018-01-16"}}'
```
```json
{
  "data": {
    "id": "12",
    "type": "tasks",
    "attributes": {
      "title": "Send Sally flowers",
      "description": null,
      "priority": "no_priority",
      "contact_id": 46,
      "user_id": 5,
      "due_date": "2018-01-16",
      "status": "active",
      "feedback": null,
      "response_required": false,
      "completed_at": null,
      "created_by_id": null,
      "created_at": "2017-01-17T12:45:07.718+11:00",
      "updated_at": "2017-01-17T12:45:07.718+11:00"
    }
  }
}
```

`POST /api/tasks`

## Update Task
```shell
curl -X PATCH https://api.adventisthub.com/api/tasks/12
-H "Authorization: Bearer token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adventisthub.v1+json"
-d '{"task": {"due_date": ""}}'
```
```json
{
  "data": {
    "id": "12",
    "type": "tasks",
    "attributes": {
      "title": "Send Sally flowers",
      "description": null,
      "priority": "no_priority",
      "contact_id": 46,
      "user_id": 5,
      "due_date": null,
      "status": "active",
      "feedback": null,
      "response_required": false,
      "completed_at": null,
      "created_by_id": null,
      "created_at": "2017-01-17T12:45:07.718+11:00",
      "updated_at": "2017-01-17T12:50:40.481+11:00"
    }
  }
}
```

`PATCH /api/tasks/{task-id}`

Only tasks created by the user can be updated.

## Delete Task
```shell
curl -X DELETE https://api.adventisthub.com/api/tasks/2
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": {
    "id": "12",
    "type": "tasks",
    "attributes": {
      "title": "Send Sally flowers",
      "description": null,
      "priority": "no_priority",
      "contact_id": 46,
      "user_id": 5,
      "due_date": null,
      "status": "active",
      "feedback": null,
      "response_required": false,
      "completed_at": null,
      "created_by_id": null,
      "created_at": "2017-01-17T12:45:07.718+11:00",
      "updated_at": "2017-01-17T12:50:40.481+11:00"
    }
  }
}
```

`DELETE /api/tasks/{task-id}`

Only tasks created by the user can be deleted.

## Completed Task
```shell
curl -X PATCH https://api.adventisthub.com/api/tasks/12/completed
-H "Authorization: Bearer token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adventisthub.v1+json"
-d '{"task": {"completed_at": "2017-01-17T13:00"}}'
```
```json
{
  "data": {
    "id": "13",
    "type": "tasks",
    "attributes": {
      "title": "Send Sally flowers",
      "description": null,
      "priority": "no_priority",
      "contact_id": null,
      "user_id": 5,
      "due_date": "2018-01-16",
      "status": "completed",
      "feedback": null,
      "response_required": false,
      "completed_at": "2017-01-17T13:00:00.000+11:00",
      "created_by_id": null,
      "created_at": "2017-01-17T12:57:54.488+11:00",
      "updated_at": "2017-01-17T13:04:29.271+11:00"
    }
  }
}
```

`PATCH /api/tasks/{task-id}/completed`

Complete a task.
If the task has response_required set to true feedback is required.

## Uncompleted Task
```shell
curl -X PATCH https://api.adventisthub.com/api/tasks/12/uncomplete
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": {
    "id": "13",
    "type": "tasks",
    "attributes": {
      "title": "Send Sally flowers",
      "description": null,
      "priority": "no_priority",
      "contact_id": null,
      "user_id": 5,
      "due_date": "2018-01-16",
      "status": "active",
      "feedback": null,
      "response_required": false,
      "completed_at": null,
      "created_by_id": null,
      "created_at": "2017-01-17T12:57:54.488+11:00",
      "updated_at": "2017-01-17T14:23:31.105+11:00"
    }
  }
}
```

`PATCH /api/tasks/{task-id}/uncomplete`

Uncomplete a task.