# REST API & HTTP Essentials 

## General REST Facts

- REST APIs must be stateless  
- In REST API Basic authentication, credentials are encoded in Base64  
- API key authentication uses a static (non-expiring) key issued by the API provider  

## CRUD and HTTP Methods

**Q: What does CRUD stand for?**  
- Create, Read, Update, Delete  

| CRUD Operation | HTTP Method      |
|----------------|------------------|
| Create         | POST             |
| Read           | GET              |
| Update         | PUT, PATCH       |
| Delete         | DELETE           |

## HTTP Response Classes

| Class Code | Meaning         |
|------------|-----------------|
| 1xx        | Informational   |
| 2xx        | Successful      |
| 3xx        | Redirection     |
| 4xx        | Client Error    |
| 5xx        | Server Error    |

## Common HTTP Response Codes

| Code | Meaning                 |
|------|-------------------------|
| 102  | Processing              |
| 200  | OK                      |
| 201  | Created                 |
| 301  | Moved Permanently       |
| 401  | Unauthorized            |
| 404  | Not Found               |
| 500  | Internal Server Error   |

## Authentication Methods in REST APIs

| Method          | Description                                                                 |
|------------------|------------------------------------------------------------------------------|
| **Basic Auth**    | Uses a username/password combo encoded in Base64                           |
| **Bearer Auth**   | Uses a bearer token for authentication                                      |
| **API Key Auth**  | Uses a static, provider-issued key                                          |
| **OAuth 2.0**     | Uses tokens, supports access delegation and refresh tokens                 |

### Q&A: Authentication Details

- **Q: Which form of REST API authentication uses a username/password combination?**  
  - Basic authentication  

- **Q: In REST API Basic authentication, in which part of the message are the credentials included?**  
  - In the HTTP Authorization header  

- **Q: In REST API Bearer authentication, are the bearer tokens valid indefinitely?**  
  - No; they expire after a set period of time  

- **Q: In REST API Bearer authentication, in which part of the message are the credentials included?**  
  - In the HTTP Authorization header  

- **Q: Is Base64 encoding secure?**  
  - No. Encoding is easily reversible; it is not encryption.  

- **Q: In API key authentication, in which part of the message should the client specify the key?**  
  - The HTTP Authorization header (recommended)  
  - *Other options: URL, cookie*  

## OAuth 2.0

- OAuth 2.0: A refresh token can be used to renew access tokens without user reauthentication  
- REST API OAuth2.0 authentication provides access delegation  
- REST API Bearer authentication uses a token (also called a bearer token) for authentication  

### Q: What are the four entities in OAuth 2.0?
1. Resource owner  
2. Client app  
3. Auth server  
4. Resource server  

## URI Anatomy (REST API Context)

**Q: Analyze the following URL:**  
`https://sandboxdnac.cisco.com/dna/intent/api/v1/network-device`

| Component | Value                                 |
|-----------|----------------------------------------|
| Scheme    | `https`                                |
| Authority | `sandboxdnac.cisco.com`                |
| Path      | `/dna/intent/api/v1/network-device`    |

- Base64 is an encoding scheme, which is a way of representing data
- Unlike encryption, it is not secure and can easily be decoded
- Always use HTTPS (HTTP + TLS) for security

## Bearer
- More secure than basic auth
- Client obtains a token by authenticating with an authorization server
- The term bearer meaans anyone who possesses the token can use it
- If an attacker steals the token, they can make API calls as if they were the legitimate user
- To mitigate, tokens expire after a set period of time
- 
