# SQL Injection

Of course, cross-site scripting is not the only place where URL encoding is used. Anywhere you want to obscure text, you can URL-encode it. It makes it harder for regular users to know what is being done because they can't easily convert the hexadecimal values back to their ASCII equivalents. Many of the other attacks can be obscured or made successful through the use of URL encoding, and SQL injection is one of them.

SQL is the Structured Query Language, used to make programmatic requests of a relational database server. The server manages the storage, which will vary from one server type to another, but in order to get to the storage, either by inserting data or retrieving it, you would use the SQL programming language.

An SQL injection is an attack against the database server, ultimately, though it takes advantage of poor programming practices in the application code. As an injection attack, it happens when a malicious user sends in (injects) unexpected data through a web request. Sometimes, form data is passed directly into an SQL query from the application server to the database server to execute. If a fragment of legitimate SQL can be sent into a server where it is executed, the database could be altered or damaged. Also, data could be extracted or even have authentication bypassed.

Applications you are trying to attack with SQL injection must already have SQL in place to run a query necessary for the application to succeed. For example, perhaps you are browsing an electronic storefront and you are trying to find all Doctor Who action figures because you really want one of Jodie Whittaker, since you have all the others. You issue a search on the site for “jodie whittaker doll” in order to get the right results back. Behind the scenes, the application may have an SQL statement that reads

```
SELECT * FROM inventory_table WHERE description == '$searchstr';
```

What you have submitted (“jodie whittaker doll”) goes into the variable $searchstr. This means it's not as simple as just issuing your own query and expecting that to run. Instead, you need to find a way to get your query to work in the context of the existing one. One way to do that can be seen in Figure 12.2.

# FIGURE 12.2 SQL injection attack

![](bbox=[0.25, 0.673, 0.763, 0.933])