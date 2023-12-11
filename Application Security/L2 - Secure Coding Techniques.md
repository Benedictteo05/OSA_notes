****### Basic Application Security Guidelines
- Secure the input
	- Validate all input
	- e.g. Form registration
- Adopt Secure Application Processing
	- Avoid Dangerous Language Constructs
	- Check Bounds
	- Ensure Exception Safety 
	- Adopt good programming practices
	- Test and verify - Use test tools
	- Request only sufficient privileges
	- Exit safely
- Produce Safe output
	- Communicate safely to the outside world

### Security Strategies
- Security should be built into applications right from the start.
- Developers, designers, architects and project managers would do well to follow these tried and tested security principles.
- The principles are derived from the $SD^3+C$ strategies

### $SD^3+C$ strategies 

**Secure by Design**
- Developers follow secure coding best practices and implement security features in their application to overcome vulnerabilities.
- Ensure that the software design is secured right from the start.
- Bad software design can make software difficult to secure later.
- e.g. Your application handles sensitive data, so you will encrypt the data and protect it from theft and tampering. This consideration to use cryptography in your application is done at the design stage.

**Secure by Default**
- Least privilege
	- Allow each user/process minimum privileges to do his/its work.
- Defense in depth
	- Design software that will not easily break down just because one security mechanism has been broken. if possible, employ multiple security mechanisms such that an attacker would need to breach several layers before being successful.
- Conservative default settings
	- The development team is aware of that attack surface for the product and minimizes it in the default configuration.
- Avoidance of risky default changes to operating system or security settings.

**Secure in Deployment**
- This means that applications can be maintained securely after deployment by updating with security patches, monitoring for attacks, and by auditing for malicious users and content.
- Security functions must be easily administered by users.
- Software must be easily patched to allow for security patches, if required.
- In the event of application failure or errors, these events should be logged so that administrators can help resolve the issues.

**Secure in Communications**
- Security response
	- Development teams responding promptly to reports of security vulnerabilities and communicate information about security updates.
- Community engagement
	- Development teams proactively engage with users to answer questions about security vulnerabilities, security updates, or changes in the security landscape.

### Security Principles

**Minimize your attack surface**
- Reduce potential points of entry from which attackers can take advantage of.
- In particular, take note of the following:
	- Services running in elevated privilege
	- Services that are running by default
	- Applications that are running
	- Open ports
	- Open named pipes
	- Accounts with administrative rights
	- Files, directories and registry keys with weak access control lists (ACLs)

**Employ secure defaults**
- Most users would choose defaults when installing your software.
- Ensure default settings/services are necessary and not exploitable by hackers.
- e.g. Windows 2000 installs IIS by default. This allows hackers to attack systems through the IIS.

**Assume external systems are insecure**
- For all data that is received from external sources, consider them to be possibly from attackers.
- Filter these data for validity before allowing them into the system.

**Fail Safely**
- Design program to recover or terminate 'gracefully' upon any form of failure.
- When the application fails, ensure that data is not lost or disclosed to unauthorized parties.

**Remember that security features != Security**
- Use correct security mechanisms to mitigate relevant threats.
- Software will not be secure because a lot of security mechanisms are implemented.

**Never depend on security through obscurity**
- Always assume that the attacker knows everything you know.
- Obscurity is a useful defense only when it is not the only defense.
- Attacks can easily find information that you try to hide.


