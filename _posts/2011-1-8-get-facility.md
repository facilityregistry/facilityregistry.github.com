---
category: Facilities
path: '/facilities/{id}.json'
title: 'Get a facility'
type: 'GET'

layout: nil
---

Get an individual facility for a particular id.

### Request

* The headers must include a **valid authentication token**.

### Response

```Status: 200 OK```

Returns the [facility object](#facility-resource)

`Status: 404 Not Found`

Facility resource not found or unavailable

For errors responses, see the [response status codes documentation](#response-status-codes).