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
            "url": "http: //facilityregistry.org/api/v1/facilities/0X9OCW3JMV98EYOVN32SGN4II.json",
            "id": "0X9OCW3JMV98EYOVN32SGN4II",
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

* `id` - The internal system unique identifier. The id must be universally unique within the FRED registry.

`"id": '0X9OCW3JMV98EYOVN32SGN4II'`

Note: the API does not providing a specific format for IDs. That is left up to the implementation.

* `url` - URL link to the unique ID API resource for the facility

`"url": "http://facilityregistry.org/api/v1/facilities/0X9OCW3JMV98EYOVN32SGN4II.json"`

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
* The property field code should consist only of letters and number and not any special characters, spaces or punctuation to allow them to represent a good xml element. The API does not specify whether to define properties using camelCasing or lower_case, however, we encourage the implementation to be consistent in their formating.
* Each property field should be unique
* Specific properties for attachments and images are not supported in this version. It is possible to use a text string to represent a file path but that is implementation specific
