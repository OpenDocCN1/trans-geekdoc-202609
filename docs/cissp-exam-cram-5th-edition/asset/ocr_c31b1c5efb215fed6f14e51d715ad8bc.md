mail order, supermarkets, and manufacturing. Programmers involved in database management use the ACID test when discussing whether a database management system has been properly designed to handle OLTP:

+   ▶ **Atomicity**: Results of a transaction are either all or nothing.
+   ▶ **Consistency**: Transactions are processed only if they meet system-defined integrity constraints.
+   ▶ **Isolation**: The results of a transaction are invisible to all other transactions until the original transaction is complete.
+   ▶ **Durability**: Once a transaction is complete, the results of the transaction are permanent.

# Database Vulnerabilities and Threats

Protecting databases is not an easy task. Database attacks are some of the most common attack vectors, and SQL injection has topped the OWASP list for more than 10 years. Many database security issues are directly attributed to poor development practices. As a security professional, you should understand the following common vulnerabilities and threats:

+   ▶ **SQL injection**: This type of attack, typically caused by unsanitized input, allows the attacker to inject a SQL query via the input data from the client to the application.
+   ▶ **Default, blank, or weak passwords**: Authentication credentials should be strong, and all weak and blank passwords removed.
+   ▶ **Extensive privileges**: The level of access provided should be only what’s needed to do the task. Administrator privileges should not be provided.
+   ▶ **Broken configuration management**: Active measurement of the environment is required to detect undocumented changes, which typically reduce security.
+   ▶ **Enabled features that are not needed**: It is important to remove, block, and disable all features that are not needed. Reducing the attack surface makes it harder for an attacker to succeed.