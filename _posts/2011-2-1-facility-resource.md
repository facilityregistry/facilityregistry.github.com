---
category: 'Facilities'
title: 'Facility Object'
---

The API exposes a representation of the health facilities in JSON.

EXAMPLE HEALTH FACILITY RESPONSE

```{
    "facilities": [
        {
            "name": "Kakamega HC",
            "href": "http://facilityregistry.org/api/v1/facilities/53adf.json",
            "uuid": "550e8400-e29b-41d4-a716-446655440000",
            "active": true,
            "createdAt": "2011-11-16T14:26:15Z",
            "updatedAt": "2011-11-16T14:26:15Z",
            "coordinates": [
                -1.6917,
                29.525
            ],
            "identifiers": [
                {
                    "agency": "MOH",
                    "context": "DHIS",
                    "id": "123"
                },
                {
                    "agency": "UNICEF",
                    "context": "mtrac",
                    "id": "53adf"
                }
            ],
            "properties": {
                "numBeds": 55,
                "services": [
                    "XR",
                    "OBG",
                    "TR"
                ],
                "equipment": [
                    {
                        "id": 542,
                        "name": "Microscope"
                    },
                    {
                        "id": 942,
                        "name": "Vaccine Fridge"
                    }
                ],
                "manager": "Mrs. Liz",
                "hasMaternity": true,
                "medicalOfficer": "Dr.Mukombo"
            }
        }
    ]
}```

###Core Properties###

Each facility has the following core properties:

* `name` - Name of the facility.

`"name": "Kakamega HC"`

* `uuid` - globally unique [UUID per RFC 4122](http://en.wikipedia.org/wiki/Universally_unique_identifier). The UUID for a facility should remain constant and should never be changed. eg) the URL of the facility changes.

`"uuid": "50e8400-e29b-41d4-a716-446655440000"`

* `href` - URL link to the unique ID API resource for the facility.  The url of a facility MAY be structured around the uuid, a system-specific identifier or some other scheme. Clients of the facilities registry MUST use the provided url field and not attempt to calculate the URL themselves from other fields the facility has.

Using the same HREF should always return the same facility (if it still exists).

`"href": "http://facilityregistry.org/api/v1/facilities/53adf.json"`

FACILITY IDENTIFIERS

One of the primary functions of the facility registry is to facilitate a mapping of the different IDs used by different agencies to represent a particular facility.

Each external identifier consists of the following components:

agency: agency who created the code. ex) ministry of health, UNICEF, etc.
context: context/external system in which the agency is using the ID. eg) HMIS, DHIS2, HR
id: unique identifier

```"identifiers": [
      {"agency": "MOH", "context": "DHIS", "id": "123"},
      {"agency": "UNICEF", "context": "mtrac", "id": "53adf"},
      { .... }
]```

* `coordinates` - Geolocation represented by longitude and latitude coordinates in that order. All coordinates assume as WSG84 projection.

`"coordinates": [lng, lat]`

* `active` - indicates whether the facility is active or not.

`"active": {true/false}`

* `createdAt` - ISO 8601 timestamp of when the facility was created in the registry.

`"createdAt": "2011-11-16T14:26:15Z"`

* `updatedAt` - ISO 8601 timestamp of when the facility was last updated in the registry.

`"updatedAt": "2011-11-18T16:26:15Z"`

###Extended Properties###

Extended properties are implementation specific properties in the properties block.

The property types that are supported are:

* String – A series of textual characters
* Integer – A whole number
* Decimal
* Boolean – A true or false value
* Date: ISO 8601 format. eg) 2012-12-16T18:22:20Z
* Lists - A list of one of the following data types 
  * Simple data types such as the code mnemonic of selected value(s) (example: “apple”,”orange”)
  * Implementation specific complex data

SAMPLE PROPERTIES

```"properties": {
    "numBeds": 55,
    "services": ["XR","OBG","TR"],
    "equipment": [
        {
            "id": 542,
            "name": "Microscope"
        },
        {
            "id": 942,
            "name": "Vaccine Fridge"
        }
    ],
    "manager": "Mrs. Liz"
    "hasMaternity": true,
},```


Property field specification expectations

* For each property field, the implementer specifies a stable code that should not be changed once defined. The implementation should warn the user if they attempt to modify the code.
* The property field code should consist only of letters and numbers and not any special characters, spaces or punctuation to allow them to represent a good xml element. The API does not specify whether to define properties using camelCasing or lower_case, however, we encourage the implementation to be consistent in their formating.
* Each property field should be unique
* Specific properties for attachments and images are not supported in this version. It is possible to use a text string to represent a file path but that is implementation specific
