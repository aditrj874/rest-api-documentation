# Authentication
TaskHub API uses **Bearer Token authentication** to protect authenticated endpoints.

Clients must include a valid access token in the `Authorization` header when making authenticated requests.

## Authorization Header
Use the following format:

```http
Authorization: Bearer YOUR_ACCESS_TOKEN
```

Replace `YOUR_ACCESS_TOKEN` with the token provided by the authentication service.

## Example Request

```http
GET /api/v1/tasks
Host: api.taskhub.example.com
Authorization: Bearer YOUR_ACCESS_TOKEN
```

## Authentication Errors

If authentication information is missing or invalid, the API may return an error response.

| Status Code | Meaning                                                                         |
| ----------- | ------------------------------------------------------------------------------- |
| 401         | Authentication is missing or invalid                                            |
| 403         | The authenticated user does not have permission to perform the requested action |

## Security Recommendations

* Do not share access tokens with other users.
* Do not commit real access tokens to source-control repositories.
* Store credentials securely.
* Use HTTPS when sending authentication information.

> **Note:** The tokens used in this documentation are examples only. TaskHub is a fictional API and does not issue real authentication tokens.
