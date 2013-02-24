---
title: 'Implementation Notes'

layout: nil
---
* All dates should follow ISO 8601 and be in UTC. Ex) 2011-11-16T14:26:15Z
* All field/properties should follow the camelCasing convention
* Use UTF-8 encoding

RECOMMENDED PRACTICES

* While it is not required, we suggest implementations support gzip, etags and cache headers which can help reduce unnecessary data transfer which is helpful in low-bandwidth environments.
* Cache headers if implemented could be especially useful, as a common use case seems to be maintaining a mirror of facility information.
