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
		- E.g. Payment system error before downloading of media. Need block downloading until payment is confirmed.
- When handling errors, developers need to carefully choose what actions to take.

### Fail open errors
- A system set to fail open does not shut down when failure conditions are present.
- Instead, the system remains "open" and operations continue as if the system were not even in place. This strategy is used when access is deemed more important that authentication.
- Deny access until specifically granted vs Grant access until denied.

### Error Messages
- E.g. 
	- When a user tries to access a file that does not exist, the error message typically indicates, "file not found".
	- When accessing a file that the user is not authorized for, it indicates, "access denied". The user is not supposed to know the file even exists.
	- The above 2 such inconsistencies will readily reveal the presence or absence of inaccessible files or the site's directory structure.

### What is Exception?
- An exception is an event, which occurs during the execution of a program.
- It disrupts the normal flow of the program's instructions.
- Exception handling enables programmers to remove error-handling code from the "main line" of the program's execution.
- Simplify code construction and maintenance.
- Allow the problematic situation to be processed at multiple levels.

### Exception handling
- Exception handling is a programming concept that allows an application to respond to different error states (like network down)
- Handling exceptions and errors correctly is critical to making your code reliable and secure.

### Unhandled Exception
- An unhandled exception occurs when the application code does not properly handle exceptions. E.g. When you try to open a file on disk, it is a common problem for the file to not exist.
- An unhandled exception occurs when a developers does not anticipate and handle a potential exception.

### Handling Exception
- Catching and Processing Errors.
- In C# the exceptions can be handled by the try-catch-finally construction.
- Provided by `System.Exception`.
- Enable clear, robust and more fault-tolerant programs.
- Catch blocks can be used multiple times to process different exception types.

### Types of Exceptions
- .NET exceptions inherit from `System.Exception`.
- The system exceptions inherit from `System.SystemException`.
- E.g.
	- `System.Argum`