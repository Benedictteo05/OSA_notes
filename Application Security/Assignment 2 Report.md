### Registration process
- Inherited from `IdentityUser` to specify additional field for `IdentityUser`.
- Created a model `ApplicationUser`.
- Save user to database using `CreateAsync` from `SignInManager`.
- Check for duplicate emails by checking if entered email is from an existing user. If it exists, return an error which prompts users to enter a different email address.
	- `userManager.FindByEmailAsync(emailAddress)`

### Securing credential
**Strong Password**
- Through Identity system, we can include validation for the backend.
	- `RequireNonAlphanumeric`, `RequireDigit`, `RequireUppercase`, `RequireLength`,
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
- To detect multiple logins from different devices. I stored the session Id with the user's data, so by checking if it exists when user login, I can tell if there is a already a session for the current user.

### Login/Logout
 - Using Identity classes `MaxFailedAccessAttempts` and  `DefaultLockoutTimeSpan` for rate limiting and defining time that it locks out.
 - To timeout, the `Clear()` property allows for what was stored inside the user's session to be cleared.
 - Using `PasswordSignInAsync`, it helps to compare passwords of users with their email without needing to hash it and compare between the saved password manually.
 - To decrypt crucial user data, it works similar as to encrypt it,  making use of `DataProtectionProvider` to `Unprotect` the credentials.

### Anti-bot
- Register reCAPTCHA v3 keys on the reCAPTCHA admin console. 
	- https://www.google.com/recaptcha/admin/create
- Saving both the secret key and the site key to use them.
- By reading the response from the `ReCaptcha`, we can determine whether to authenticate a user or not.
	- Whether it is not a success or if the score is below 0.5 (varies from 0.0 to 1.0).

## Proper Error handling
- Create an error page `404.cshtml`, under a folder `errors`.
- In `program.cs`, use `app.UseStatusCodePagesWithRedirects("/errors/{0}");`

### Software Testing 
- Making use of GitHub's internal tool, under security to enable 