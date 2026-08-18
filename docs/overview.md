# TaskHub REST API

## Overview

TaskHub is a fictional REST API for managing users, projects, and tasks within a project management system.

The API follows REST principles and uses HTTP methods to perform operations on resources.

## Base URL

All API requests use the following base URL:

```text
https://api.taskhub.example.com/api/v1
```

> **Note:** TaskHub is a documentation portfolio project. The API described here is fictional and is not connected to a live backend.

## API Resources

TaskHub provides three primary resources:

| Resource | Description                              |
| -------- | ---------------------------------------- |
| Users    | Manage user information and accounts.    |
| Projects | Create and manage projects.              |
| Tasks    | Create, update, assign, and track tasks. |

## HTTP Methods

TaskHub uses standard HTTP methods to perform operations on resources.

| Method | Purpose                     |
| ------ | --------------------------- |
| GET    | Retrieve information        |
| POST   | Create a new resource       |
| PUT    | Update an existing resource |
| DELETE | Delete a resource           |

## Example Endpoint

To retrieve a list of tasks:

```http
GET /api/v1/tasks
```

A complete request would be:

```http
GET https://api.taskhub.example.com/api/v1/tasks
```

## Example Response

A successful request may return:

```json
{
  "data": [
    {
      "id": 101,
      "title": "Write API documentation",
      "status": "in-progress",
      "priority": "high"
    }
  ]
}
```

## Response Format

TaskHub uses JSON for API responses.

A typical response contains a `data` object or array containing the requested resource.

## Authentication

Most TaskHub endpoints require authentication.

Clients must provide a valid authentication token in the request header:

```http
Authorization: Bearer YOUR_ACCESS_TOKEN
```

Authentication details are covered in the [Authentication Guide](authentication.md).

## API Versioning

The current API version is **v1**.

The version is included in the URL:

```text
/api/v1/
```

Versioning helps maintain compatibility when changes are introduced in future API releases.

## Related Documentation

* [Authentication](authentication.md)
* [Users](users.md)
* [Projects](projects.md)
* [Tasks](tasks.md)
* [Error Handling](errors.md)
* [Quick Start](quick-start.md)

