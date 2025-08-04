## API Keys
- API key authentication uses a static kety issued by the API provider
- Client uses this key in each API call for authentication
- Unlike bearer tokens, the API key is static and remains valid until revoked

### API keys can be sent in 
- HTTP Authorizaton header (recommended)
- URL: not recommended, URLs are often logged by web servers, proxies, browsers, etc

### advantages: 
- Easier to implement than bearer, no need to refresh tokens
- Good for tracking API usage, often used by cloud services and third party APIs

### Disadvantages: 
- If stolen, the key grants full access until revoked
- API keys must be rotated manually to maintain security, whereas tokens expire automatically
