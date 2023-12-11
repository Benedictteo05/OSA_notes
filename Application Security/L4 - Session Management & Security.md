### HTTP is Stateless
**HTTP is a stateless protocol**
- It follows a request/response pattern. 
	- i.e. User requests a resource and the web server responds with the requested resource.
- Information is not retained (pass on) from one request to another
- Benefits:
	- Lightweight, avoid straining the server as it does not have to keep track of connected clients.

### Session Management
2 Types of state management techniques
- Client-side state management
	- State related information will directly get stored on the client-side
- Server-side state management
	- All the information is stored in the user memory


### Session Management (Server)
- Session
	- Session is used to store information and identity. The server stores information using `Session_id`.
		- Session Ids are attractive to attackers because once obtained they can basically hijack user's identities.
	- Session State Variables are available across all pages, but only for a given single session.
		- 2 events: `Session_start()`, `Session_End()`
	- In a typical website, after authentication is successful verified from database, user will be redirected to the homepage.
	- How do we know from the next page that the authentication was successful?

**Example**
- Store value to session variable
- Sample code to create a session variable
```
protected void btnSubmit_Click(object sender, EventArgs e)
{
	Session.add("UserName", txtboxloginid.Text);
	
	OR
	
	Session["UserName"] = txtboxloginid.Txt;
	Response.Redirect("Home.aspx")
}
```

- Retrieve value from session
- Need to cast the return value the correct data type
- Sample code to retrieve session
```
string LoginUser = (String)Session["ssuserName"];
Int loancnt = (int)Session["ssloadcount"];
```

- Delete session object
- To remove a specific session object
```
Session.Remove("cartValue");
```
- To remove all objects
```
Session.Abandon();
```

### Configuring Session Timeout
- Session timeout value can be specified in the web.config file (.NET Framework)
- It indicates the time (in minutes) that the session can be idle before it is abandoned
- Configure session timeout using `<sessionState>` attribute
- By default, session timeout is 20 minutes
- In the example below, the session will timeout in 1 minute in web.config
```
<system.web>
	<sessionState timeout="1"></sessionState>
</system.web>
```

### How is data stored in "Session"
- InProc Mode
	- It is a default session mode and a value store in web server memory (IIS)
	- Session value stored when server starts and it ends when the server is restarted.
	- Limited to ONLY one server
- State Server Mode
	- In this mode, session data is stored in separated server.
- SQL Server Mode
	- in this mode, session data is stored in the database. It is a secure mode.

**Application**
- State is maintained throughout until application shut down.
- Shared by all users accessing the application.
- Mainly store user activity in server memory and application event shown in Global.asax file.
- 3 events: `Application_start()`, `Application_Error()`, `Application_End()`

**Cache**
- Cache is stored on server side.
- It implements Page Caching and data caching.
- Cache is use to set expiration policies:
	- `Response.Cache.SetExpiresTime(DateTime.Now.AddDays(1));`

### Dependency Injection 
**Transient**
- Every time you refresh, the session id changes
- Renewed Data for each page

**Scoped**
- Only when you go to the next tab, it will refresh the session id

**Singleton**
- Same data in the some scope, but session id will refresh in different scope

### Session Management (Client)
- Cookies
	- A small amount of data which is either stored at client side in text file or in memory of the client browser session.
	- Every time a user visits a website, cookies are retrieved from the user machine and help identify the user.
```
// Creating a cookie
myCookie.Values.Add("muffin", "chocolate");
myCookie.Values.Add("babka", "cinnamon");

// Adding Cookie to collection
Response.Cookie.Add(myCookie);

// Getting Values stored in a cookie
Response.Write(myCookie["babka"].ToString());

// Setting cookie path
myCookie.Path = "/forums"

// Setting domain for a cookie
myCookie.Domain = "forums.geekpedia.com";

// Deleting a cookie
myCookie.Expires = DateTime.Now.AddDays(-1);
```
	
- Cookie info in Browser 
- Google Chrome -> Settings -> Privacy and Security

- Persistent Cookie
	- Cookies having an expiration date is called persistent cookie. This type of cookie reaches their end as their expiration dates comes to an end. In this cookie we set an expiration data.
