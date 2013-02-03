---
category: 'Facilities'
path: '/facilities.json'
title: 'Create a facility'
type: 'POST'

layout: nil
---

Create a new facility 

### Request

* The headers must include a **valid authentication token**.
* **The body can't be empty** and must include at least the `name` attribute that represents the name of the facility.

```Authentication: AUTHENTICATION TOKEN```
```{
    name: 'Kakamega HC'
}```

### Response

**If succeeds**, returns the created facility

`Status: 201 Created
Location: http: //facilityregistry.org/api/v1/facilities/0X9OCW3JMV98EYOVN32SGN4II.json`

**If duplicate is detected** a 409 is returned

`Status: 409 Conflict`

For errors responses, see the [response status codes documentation](#response-status-codes).