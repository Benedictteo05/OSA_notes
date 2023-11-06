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


**Server**
- Session
	- Session is used to store information and identity. The server stores information using Session_id.
		- Session Ids are attractive to attackers because once obtained they can basically hijack user's identities.
	- Session State Variables are available across all pages, but only for a given session 
