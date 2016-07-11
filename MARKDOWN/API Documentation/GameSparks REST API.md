---
src: /API Documentation/GameSparks REST API.md
---

# GameSparks REST API

The GameSparks REST API allows you to change the configuration of your game via your own processes, bypassing the need to use the GameSparks Portal Web interface.

## Authentication

All REST API methods require the use of HTTP Basic Authentication to authenticate with the service. You need to provide the username and password you use to login to the portal. The REST endpoint is secured over HTTPS, so there is no need to worry about your credentials being exposed. To authenticate using Basic Authentication you will need to provide an "Authorization" header. The Authorization header is constructed as follows:

  * Username and password are combined into a string "username:password"
  * The resulting string literal is then encoded using the RFC2045-MIME variant of Base64, except not limited to 76 char/line[9]
  * The authorization method and a space i.e. "Basic " is then put before the encoded string.
  * For example, if the user agent uses 'Aladdin' as the username and 'open sesame' as the password then the header is formed as follows:

Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==
