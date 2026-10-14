
## Custom Applications

Written by a firm’s programmers
Not likely to be well trained in secure coding

## The Key Principle

Never trust user input
Filter user input for inappropriate content

## Buffer Overflow Attacks

In some languages, specific actions are needed
In other languages, not a major problem

## Login Screen Bypass Attacks

Website user gets to a login screen
Instead of logging in, enters a URL for a page that should only be accessible to authorized users

## Cross-Site Scripting (XSS) Attacks

One user’s input can go to another user’s webpage
An example

Usually caused if a website sends back information sent to it without checking for data type, scripts, etc.

Example: If you type your username, it may include something like “Hello, username” in the webpage it sends you

Example of an XSS attack

Attacker sends the intended victim an e-mail message with a link to a legitimate site
However, the link includes a script that is not visible in the browser window because it is beyond the end of the window
The intended victim clicks on the link and is taken to the legitimate webpage
The URL’s script is sent to the webserver with the HTTP GET command to retrieve the legitimate webpage
The webserver sends back a webpage including the script
The script is invisible to the user (browsers do not display scripts)
But the script executes
The script may exploit a vulnerability in the browser or another part of the user’s software

Many other examples exist

### Figure 8-6 Securing Custom Applications (Study Figure)

### CROSS-SITE SCRIPTING ATTACKS
Another danger of website programming is accidentally allowing **cross-site scripting (XSS)**, in which one user’s input can appear on the page of another user. This is a danger in any webpage that reflects back a user’s input. For instance, reflection exists if you type a username and the next webpage contains “Hello, username.”

Consider the following example. The attacker sends the intended victim an e-mail message. The message contains a link to a legitimate website that does reflection. The link is long and extends past the URL window. In the part that the user cannot see because it is beyond the URL window, the URL has a script. When the user clicks on the URL, the GET request including the script goes to the legitimate website. The legitimate website reflects back legitimate information plus the script. The script will execute without user intervention. If the intended victim’s browser has the vulnerability that the script is designed to exploit, the intended victim becomes an actual victim.

## SQL Injection Attacks

- For database access
- Programmer expects an input value—a text string, number, etc.
  - May use it as part of a SQL query or operation against the database
  - Say to accept a last name as input and return the person's telephone number
- Attacker enters an unexpected string
  - For example, a last name followed by a full SQL query string
  - The program may execute both the telephone number lookup command and the extra SQL query
  - This may look up information that should not be available to the attacker
  - It may even delete an entire table
- Attack methods using SQL injection
  - In-band, out-of-band, and inferential SQL injection
  - Error-based inference
  - Blind SQL injection
- Preventing SQL injection
  - Parameterization
  - Sanitizing input
  - Stored procedures
- There are many other SQL injection attacks
- Must Require Strong Secure Programming Training
  - General principles
  - Programming-language-specific information
  - Application-specific threats and countermeasures

### Figure 8-7 SQL Injection (Study Figure)

This is only one example of an XSS attack. Any time a webpage reflects user input, an XSS attack is likely to be possible. Consequently, HTML user input must be filtered to ensure that it does not contain scripts.

### SQL INJECTION ATTACKS
In the early days of the Internet, most websites consisted of linked static HTML pages. Over time, pages became dynamic and were linked to back-end databases on servers. Web servers could give users access to password-protected data and serve customized webpages. This was a tremendous improvement over static pages. However, it also made servers and databases vulnerable to new types of attacks.

SQL injection is an attack that involves sending modified SQL statements to a web application that will, in turn, modify a database. Attackers can send unexpected input through their web browser that will enable them to read from, write to, and even delete entire databases. SQL injection can even be used to execute commands on the server. SQL injection is a common attack method for many of the high-profile attacks seen in the news.

Structured Query Language In order to understand how SQL injection works, you need to first have a general idea of what SQL is and how it interacts with databases. Structured Query Language (SQL) is a computer language used to access, query, and manage databases. SQL statements use clauses (such as SELECT, UPDATE, WHERE) to specify which data is being accessed and how it is being manipulated.

A SQL query is one of the most common SQL statements. It uses the SELECT clause. For example, suppose you are looking for a new car. You want a red car in a specific price range. In your mind you might think, “Select from this car lot all of the cars where the color is red and order them by price.” This might sound awkward, but all of the elements for a SQL query are present. Below is how this would look if it were written as a SQL statement.

```sql
SELECT * FROM Cars WHERE
color='red' ORDER BY price;
```

