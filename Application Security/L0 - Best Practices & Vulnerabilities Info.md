1. [OWASP](https://owasp.org/www-project-top-ten/)
2. [SANS - The Top Cyber Security Risks](https://www.sans.org/blog/cis-controls-v8/)
3. [SANS Top 25 Programming Errors](http://www.sans.org/top25-programming-errors/)
4. [Qualys - Top 10](http://www.qualys.com/research/rnd/top10/)
5. [MITRE ATT&CK](https://attack.mitre.org/)
6. [[L0 - Best Practices & Vulnerabilities Info#^34f1fd|Common Weakness Enumeration (CWE)]]
	- http://cwe.mitre.org/
	- http://cwe.mitre.org/data/graphs/699.html
- [Common Vulnerabilities and Exposures (CVE)](http://cve.mitre.org/)

### [Common Weakness Enumeration (CWE)](http://cwe.mitre.org/)

^34f1fd
- They help developers and security practitioners to:
	- Describe and discuss software and hardware weaknesses in a common language.
	- Check for weaknesses in existing software and hardware products.
	- Evaluate coverage of tools targeting these weaknesses
	- Leverage a common baseline standard for weakness identification, mitigation, and prevention efforts.
	- Prevent software and hardware vulnerabilities prior to development.

### Common Weakness Scoring System (CWSS)
- CWSS provides a mechanism for prioritizing software weaknesses in a consistent, flexible and open manner.
- It is a collaborative, community-based effort that is addressing the needs of its stakeholders across government, academia, and industry.
- CWSS is organized into 3 metric groups:
	- Base findings, Attack Surface, and Environmental.
	- Each group contains multiple metrics/factors to compute a CWSS score.
- 3 sub scores are multiplied together, which produces a CWSS score between 0 - 100.

**Base Finding metric group**
- Capture the inherent risk of the weakness, confidence in the accuracy of the finding, and strength of controls.
- Factors:
	- Technical Impact
	- Acquired privilege
	- Acquired privilege layer
	- Internal Control Effectiveness
	- Finding Confidence

**Attack Surface metric group**
- The barrier that an attack must overcome in order to exploit the weakness.
- Factors:
	- Required privilege
	- Required privilege layer
	- Access Vector
	- Authentication Strength
	- Level of Interaction
	- Deployment Scope

**Environmental metric group**
- Characteristics of the weakness that are specific to a particular environment or operational context.
- Factors:
	- Business Impact
	- Likelihood of Discovery
	- Likelihood of Exploit
	- External Control Effectiveness
	- Prevalence

### Identification and Authentication Failures
**Attacks:**
- Automated attacks such as credential stuffing and brute force.
- Uses weal or ineffective credential recovery and forgot-password processes, such as "knowledge-based answers", which cannot be made safe.
- Uses plain text, encrypted, or weakly hashed passwords data stores.
- Missing or ineffective multi-factor authentication.
- Exposes session identifier in the URL.
- Reuse session identifier after successful login.
- Does not correctly invalidate Session IDs upon logout.
- Authentication and session management includes:
	1. Handling user authentication
	2. Managing active sessions
- Custom authentication and session management schemes are often developed
	- Custom schemes are frequently flawed in various areas.
		- e.g. Logout, password management, timeouts, account update.
- Impacts:
	- User accounts compromised or user sessions hijacked.

### Broken authentication and Session Management Prevention
- Account credentials must be properly protected by means of strong encryption.
	- SSL should be used in the transmission of credential information.
- Secure Session ID
	- Name should not give away details about the purpose and meaning of ID.
	- Length at least 128 bits to prevent brute force attacks.
	- Must be random enough to prevent guessing.
	- No meaning to the ID to prevent information disclosure attacks.
- Avoid XSS flaws which could be used to steal session ID.
- Session Management
	- Use built-in session management implementation.
		- E.g. ASP .NET/Core provide their own session management features.
	- Use SSL to protect session ID exchange.
	- Cookies
		- Secure Attribute
			- Cookies must always be passed using an encrypted tunnel when set.
		- HttpOnly Attribute
			- Cookies cannot be accessed by a client side script (XSS attack) when set.
			- Highly recommended to use non-persistent cookies for session management purposes.
	- Session Expiration
		- Minimize time period an attack can launch attacks over active sessions.

### HTTPOnly
- Syntax used within the HTTP response header
```
Set-Cookie: <name>=<value>[; <Max-Age>=<age>]
`[; exprires=<date>][; domain=<domain_name>]
[; path=<some_path>][; secure][; HttpOnly]
```

### Session Fixation
- Session Fixation is a specific attack against the session that allows an attacker to gain access to a victim's session.
- An attacker visits the website to obtain a valid Session.
- This valid session cookie is placed in the victim's browser by getting the victim to click on some malicious link.
- When the victim logs into the website, both the attacker and the victim will use the same session cookie that the attacker already knows, and thus the attacker-owned cookie is now authenticated and can be exploited.

### Cryptographic Failures
- Not properly protecting sensitive data
- e.g.
	- No appropriate encryption or hashing for credit cards and authentication credentials.
	- No SSL to protect sensitive data in transit.
	- Password database uses unsalted hashes to store passwords.
