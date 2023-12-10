### SQL Injection  (SQLi)
- Occurs when an attacker is able to manipulate SQL statements through data inputs of an application.
- Attackers can possibly modify SQL statement in a vulnerable application via forms or parameters.
- Impacts:
	1. Data loss or corruption, lack of accountability, or denial of access.
	2. May lead to gaining access to vulnerable system.

### In-band SQL injection (Simple SQLi)
- The same channel was used to launch the attack and obtain the result
- Most common  
### Inferential SQL injection (Blind SQLi)
- Attackers sends data payloads to the server and observes the response and behavior of the server to learn more about its structure. (data is not transferred from the website database to the attacker)