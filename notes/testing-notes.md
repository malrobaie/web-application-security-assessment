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
Request successfully modified and forwarded to the server. The application accepted user-controlled input without immediate rejection.

**Conclusion:**
Authentication input fields are directly controllable and represent a potential injection attack surface. Further testing would be required to confirm exploitability in a production system.

---

## XSS Test

**Location:**
Search functionality

**Payload:**

```html
<img src=x onerror=alert('XSS')>
```

**Result:**
JavaScript executed successfully in the browser (alert triggered)

**Conclusion:**
Reflected XSS vulnerability confirmed due to lack of input sanitization and output encoding

---

## Access Control Testing

**Method:**
Modified API resource identifiers using Burp Suite Repeater

**Endpoint:**
GET /rest/basket/{id}

**Test Cases:**

* /6 → valid data
* /1 → different user data
* /999 → null

**Result:**
Application returned data for different identifiers without enforcing authorization checks

**Conclusion:**
Confirmed IDOR vulnerability due to lack of server-side access control validation

---

## Sensitive Data Review

**Areas Checked:**
Local storage, session storage, cookies

**Method:**
Inspected browser storage using developer tools

**Findings:**

* JWT authentication token stored in Local Storage
* Basket identifier (`bid`) stored in Session Storage
* Authentication token also present in Cookies

**Conclusion:**
Sensitive authentication data is accessible via client-side storage, increasing risk of token exposure, especially in the presence of client-side vulnerabilities such as XSS

---

## DAST Scan

**Tool:**
OWASP ZAP

**Purpose:**
Identify additional vulnerabilities and validate manual findings

**Status:**
Automated scanning performed to supplement manual testing and identify additional risk areas