```
Response.Cookies["UserName"].Value = "Abhishek";
Response.Cookies["UserName"].Expires = DateTime.Now.AddDays(1);

HttpCookie aCookie = new HttpCookie("Session");
aCookie.Value = DateTime.Now.ToString();
aCookie.Expires = DateTime.Now.AddDays(1);
Response.Cookies.Add(aCookie);
```
	
- Non Persistent Cookie
	- Not stored in the client's hard drive permanently
	- Maintains user information as long as the user access or uses the services.
- `Controlstate`
	- A private `ViewState` for specific controls only.
	- To cache data necessary for a control to function properly.
	- Not affected when `ViewState` is turned off.
- Hidden Field
	- Hidden field is not displayed on the browser.
	- `Response.Redirect("ShowStringValue.aspx?Username=" + txtUsername.Text);`
	- Values are exchanged in clear text.
	- It is visible to all the users in url as in the following link,
```
if (HiddenField1.Value != null)
{
	int val = Convert.ToInt32(HiddenField1.Value) + 1;
	HiddenField1.Value = val.ToString();
	Label1.Text = val.ToString();
}
```
- `ViewState`
	- For page level state management
	- Enabled by default
		- Change the `EnableViewState` value to either TRUE (enabling) or FALSE
	- Stores any type of data (small data)
	- Enables and disables on page level control.
	- Supports Encryption and Decryption and data/value is stored in hashed format.
```
if (ViewState["UserName"] != null)
{
	lblName.Text = ViewState["UserName"].ToString();
}
```
- Query String
	- Query string stores the value in URL.
	- `Response.Redirect("ShowStringValue.aspx?Username" + txtUsername.Text);`
	- Values are exchanged in clear text.
	- It is visible to all the users in url.

### .Net Core Session Mgt
- Hidden Field, Query String, Cookies, Session Variables.
- Session is not enabled by default in ASP.NET Core.

**3 Steps:**
- Step 1
		- Create Session Object/value in `OnPost`
		-  Check if `ModelState` is valid
	```
	public IActionResult OnPost()
	{
		if (ModelState.Isvalid)
		{
			HttpContext.Session.SetString("SSName", MyEmployee.Name);
			HttpContext.Session.SetString("SSDept", MyEmployee.Department);
			return RedirectToPage("Confirm");
		}
	
		return Page()
	}
	```
	
- Step 2
	- At runtime info in Startup.cs
	- Add `services.AddSession() in ConfigureServices (IServiceCollection)`
	```
	public void ConfigureServices(IServiceCollection services)
	{
		...
		services.AddSession(options => {});
		...
	}
	```
	
	-  Add `app.UserSession() in Configure(...)`
	```
	public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
	{
		...
		app.UseSession();
		...
	}
	```
	
- Step 3
	- In the subsequent Page
	- Extract session data using `HttpContext.Session.GetString(...)`
```
	public IActionResult OnGet()
	{
		if (!String.IsNullOrEmpty(HttpContext.Session.GetString("SSName")))
		{
			HttpContext.Session.GetString("SSName");
		}
	}
```

### Configuring Session Timeout (.NET Core)
**In `startup.cs`**
```
public void ConfigureServices(IServiceCollection services)
{
	services.AddRazorPages();
	services.AddSession(options => {
		options.IdleTimeout = TimeSpan.FromMinutes(20);
	})
	services.AddTransient<EmployeeService>();
}
```
- By default, session timeout = 20 minutes

### Session services
- Transient 
	- Every request, the service will create a new session id.
	- Very secure.
	- However, it is taxing on the server as it keeps generating the id.
- Scope
	- Same session id within the same browser and different request.
	- Unless the user reopens the browser and get a new request.
- Singleton
	- Session will never change.
	- For convenience.
	- Least secure.

### Logout
```
protected void btnLogout_Click(object sender, EventArgs e)
{
	// Clear Session
	Session.Clear;
	Session.Abandon();
	Session.RemoveAll();
	if (Request.Cookies["ASP.NET_SessionID"] != null)
	{
		// Empty the Cookie
		Response.Cookies["ASP.NET_SessionID"].value = string.Empty;
		Response.Cookies["ASP.NET_"]
	}
}
```