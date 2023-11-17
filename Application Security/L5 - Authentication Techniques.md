### Types of authentication methods
- What a user knows (knowledge)
	- Password
	- Pin
- What a user has (possession)
	- NRIC, Passport
	- OTP (One time password)
- What a user is (inherence)
	- Standard biometrics
		- e.g. Fingerprints, Retina, Face
	- Behavioral biometrics
		- Keystroke dynamics;
		- Voice recognition
		- Computer foot printing
		- Gait (Pattern of movement)
	- Cognitive biometrics
		- Memorable events
		- Identify specific faces

### Outdated Web authentication methods
- What you know 
	- Old authentication methods such as login & passwords is no longer suffice due to common web vulnerabilities as well as the growing sophistication of hacking tools.
	- More than 1 person may gain access to the same account due to:
		- Illegal sharing of account
		- Stealing of accounts

### Attacks on Authentication System
**Attacks**
- XSS attacks
- Brute-force attempts using bots
- SQL injection attack
- Multiple login attempts from a single IP

### Preventive measures to protect Authentication System
**Prevention**
- Limiting the frequency of online login attempts to an account through various actions:
	- Enforcing multi-factor authentication, Anti-bots (e.g. CAPTCHA), or other forms of verification.
	- Locking an account after a specified number of login attempts is reached.
	- Prohibiting multiple sessions for single user and location-based verification.

### Multi-factor Authentication
- Granting access to a website or application by presenting two or more pieces of evidence (or factors) to an authentication mechanism:
	- Knowledge 
	- Possession
	- Inherence
- Implement multi-factor authentication to prevent automated (bot), credential stuffing, brute force, and stolen credential re-user attacks.

### 2-Factor Authentication (2FA)
- e.g. An online banking system where a login control (what you know) required a second factor authentication such as SMS/Token/Email/etc (posse)