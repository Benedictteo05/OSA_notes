### Registration process
- Inherited from `IdentityUser` to specify additional field for `IdentityUser`.
- Created a model `ApplicationUser`.
- Save user to database using `CreateAsync` from `SignInManager`.
- Check for duplicate emails by checking if entered email is from an existing user. If it exists, return an error which prompts users to enter a different email address.
	- `userManager.FindByEmailAsync(emailAddress)`

### Securing credential
**Strong Password**
- Through Identity system, we can include validation for the backend.
	- `RequireNonAlphanumeric`, `RequireDigit`, `RequireUppercase`, `RequireLength`, `MaxFailedAccessAttempts`, `DefaultLockoutTimeSpan`
- For the frontend, I chose a progress bar in addition to feedback message to indicate visually how secure a user password is, this allows for a smoother and pleasant experience for user. 
- Reason for both backend and frontend validation is because penetration testing works only on server side, therefore we need to have server side validation.
**Securing user data and passwords**
- From nuGet packages we can install a package to validate passwords against the top 100 or 5000 common passwords, this enhances the effectiveness user's passwords.
- Using `DataProtectionProvider` we can create a secret key to create a secret key. This secret key can be used to encrypt crucial user data such as NRIC. 
- With the same key generated, we can use it to decrypt user's data to display it back to them.

### Validating passwords against top 100 common passwords
- `builder.AddTop100PasswordValidator<ApplicationUser>();`
- Source: https://github.com/andrewlock/CommonPasswordsValidator

### Session
- We can generate a session Id using `Guid`, and storing with our user's data.
- In `program.cs` we can implement secure session using `IServiceCollection AddSession`.
	- Specifying fields such as `IdleTimeout`, `HttpOnly`, `SecurePolicy` and `isEssential`
- To use session inside login, through `IHttpContextAccessor`, the Session property provides access to allow developers to `setString()` in users' sessions.
- To timeout, the `Clear()` property allows 

### Max Failed Access Attempts 
- Limit is 3 failed attempts.
- Default lockout Time: 10 mins.

 
