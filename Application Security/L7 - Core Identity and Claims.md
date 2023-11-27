### ASP.NET Core Identity
- A framework for managing and storing user accounts in ASP.NET Core apps - Microsoft's membership system for managing application users.
- Manages users, passwords, profile data, roles, claims, tokens, email confirmation, and more.

### Features of ASP.NET Identity
- User management
	- Built-in APIs for creating, deleting, or modifying user details.
	- Programmers can easily utilize these APIs for those purpose.
- External Identity Providers
	- Users can now easily log-in with their social media accounts, including platforms like Facebook, Gmail, Twitter, etc. Azure Active directory can also be used for logging into the system as well. What's more, if none of the above identity providers suits your requirement, you can roll out your own identity provider and user it for identification.
- Two-factor Authentication
	- Implement security mechanism in which the user is authenticated by a combination of two methods. 
	- e.g. via Password + Security code.
	- Adds another layer of security to the system.
- Roles Management
	- Roles are stored in a separate table. You can add, edit, and delete roles according to specific needs.
- Claims Management
	- A claim in a membership system is the information of the user. This can be the user's id, name, or email address that can identify the user on an application level. .NET developers are now able to add further information about the user.
- Account Lockout
	- Disables the user's account if they enter an incorrect password for a specific number of times. The feature locks the account for a short period.

### Components of ASP.NET Identity
- User
	- A user is an entity in the system.
	- `IdentityUser` class holds the important information to the user, such as User Id and password.
	- Developers can create custom class and deriver it from `IdentityUser` to add more descriptive details to a user.
- User Manager
	- The `UserManager` class manages the user accounts and helps to perform a variety of operation including:
		- Creating or removing a user account.
		- Modifying passwords.
		- Assigning or removing the user from a role.
	- Entity Framework DbContext
		- The database schema in ASP.NET Identity is created with the Entity Framework's Code-first approach