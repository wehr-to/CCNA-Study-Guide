- REST APIs must be stateless
- In REST API Basic authentication, credentials are encoded in Base64.

- Q: What does CRUD stand for?
Cread, Read, Update, Delete

- CRUD Delete = HTTP DELETE
- CRUD Read = HTTP GET
- CRUD Create = HTTP POST
- CRUD Update = HTTP PUT, PATCH


- HTTP Response class 1xx = Informational
- HTTP Response class 2xx = Successful
- HTTP Response class 3xx = Redirection
- HTTP Response class 4xx = Client Error
- HTTP Response class 5xx = Server Error

- HTTP Response code 102 = Processing
- HTTP Response code 200 = OK
- HTTP Response code 201 = Created
- HTTP Response code 301 = Moved Permanently
- HTTP Response code 401 = Unauthorized
- HTTP Response code 404 = Not Found
- HTTP Response code 500 = Internal Server Error

- Q: What does URI stand for?
- Uniform Resource Identifier
- Q: In API key authentication, in which part of the message should the client specify the key?
- The HTTP Authorization header (recommended). *Other options: URL, cookie
- Q: In REST API Basic authentication, in which part of the message are the credentials included?
- In the HTTP Authorization header
- Q: In REST API Bearer authentication, are the bearer tokens valid indefinitely?
- No; they expire after a set period of time
- Q: In REST API Bearer authentication, in which part of the message are the credentials included?
- In the HTTP Authorization header
- Q: Is Base64 encoding secure?
- No. Encoding is easily reversible; it is not encryption.

- OAuth 2.0: A refresh token can be used to renew access tokens without user reauthentication.
- REST API OAuth2.0 authentication provides access delegation.
- REST API Bearer authentication uses a token (also called a bearer token) for authentication.

- What are the four entities in OAuth 2.0?
- 1: Resource owner
- 2: Client app
- 3: Auth server
- 4: Resource server

- Q: Which form of REST API authentication uses a username/password combination?
- Basic authentication

- Q: Analyze the following URL: https://sandboxdnac.cisco.com/dna/intent/api/v1/network-device

- 1: Which part of the following URI is the authority?
- sandboxdnac.cisco.com

- 2: Which part of the following URI is the path?
- /dna/intent/api/v1/network-device

- 3: Which part of the following URI is the scheme?
- https

- API key authentication uses a static (non-expiring) key issued by the API provider.