In this case, the SQL query retrieved information from a database containing information about cars. The table was named Cars, the column name was color, it returned information about all red cars, and it ordered the results based on values from the price column.

> ***Warning***: SQL injection can cause tremendous damage and harm. It is illegal to do on other systems, and you will be prosecuted. Do not use SQL injection on any system without permission. This is only for informational purposes.

## Passing SQL Statements

Typically, users are not allowed to submit their own SQL statements through webpages. This would be too difficult for users. It would also give them too much control over the database. Users usually select values from controls such as drop-down lists, combo boxes, or check boxes. They can also enter values such as a username or a password. These values are then sent to the webserver and web application (middleware) and eventually passed to the database.

The middleware server is responsible for accepting values passed from users and formatting the SQL statements. However, using SQL injection it is possible to send malformed input that can alter the statement created by the web application. As shown in Figure 8-8, the altered SQL statement is then sent to the database. The subsequent results are sent directly back to the user.

In the example below, you will see how values from a login screen (username and password) are entered and passed to the web application correctly. You’ll then see an example of how SQL injection could be used maliciously. SQL statements are usually written on a single line. To make the statements easier to read, the clauses have been placed on separate lines.

## Normal SQL Statements

Login screens require users to enter a username and password. These values are then passed to the web application and checked against values in the database. The SQL statement below shows how these parameters might be passed to a database for a legitimate login shown in Figure 8-9.

### Figure 8-8 Simplified SQL Injection Path

![](img/073342643701cc54eb7875c41ab92ef2_404_0.png)

```sql
SELECT * FROM Users WHERE
    username='boyle02' AND
    password='12345678';
```

Both the username (boyle02) and password (12345678) are **strings** that can include letters, numbers, and characters. They are both enclosed by single quotes, and the SQL statement ends with a semicolon.

### Malformed SQL Statements
In the SQL statement below, the password (12345678) is replaced with text (whatever' or 1=1--) as shown in Figure 8-10. This will alter how the SQL query is interpreted. Note that the additional single quote after the word “whatever” encloses the password. Since the actual password (12345678) is not “whatever” the login should fail. However, the additional parameters will ensure that the login succeeds.

The rest of the injected SQL statement is processed normally. The logical operator “or” is used to create a two-part WHERE clause. The first part of the clause will return a false value for the WHERE clause. The second part of the clause, 1=1, will always return a true value. This guarantees that the login will succeed.

```sql
SELECT * FROM Users WHERE
    username='boyle02' AND
    password='whatever' or 1=1--';
```

### Attack Methods Using SQL Injection
SQL injection can be used in several different ways. **In-band** SQL injection extracts data directly from the database and displays it in a web browser. **Out-of-band** SQL injection uses malformed statements to extract data through a different application such as e-mail. **Inferential** SQL injection doesn’t necessarily extract data from the database. Rather, information *about* the database is gathered from responses to malformed SQL statements.

**Error-based inference** makes assumptions about the underlying database based on error messages received after a query. The database will report different errors depending on how the SQL statement was interpreted. Sometimes error-based inference is not possible because the application developer either prevents detailed error messages from being returned or returns a single generic error page. In this case, blind SQL injection must be used.

**Blind SQL injection** uses a series of SQL statements that produce different responses based on true/false questions or timed responses. For example, a savvy developer may require a single generic error message be sent for multiple different errors. This would make error-based inference difficult.

Using blind SQL injection, an attacker could create a SQL statement that would take much longer to process (i.e., perform a trivial task a million times) if it were *successfully* executed. Failed SQL statements would return the error page almost immediately. Successful SQL statements would return the error page after being delayed for, say, 10 seconds.

### Preventing SQL Injection
Application developers can minimize the threat of a SQL injection attack by using parameterized queries with bound parameters and sanitizing input. *Parameterizing* the query using bound parameters treats input as data only, not as part of the SQL statement. The input received from users is kept separate from the SQL statement and is not parsed.

*Sanitizing* the input from users involves removing all characters that may be used in SQL injection. This can be problematic because these characters are often used as input. For example, many foreign names use apostrophes and dashes (O’Connor, D’Angelo, Van’Campen, Al-Kurd, etc.). Applications may also require the use of characters such as “&” or “$” to work properly.

Additionally, limiting the permissions required to run the web application and using *stored procedures* can help stop SQL injection attacks.

![](img/073342643701cc54eb7875c41ab92ef2_405_0.png)

![](img/073342643701cc54eb7875c41ab92ef2_405_1.png)
