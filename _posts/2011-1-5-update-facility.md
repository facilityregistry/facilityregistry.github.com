---
category: 'Facilities'
path: '/facilities/{id}.json'
title: 'Update a facility'
type: 'PUT'

layout: nil
---

Update the facility, replacing the facility properties with the new resource representation passed in the request.

### Request

* The headers must include a **valid authentication token**.
* Full new resource representation of the facility (not a partial update)
* **The body can't be empty** and must include at least the name attribute, a `string` that will be used as the name of the facility.

```Authentication: AUTHENTICATION TOKEN```
```{
    name: 'Kakamega HCII'
}```

### Response

**If succeeds**, returns the location of the updated facility.

`Status: 200 OK
Location: http: //facilityregistry.org/api/v1/facilities/0X9OCW3JMV98EYOVN32SGN4II.json`

If the the facility resource is not found to update

`Status: 404 Not Found`

For errors responses, see the [response status codes documentation](#response-status-codes).

Question - Can the id be changed in a PUT?