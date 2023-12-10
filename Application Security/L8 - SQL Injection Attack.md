### SQL Injection  (SQLi)
- Occurs when an attacker is able to manipulate SQL statements through data inputs of an application.
- Attackers can possibly modify SQL statement in a vulnerable application via forms or parameters.
- Impacts:
	1. Data loss or corruption, lack of accountability, or denial of access.
	2. May lead to gaining access to vulnerable system.

### In-band SQL injection (Simple SQLi)
- Most common SQL injection 
- The same channel was used to launch the attack and obtain the result
- Error-based & Union-based

### Error-based SQLi
- An error-based SQL injection technique relies on error message thrown by the database server to obtain information about the structure of the database.

### Union-based SQLi
- Leverage the UNION SQL operator to combine the results of two or more SELECT statements into a single result, which is then returned as part of the HTTP response.

### Inferential SQL injection (Blind SQLi)
- Attackers sends data payloads to the server and observes the response and behavior of the server to learn more about its structure. (data is not transferred from the website database to the attacker)
- Attackers are not able to see the results of an attack as no data is transferred via the web application (Blind SQLi)
- Boolean-based blind SQLi and Time-based blind SQLi

### Boolean-based blind SQLi
- Relies on sending an SQL query to the database, which forces the application to return a TRUE or FALSE result.

### Time-based blind SQLi
- Forces the database to wait for a specified amount of time (in seconds) before responding. The response time will indicate to the attacker whether the result of the query is TRUE or FALSE.