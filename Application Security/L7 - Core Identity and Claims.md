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
	- By default, all of the tables are created in a specific database. However, they are customizable.  
	- Create a `DbContext` class that derives from the `IdentityDbContext` class and store the database information as per your needs.
- Role 
	- Developers may create **Roles** that contain a set of permissions for performing a set of activities in the app.
	- Use the `RoleManager` class to add additional details to a role if required.
- `RoleManager`
	- Adding, removing, and confirming the existence of a specified role.
- Authentication Manager
	- The authentication in ASP.NET identity is handled by the `AuthenticationManager` class.
		- This class takes care of signing the user in and out.
	- The `IAuthenticationManager` interface holds all the necessary information regarding the authentication process.

### Adding ASP.NET Core Identity
1. [[L7 - Core Identity and Claims#^b72128|Add the required packages and references]]
2. [[L7 - Core Identity and Claims#^27d2c2|Set Auth type or DBContext]]
3. [[L7 - Core Identity and Claims#^3420e9|Add authentication middleware]]

**Add the required packages and references** ^b72128
- Developers are required to install a couple of packages to be able to use ASP.NET Core identity
- Add Package
	- `Microsoft.AspNetCore.Identity.EntityFrameworkCore`   
	- `Microsoft.AspNetCore.Identity.UI`
- Add Reference
	- `using Microsoft.AspNetCore.Identity;`

**Set Auth type or DBContext** ^27d2c2
- Option 1:
	- Use "Individual Account" as the authentication type in project template

- Option 2:
	- Alternative developers may set authentication type to "None" and later set DbContext to inherit from `IdentityDbContext<IdentityUser>`.
	- After performing [[ASP .NET#^960f9f|migration]] , the Identity will adds a number of tables related to user and role information.

**Add authentication middleware** ^3420e9
- Add authentication and authorization middleware.  
- Identity is enabled by calling `UseAuthentication`.  
- UseAuthentication adds authentication middleware to the HTTP request.  
- For example in Program.cs of core web app, inject the following method(s) and Service(s):
	- `builder.Services.AddDbContext<AuthDbContext>();` 
	- `builder.Services.AddIdentity<IdentityUserIdentityRole().AddEntityFrameworkStores<AuthDbContext>();`
	- builder.Services.ConfigureApplicationCookie (..)  
	- `app.UseAuthentication();`