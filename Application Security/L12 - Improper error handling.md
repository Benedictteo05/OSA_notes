### Web Application Errors
- It is common for web applications to frequently generate error conditions during normal operation.
- These errors must be properly handled according to a well thought out scheme:
	- Provides meaningful error message to the user.
	- Provides diagnostic information to the site admin.
	- Provides no useful information to an attacker.

### Improper error handling
- An improper handling of error could potentially results in detailed internal error messages such as:
	- Stack traces
	- Database dumps
	- Error codes
	- being displayed to the unknown users or hackers.
- These messages display implementation details that should never be revealed.
- Such details can provide hackers important clues on potential flaws in the site.

### Action
- When Exceptions are thrown what should be the next action:
	- Fail Open System
		- Allow access
		- E.g. Payment system error before shipping can be confirmed. Need to re-try payment again. If not, this  might results in lost of business.
	- Fail Closed System
		- Deny access
		- E.g. Payment system error before downloading of media. Need block downloading until paym