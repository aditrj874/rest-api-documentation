# Quick Start

This guide shows how to make your first request to the TaskHub API.

> **Note:** TaskHub is a fictional API created as a technical documentation portfolio project. The examples are for documentation purposes and do not connect to a live service.

## Prerequisites

Before using the API, you should have:

* Basic knowledge of HTTP requests.
* An API client such as Postman or cURL.
* A valid access token for authenticated requests.

## Step 1: Set the Base URL

Use the following base URL:

```text
https://api.taskhub.example.com/api/v1
```

## Step 2: Add Authentication

Include your access token in the request header:

```http
Authorization: Bearer YOUR_ACCESS_TOKEN
```

## Step 3: Make Your First Request

Retrieve the available tasks:

```bash
curl -X GET "https://api.taskhub.example.com/api/v1/tasks" \
  -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
```

## Step 4: Review the Response

A successful request returns a `200 OK` response.

Example:

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

## What's Next?

After making your first request, explore:

* [Authentication](authentication.md)
* [Users](users.md)
* [Projects](projects.md)
* [Tasks](tasks.md)
* [Error Handling](errors.md)
