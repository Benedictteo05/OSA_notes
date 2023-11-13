### HTTP is Stateless
**HTTP is a stateless protocol**
- It follows a request/response pattern. 
	- i.e. User requests a resource and the web server responds with the requested resource.
- Information is not retained (pass on) from one request to another

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
	Session.add("ssuser", txtboxloginid.Text);
	or
	Session["ssuser"] = txtboxloginid.Txt;
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
- Session timeout value can be specified in the web.config file (.net Framework)
- It indicates the time (in minutes) that the session can be idle before it is abandoned
- Configure session timeout using `<sessionState>` attribute
- By default, session timeout is 20 minutes
- In the example below, the session will timeout in 1 minute in web.config
```
<system.web>
	<sessionState timeout="1"></sessionState>
</system.web>
```

**How is data stored in "Session"**
- InProc Mode
	- It is a default session mode and a value store in web server memory (IIS)
	- Session value stored when server starts and it ends when the server is restarted.
	- Limited to ONLY one server
- State Server Mode
	- In this mode,, session data is stored in separated server.
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
Response.Write()
```