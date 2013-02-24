---
title: 'Authentication'

layout: nil
---

Authentication is handled by [HTTP Basic Authentication](http://en.wikipedia.org/wiki/Basic_access_authentication).

Every API request must include a **valid authentication token** in the header.

The Authorization header is constructed as follows:

* Username and password are combined into a string "username:password"
* The resulting string literal is then encoded using Base64
* The authorization method and a space i.e. "Basic " is then put before the encoded string.

For example, if the user agent uses 'Aladdin' as the username and 'open sesame' as the password then the header is formed as follows:

`Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==`