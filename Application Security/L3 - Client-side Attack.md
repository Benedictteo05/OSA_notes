### OWASP
- Open Web Application Security Project (OWASP)
- Non-profit foundation that works to improve the security of software
- Community-led open source software projects
- Source for developers and technologies to secure the web

**OWASP Risk Rating Methodology**
- Risk model: Risk = Likelihood * Impact
	- Step 1: Identifying a risk
		- e.g. OWASP, SANS top 25
	- Step 2: Factors for Estimating Likelihood
		- e.g. Skill level, Motive, Opportunity, Size, Ease of discovery, Ease of Exploit, Awareness, Intrusion detection
	- Step 3: Factors for Estimating Impact
		- e.g. Loss of confidentiality, Loss of integrity, Loss of availability, Loss of accountability, Financial damage, Reputation damage, Non-compliance, Privacy violation
	- Step 4: Determining Severity of the Risk
	- Step 5: Deciding what to Fix 
		- After the risks to the application have been classified there will be a prioritized list of what to fix.
		- As a general rule, the most severe risks should be fixed first.
		- Not all risks are worth fixing.
		- Some loss is not only expected, but justifiable based upon the cost of fixing the issue.
	- Step 6: Customizing your Risk Rating Model
		- Risk ranking should be adapted to your own company purpose and mission

| Likelihood and impact levels| |
|-----------|-------|
|0 to < 3| Low|
|3 to < 6| Medium|
|6 to 9| High|

### Cross-Site Scripting (XSS)
- A client-side code injection attack allowing the injection of malicious code into a website.

