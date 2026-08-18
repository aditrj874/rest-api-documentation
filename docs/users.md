# Users API

The Users API provides endpoints for retrieving user information.

## Get All Users

Retrieves a list of users.

### Endpoint

```http
GET /users
```

### Example Request

```bash
curl -X GET "https://api.taskhub.example.com/api/v1/users" \
  -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
```

### Example Response

```json
{
  "data": [
    {
      "id": 101,
      "name": "Aditya Raj",
      "email": "aditya@example.com",
      "role": "member"
    },
    {
      "id": 102,
      "name": "Peter Sharma",
      "email": "peter@example.com",
      "role": "manager"
    }
  ]
}
```

### Response Fields

| Field | Type    | Description                     |
| ----- | ------- | ------------------------------- |
| id    | integer | Unique identifier for the user. |
| name  | string  | User's display name.            |
| email | string  | User's email address.           |
| role  | string  | User's assigned role.           |

### Possible Responses

| Status Code | Description                                            |
| ----------- | ------------------------------------------------------ |
| 200         | Users retrieved successfully.                          |
| 401         | Authentication is missing or invalid.                  |
| 403         | User does not have permission to access this resource. |

---

## Get a User

Retrieves information about a specific user.

### Endpoint

```http
GET /users/{user_id}
```

### Path Parameters

| Parameter | Type    | Required | Description                    |
| --------- | ------- | -------- | ------------------------------ |
| user_id   | integer | Yes      | Unique identifier of the user. |

### Example

```http
GET /users/101
```

### Example Response

```json
{
  "id": 101,
  "name": "Aditya Raj",
  "email": "aditya@example.com",
  "role": "member"
}
```

### Possible Responses

| Status Code | Description                           |
| ----------- | ------------------------------------- |
| 200         | User retrieved successfully.          |
| 401         | Authentication is missing or invalid. |
| 404         | User was not found.                   |
