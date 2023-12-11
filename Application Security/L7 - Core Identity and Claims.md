## ASP.NET Core Identity
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
	- The database schema in ASP.NET Identity is created with the Entity Framework's Code-first approach.
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
^7239f4
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
	- `builder.Services.ConfigureApplicationCookie (..)  `
	- `app.UseAuthentication();`

### Identity Services
- Call the methods in the following order:
1. Add {Service}
	- E.g. `builder.Services.AddAuthorization(options => ..)`
2. `builder.Services.{?}{Service}`
	- E.g.:
		- `builder.Services.AddAuthorization(options => ...)`
		- `builder.Services.AddDbContext<AuthDbContext>(...)`
		- `builder.Services.ConfigureApplicationCookie(Config => ..)`

## Authentication & Authorization

### Creating an Identity
- Namespace: Microsoft.Asp.NetCore.Identity
- The UserManager class of Microsoft.AspNetCore.Identity namespace helps to manage Identity users stored in the database.
- The generic version of this class is `UserManager<T>` where T is the class chosen to represent users.
	- `UserManager<IdentityUser> userManager`
- Use this class to perform CRUD operations for the users.

```
(add reference)
using Microsoft.AspNetCore.Identity;

(Create a user Class)
public class RModel{

	[Required]
	public string Name {get;set;}
	[Required]
	public string Email {get;set;}
	[Required]
	public string Password {get;set;}
}
```

```
(Prepare the Identity User data)
var user = new IdentityUser()
{
	userName = RModel.Name,
	Email = RModel.Email
}
```

```
(Add User into database)
IdentityResult result = await userManager.CreateAsync(user, RModelPassword);
if (result.Succeeded)
{
return RedirectToPage("Index");
}
else{}
```

### Authenticating an Identity
- In order to use the Authentication feature in .NET Core, developers will need to [[L7 - Core Identity and Claims#^7239f4|add support for ASP.NET Core Identity]].
- There are 2 methods of authentication in ASP.NET Core Identity.
	- Cookie vs Token

### Authentication methods:
- `builder.Services.AddAuthentication(..).AddCookie (..)`
- `builder.Services.AddAuthentication(..).AddFacebook(..)`
- `builder.Services.AddAuthentication(..).AddGoogle(..)`

### App Cookie configuration
- To make any changes to the behavior of the cookie, you may make code changes to `ConfigureApplicationCookie()` method of the `Startup.cs` or `Program.cs`.
```
services.ConfigureApplicationCookie(options =>  
{  
options.Cookie.Expiration = TimeSpan.FromDays(150);  
options.Cookie.HttpOnly = true;  
options.LoginPath = "/Account/Login";  
options.LogoutPath = "/Account/Logout";  
options.SlidingExpiration = true;  
});
```

### App Cookie Settings
- `Cookie.Name`: name of the application cookie.
- `Cookie.HttpOnly`: it specify that cookie is accessible from client side scripts or not.
- `ExpireTimeSpan:` it specify that the time that authentication ticket stored in the cookie and remain valid.
- `LoginPath`: Login page path.
- `LogoutPath`: Logout page path.
- `AccessDeniedPath`: it defines the path on which user will be directed if authorization fails.
- `SlidingExpiration`: This is a Boolean property. When it set to true. New cookie will be created when current cookie is more than halfway through the expiration window.

### `SignInManager` classes
- The `SignInManager` is responsible for Authentication a user:
	- Signing in
	- Signing out
	- Issue authentication cookie

- `SignInManager` defines methods related to the authentication of users.
	- `PasswordSignInAsync` method accepts a username and a password and returns a sign-in result with a property indicating whether the authentication attempt was successful.

### `SignInAsync`
- If the user credential is successfully verified, the `SignInAsync` method creates an encrypted cookie (together with the security context) and adds it to the current response.  
- The Current response is returned to User. The User browser reads the cookie from the response and stores it securely. When user sends another request to the server, the browser sends the cookie along with the request.

### Authorizing an Identity
- After successful login to the application, authorization mechanism checks whether login user has privileges to access the application resource.

### Types of Authorization in Identity
- Role-based
	- Roles are commonly used to create fine-grained authorization policies that differentiate between different signed-in users.
```
string [] roleNames = {"Administrator", "GroupUser", "User", "Guest"};
foreach(var roleName in roleNames)
{
	var roleExist = await Rolemanager.RoleExistsAsync(roleName);
	if (!roleExist)
	{
		roleResult = await RoleManager.CreateAsync(new IdentityRole(roleName));
	}
}
```

```
user = new IdentityUser()
{
	UserName = "Timothy.W.gmail.com",
	Email = "Timothy.W.gmail.com",
};
await Usermanager.CreateAsync(user, "Time@123");
await UserManager.AddToRoleAsync(user, "")
```
- Claims-based
	- Claims are a general-purpose approach to describing any data that is known about a user and allow custom data to be added to the Identity user store.

### Setting the page requirements
```
// Must be 'GroupUser' AND 'User'
[Authorize(Roles=”GroupUser”)]
[Authorize(Roles=”User”)]

// Must be 'GroupUser' OR 'User'
[Authorize(Roles=”GroupUser, User”)]
```
