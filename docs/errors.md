# Error Handling

TaskHub uses standard HTTP status codes to indicate whether an API request was successful or resulted in an error.

## Common Error Codes

| Status Code | Meaning               | Description                                |
| ----------- | --------------------- | ------------------------------------------ |
| 400         | Bad Request           | The request contains invalid data.         |
| 401         | Unauthorized          | Authentication is missing or invalid.      |
| 403         | Forbidden             | The user does not have permission.         |
| 404         | Not Found             | The requested resource does not exist.     |
| 405         | Method Not Allowed    | The HTTP method is not supported.          |
| 429         | Too Many Requests     | The client has exceeded the request limit. |
| 500         | Internal Server Error | An unexpected server error occurred.       |
| 503         | Service Unavailable   | The service is temporarily unavailable.    |

## Error Response Format

TaskHub returns errors in JSON format.

Example:

```json
{
  "error": {
    "code": "PROJECT_NOT_FOUND",
    "message": "The requested project could not be found."
  }
}
```

### Error Fields

| Field   | Type   | Description                              |
| ------- | ------ | ---------------------------------------- |
| code    | string | Machine-readable error identifier.       |
| message | string | Human-readable explanation of the error. |

## Example

If a client requests a project that does not exist:

```http
GET /projects/999
```

The API may return:

```http
HTTP/1.1 404 Not Found
```

```json
{
  "error": {
    "code": "PROJECT_NOT_FOUND",
    "message": "The requested project could not be found."
  }
}
```

## Troubleshooting

When an API request fails:

1. Check the HTTP status code.
2. Verify the request URL.
3. Confirm that the HTTP method is correct.
4. Check required parameters.
5. Verify authentication credentials.
6. Review the response body for additional error information.
