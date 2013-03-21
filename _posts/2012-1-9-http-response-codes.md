---
title: 'HTTP Response Codes'

layout: nil
---

### HTTP Status Codes

* `200 OK` - All Indicates that the specified action was successfully completed. A 200 response indicates that the registry did successfully perform the operation and the response contains the final result of the action.
* `201 Created` - Indicates that a request was successful and as a result, a resource has been created
* `400 Bad Request` - Indicates that the requested operation is not valid.
* `401 Unauthorized` - Raised when the client attempts to perform an operation against a resource which requires authorization. This error code indicates a challenge for client credentials.
* `403 Forbidden` - Indicates that the client does not have the necessary permission to perform the specified operation against the requested resource.
* `404 Not Found` - Indicates that a resource was not found or is not available.
* `405 Not Allowed` - Indicates that the requested operation is not allowed on the current resource (for example: DELETE on a collection)
* `409 Conflict` - Indicates that the facility registry has detected a conflict in the operation and has refused to perform the operation.
* `410 Gone` - Indicates that a resource did exist but has been permanently removed.
* `500 Internal Server Error` - Indicates that the server encountered an error while attempting to execute the desired action.

### Success

Success differ from errors in that their body may not be a simple response object with a code and a message. The headers however are consistent across all calls:

* `GET`, `PUT`, `DELETE` returns `200 OK` on success,
* `POST ` returns `201 Created` on success,

### Error

Error responses are simply returning [standard HTTP error codes](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) along with some additional information:

* The error code is sent back as a status header,
* The body includes an object describing both the code and OPTIONALLY the message

For example, for a call with when the resource is not found:

```Status: 404 Not Found```
```{
    code: 404 Not Found,
    message: 'Resource not found'
}```
