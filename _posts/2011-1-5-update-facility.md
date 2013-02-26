---
category: 'Facilities'
path: '/facilities/{id}.json'
title: 'Update a facility'
type: 'PUT'

layout: nil
---

Update the facility, replacing the facility properties with the new resource representation passed in the request.

### Request

* Full new resource representation of the facility (not a partial update)
* **The body can't be empty** and must include at least the name attribute, a `string` that will be used as the name of the facility.
* The `id`, `url`, `createdAt`, and `updatedAt` core properties cannot be changed by the client.  An update request including any of these properties or any unknown core properties should result in a `400 Bad Request` error.

```{
    name: 'Kakamega HCII'
}```

### Response

Returns the location of the updated facility.

`Status: 200 OK
Location: http: //facilityregistry.org/api/v1/facilities/0X9OCW3JMV98EYOVN32SGN4II.json`

`{
   "facility": {
   "name": "Kakamega HC",
   ...
}`

Returns the [facility object](#facility-resource) of the updated facility.

*Not Found*

If the the facility resource is not found to update

```Status: 404 Not Found```
```{
    code: 404 Not Found,
    message: 'Resource not found'
}```

For errors responses, see the [response status codes documentation](#response-status-codes).
