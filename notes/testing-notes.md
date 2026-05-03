## Burp Proxy Setup

* Launched Burp Suite Community Edition
* Created temporary project with default configuration
* Enabled proxy interception
* Used Burp built-in browser to route traffic
* Verified HTTP traffic flowing through proxy

---

## Authentication Request Analysis

**Endpoint:**
POST /rest/user/login

**Request Body:**

```json
{
  "email": "test@test.com",
  "password": "test123"
}
```

**Observation:**
User credentials are transmitted via JSON payload. This endpoint represents a critical attack surface for authentication bypass and injection testing.

---

## SQL Injection Test

**Method:**
Intercepted login request using Burp Suite and modified input parameters

**Payload:**

```sql
' OR 1=1--
```

**Result:**
Request successfully modified and forwarded to server

**Conclusion:**
Authentication input fields are directly controllable and susceptible to injection testing. Further validation would determine exploitability in a production system.

---

## XSS Test

**Location:**
Search functionality

**Payload:**

```html
<img src=x onerror=alert('XSS')>
```

**Result:**
JavaScript executed successfully in browser (alert triggered)

**Conclusion:**
Reflected XSS confirmed due to lack of input sanitization and output encoding

---

## Access Control Testing (In Progress)

**Method:**
Modified API resource identifiers using Burp Suite Repeater

**Example Target:**
GET /rest/basket/{id}

**Observation:**
Testing focused on accessing resources outside assigned user context

**Conclusion:**
Further validation required to confirm unauthorized data access behavior

---

## Sensitive Data Review (In Progress)

**Areas Reviewed:**

* Local storage
* Session storage
* Cookies
* API responses

**Observation:**
Evaluating presence of sensitive data such as tokens, user information, or system metadata

**Conclusion:**
Pending validation of exposure risk

---

## DAST Scan (Planned)

**Tool:**
OWASP ZAP

**Purpose:**
Identify additional vulnerabilities and validate manual findings

**Status:**
Pending execution
