---
category: Facilities
path: '/facilities/{id}.json'
title: 'Delete a facility'
type: 'DELETE'

layout: nil
---
Delete a facility

### Request

* **`{id}`** of the facility to delete.
* **The body is omitted**.

### Response

If the facility resource is found and deleted

`Status: 200 OK`

```{
    code: 200,
    id: '0X9OCW3JMV98EYOVN32SGN4II'
    message: 'Resource deleted'
}```

If facility resource for id is not found

```Status: 404 Not Found```
```{
    code: 404 Not Found,
    message: 'Resource not found'
}```

Note: The facility registry SHALL delete the facility resource such that the record is no longer discoverable to consumers. The process by which the facility registry marks the facility as deleted is not specified in this document, and is left to implementers to determine the most appropriate method.

For errors responses, see the [response status codes documentation](#http-response-codes).