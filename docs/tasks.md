# Tasks API

The Tasks API provides endpoints for creating, retrieving, updating, and deleting tasks.

## Get All Tasks

Retrieves tasks available to the authenticated user.

### Endpoint

```http
GET /tasks
```

### Query Parameters

| Parameter  | Type    | Required | Description                           |
| ---------- | ------- | -------- | ------------------------------------- |
| status     | string  | No       | Filters tasks by status.              |
| priority   | string  | No       | Filters tasks by priority.            |
| project_id | integer | No       | Filters tasks belonging to a project. |

### Example Request

```http
GET /tasks?status=in-progress&priority=high
```

### Example Response

```json
{
  "data": [
    {
      "id": 101,
      "title": "Write API documentation",
      "status": "in-progress",
      "priority": "high",
      "project_id": 201
    }
  ]
}
```

### Possible Responses

| Status Code | Description                           |
| ----------- | ------------------------------------- |
| 200         | Tasks retrieved successfully.         |
| 401         | Authentication is missing or invalid. |

---

## Get a Task

Retrieves a specific task.

### Endpoint

```http
GET /tasks/{task_id}
```

### Path Parameters

| Parameter | Type    | Required | Description                    |
| --------- | ------- | -------- | ------------------------------ |
| task_id   | integer | Yes      | Unique identifier of the task. |

### Example Request

```http
GET /tasks/101
```

### Example Response

```json
{
  "id": 101,
  "title": "Write API documentation",
  "description": "Document the TaskHub REST API.",
  "status": "in-progress",
  "priority": "high",
  "project_id": 201
}
```

---

## Create a Task

Creates a new task.

### Endpoint

```http
POST /tasks
```

### Request Body

```json
{
  "title": "Create user documentation",
  "description": "Write the user documentation for TaskHub.",
  "priority": "medium",
  "project_id": 201
}
```

### Request Fields

| Field       | Type    | Required | Description                       |
| ----------- | ------- | -------- | --------------------------------- |
| title       | string  | Yes      | Title of the task.                |
| description | string  | Yes      | Description of the task.          |
| priority    | string  | No       | Priority assigned to the task.    |
| project_id  | integer | Yes      | Project associated with the task. |

### Example Response

```http
HTTP/1.1 201 Created
```

```json
{
  "id": 102,
  "title": "Create user documentation",
  "description": "Write the user documentation for TaskHub.",
  "priority": "medium",
  "project_id": 201,
  "status": "pending"
}
```

---

## Update a Task

Updates an existing task.

### Endpoint

```http
PUT /tasks/{task_id}
```

### Example Request

```http
PUT /tasks/101
Content-Type: application/json
Authorization: Bearer YOUR_ACCESS_TOKEN
```

Request body:

```json
{
  "status": "completed",
  "priority": "high"
}
```

### Example Response

```json
{
  "id": 101,
  "title": "Write API documentation",
  "status": "completed",
  "priority": "high"
}
```

---

## Delete a Task

Deletes a task.

### Endpoint

```http
DELETE /tasks/{task_id}
```

### Example Request

```http
DELETE /tasks/101
```

### Successful Response

```http
HTTP/1.1 204 No Content
```

A `204` response indicates that the task was successfully deleted and the server does not return a response body.

### Possible Responses

| Status Code | Description                           |
| ----------- | ------------------------------------- |
| 204         | Task deleted successfully.            |
| 401         | Authentication is missing or invalid. |
| 404         | Task was not found.                   |
