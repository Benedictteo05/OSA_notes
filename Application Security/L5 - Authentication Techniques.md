### Types of authentication methods
- What a user knows (knowledge)
	- Password
	- Pin
- What a user has (possession)
	- NRIC, Passport
	- [[L5 - Authentication Techniques#^183ff1|OTP (One time password)]]
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
^183ff1
- e.g. An online banking system where a login control (what you know) required a second factor authentication such as SMS/Token/Email/etc (possession).
- Is 2FA required for all websites

**Steps for 2FA (SMS OTP)**
1. System verifies userid and password
2. System generates 6 digits SMS OTP to user
	- Save a copy of OTP values and date/time created in db
3. System prompts user for OTP
4. System check if OTP entered is valid
	- Valid if OTP matches the one save in db
	- if OTP matches, check if OTP is received before the expired date/time
5. If user request OTP again due to timeout, repeat (step 2 - 4)
6. System create session and redirect to homepage

**Authenticator App**
- Free security app that can protect your account (e.g. Google, Microsoft, Website) against password theft.
- The Authenticator app (IOS/Android) generates a random code used to verify your identity