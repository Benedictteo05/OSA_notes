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
