# Response & Error Code

### Response Status (HTTP Status)

Occasionally you might encounter errors when accessing the REST API. There are xxx possible types:


| Error Code | Error Description |
| ------ | ------ |
| **400 Bad Request** | Invalid request, e.g. using an unsupported HTTP method |
| **401 Unauthorized** | Authentication or permission error, e.g. incorrect API keys |
| **403 Forbidden** | Client error status response code indicates that the server understood the request but refuses to authorize it. |
| **404 Not Found** | Requests to resources that don't exist or are missing |
| **500 Internal Server Error** | Some server code error |

Errors return both an appropriate HTTP status code and response object which contains a `code`, `message` and `data` attribute.
