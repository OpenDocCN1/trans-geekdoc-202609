# # Man-in-the-middle (MitM)

![](bbox=[0.275, 0.11, 0.9, 0.3])

A man-in-the-middle attack (now also sometimes referred to as an on-path attack) is where an attacker eavesdrops on communications between two systems.
This can result in data breaches, or data alteration, without the knowledge of the original parties involved.

# ## Phishing

Phishing is when a victim receives, and responds to, a seemingly legitimate message (such as an email) that has the aim of deceiving the victim into providing sensitive information, such as login credentials or bank account details. This can result in unauthorized access to other systems, identity theft and financial crimes.

# ## SQL injection

An SQL injection is where an attacker exploits vulnerabilities in the way an application or website has been designed to work with its database. It relies upon the programmers not applying sufficient validation checks to the user inputs, so that the application can make unintended changes to the underlying database. This can result in unauthorized viewing of user lists (and their passwords), deletion of data or granting administrative control of the database to the attacker.

To understand how the SQL injection attack works, consider the impact the following Python would have to the SQL statement if executed on a database:

```
first_name = "Robert"; DROP TABLE Students; --"
family_name = "Doe"
sql = "INSERT INTO Students VALUES ('" + first_name + "', '" + family_name + "')";
```

The SQL string now actually contains three different SQL commands:
1 INSERT INTO Students VALUES ('Robert');
2 DROP TABLE Students;
3 --', 'Doe');