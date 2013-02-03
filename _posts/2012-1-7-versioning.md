---
title: 'Versioning'

layout: nil
---
API Documentation follows [semantic versioning](http://semver.org/) 

API documentation revisions will be assigned a unique version number in the format MAJOR.MINOR.REVISION. These version numbers follow semantic versioning pattern whereby:

* REVISION is incremented for revisions to a MINOR version. These changes represent nonfunctional changes to the API.
* MINOR version numbers are incremented when new functionality is introduced which is backwards compatible with existing functionality in the MAJOR version. MINOR versions numbers are semantically compatible with previous MINOR versions.
* MAJOR version numbers are incremented when new functionality is introduced which is semantically incompatible with previous versions.

`/api/v1/facilities.json`

All prior versions still supported by the code should be exposed by its own URL.