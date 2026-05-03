## Burp Proxy Setup

- Burp Suite Community Edition launched
- Temporary project used with default configuration
- Proxy intercept enabled
- Used Burp built-in browser to route traffic
- Verified application traffic flowing through Burp

### Authentication Request Analysis

Endpoint:
POST /rest/user/login

Request Body:
{
  "email": "test@test.com",
  "password": "test123"
}

Observation:
User credentials are transmitted via JSON payload, making this endpoint a primary target for injection testing and authentication bypass attempts.