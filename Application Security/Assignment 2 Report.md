### Registration process
- Inherited from `IdentityUser` to specify additional field for `IdentityUser`.
- Created a model `ApplicationUser`.
- Save user to database using `CreateAsync` from `SignInManager`.
- Check for duplicate emails by checking if entered email is from an existing user. If it exists, return an error which prompts users to enter a different email address.
	- `userManager.FindByEmailAsync(emailAddress)`

### Securing credential
- Through Identity system, we can include 

### Validating passwords against top 100 common passwords
- `builder.AddTop100PasswordValidator<ApplicationUser>();`
- Source: https://github.com/andrewlock/CommonPasswordsValidator


### Max Failed Access Attempts 
- Limit is 3 failed attempts.
- Default lockout Time: 10 mins.

 
