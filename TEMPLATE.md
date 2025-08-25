# CVE-XXXX-YYYY — Vulnerability Title

### Overview
- **CVE ID:** CVE-XXXX-YYYY  
- **Published:** YYYY-MM-DD  
- **Severity (CVSS):** X.X (Medium/High/Critical)  
- **Affected Software/Versions:** Vendor / Product / Version  
- **Vulnerability Type:** e.g., SQL Injection, XSS, RCE, SSRF, IDOR  

**Summary:**  
Brief description of the vulnerability.  
Example: _A SQL injection in the login form of XYZ CMS allows unauthenticated attackers to extract user credentials._

---

### Context
Explain where the bug lives and how it’s reachable:  
- Application / component affected (API endpoint, form, file upload, etc.)  
- Typical user interaction vs attacker-controlled input  
- Authentication requirements (unauthenticated / low-priv / admin-only)  

---

### Root Cause
Explain **why** the vulnerability exists:  
- Flawed input handling or trust boundary  
- Missing sanitization/validation, improper access controls, weak parsing, etc.  
- Example code or request that highlights the mistake  

```http
POST /login HTTP/1.1
username=admin' OR '1'='1&password=anything
````
---

### Exploitation

Attacker walkthrough of how to exploit it:

1. **Trigger** — what input/request reaches the vulnerable code
2. **Manipulation** — how the payload interacts with backend logic
3. **Impact** — data leakage, authentication bypass, remote code execution, etc.
4. **Demonstration** — crafted request or script that proves the exploit

Use real HTTP requests, curl examples, or Burp Repeater payloads to illustrate:

```http
GET /profile?id=1' UNION SELECT username, password FROM users-- -
```
---
### Proof of Concept

Minimal working example showing the vulnerability in action.

* Example PoC script: [`poc/example.py`](poc/example.py)
* Or raw request files (`poc/exploit.req`)

---
### Exploitation Notes

Extra attacker insights:

* Bypasses for filters / WAFs (encoding tricks, case changes, polyglot payloads)
* Escalation opportunities (e.g., from XSS → account takeover)
* Chaining potential with other bugs (SSRF → RCE, SQLi → LFI → RCE)

---
### Lessons Learned

* Why this vulnerability class is dangerous in modern web apps
* Common patterns attackers should look for (e.g., unsanitized query params, unsafe deserialization)
* Broader implications for chaining web vulns into full compromises

---
### References

* [CVE Entry](https://cve.mitre.org/)
* [Exploit-DB PoC](https://www.exploit-db.com/)
* [Vendor Advisory](https://example.com/advisory)
* [Relevant Blog/Research](https://example.com/article)
