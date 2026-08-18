# Projects API

The Projects API provides endpoints for creating, retrieving, and updating projects in TaskHub.

## Get All Projects

Retrieves a list of projects available to the authenticated user.

### Endpoint

```http
GET /projects
```

### Example Request

```bash
curl -X GET "https://api.taskhub.example.com/api/v1/projects" \
  -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
```

### Example Response

```json
{
  "data": [
    {
      "id": 201,
      "name": "Website Redesign",
      "description": "Redesign the company website.",
      "status": "active"
    }
  ]
}
```

### Response Fields

| Field       | Type    | Description                       |
| ----------- | ------- | --------------------------------- |
| id          | integer | Unique identifier of the project. |
| name        | string  | Name of the project.              |
| description | string  | Description of the project.       |
| status      | string  | Current project status.           |

### Possible Responses

| Status Code | Description                           |
| ----------- | ------------------------------------- |
| 200         | Projects retrieved successfully.      |
| 401         | Authentication is missing or invalid. |

---

## Get a Project

Retrieves a specific project by its ID.

### Endpoint

```http
GET /projects/{project_id}
```

### Path Parameters

| Parameter  | Type    | Required | Description                       |
| ---------- | ------- | -------- | --------------------------------- |
| project_id | integer | Yes      | Unique identifier of the project. |

### Example Request

```http
GET /projects/201
```

### Example Response

```json
{
  "id": 201,
  "name": "Website Redesign",
  "description": "Redesign the company website.",
  "status": "active"
}
```

### Possible Responses

| Status Code | Description                           |
| ----------- | ------------------------------------- |
| 200         | Project retrieved successfully.       |
| 401         | Authentication is missing or invalid. |
| 404         | Project was not found.                |

---

## Create a Project

Creates a new project.

### Endpoint

```http
POST /projects
```

### Request Body

```json
{
  "name": "Mobile App Development",
  "description": "Development of a mobile application.",
  "status": "active"
}
```

### Request Fields

| Field       | Type   | Required | Description                    |
| ----------- | ------ | -------- | ------------------------------ |
| name        | string | Yes      | Name of the project.           |
| description | string | Yes      | Description of the project.    |
| status      | string | No       | Initial status of the project. |

### Example Request

```bash
curl -X POST "https://api.taskhub.example.com/api/v1/projects" \
  -H "Authorization: Bearer YOUR_ACCESS_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Mobile App Development",
    "description": "Development of a mobile application.",
    "status": "active"
  }'
```

### Example Response

```http
HTTP/1.1 201 Created
```

```json
{
  "id": 202,
  "name": "Mobile App Development",
  "description": "Development of a mobile application.",
  "status": "active"
}
```

### Possible Responses

| Status Code | Description                           |
| ----------- | ------------------------------------- |
| 201         | Project created successfully.         |
| 400         | Invalid request data.                 |
| 401         | Authentication is missing or invalid. |

---

## Update a Project

Updates an existing project.

### Endpoint

```http
PUT /projects/{project_id}
```

### Path Parameters

| Parameter  | Type    | Required | Description                       |
| ---------- | ------- | -------- | --------------------------------- |
| project_id | integer | Yes      | Unique identifier of the project. |

### Request Body

```json
{
  "name": "Website Redesign — Phase 2",
  "description": "Updated project description.",
  "status": "active"
}
```

### Example Request

```http
PUT /projects/201
Content-Type: application/json
Authorization: Bearer YOUR_ACCESS_TOKEN
```

### Example Response

```json
{
  "id": 201,
  "name": "Website Redesign — Phase 2",
  "description": "Updated project description.",
  "status": "active"
}
```

### Possible Responses

| Status Code | Description                           |
| ----------- | ------------------------------------- |
| 200         | Project updated successfully.         |
| 400         | Invalid request data.                 |
| 401         | Authentication is missing or invalid. |
| 404         | Project was not found.                |
