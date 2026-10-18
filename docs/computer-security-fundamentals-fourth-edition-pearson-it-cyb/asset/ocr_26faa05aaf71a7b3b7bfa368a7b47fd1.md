```
SELECT * FROM tblUsers WHERE USERNAME = 'jdoe' AND PASSWORD = 'letmein'
```

Now if there is a username jdoe in tblUsers, and the password for it is letmein, then this user will be logged on. If not, then an error will occur.

SQL injection works by putting some SQL into the username and password block that is always true. For example, suppose you enter 'OR X=X' into the username and password boxes. This will cause the program to create this query:

Click here to view code image

```
SELECT * FROM tblUsers WHERE USERNAME = '' OR X=X' AND PASSWORD = '' OR X:
```

Notice that you start with a single quotation mark (') before the OR X=X. This closes the open quote the attacker knows must be in the code. And if you see '', that essentially is a blank or null, and it tells the database to log you in if the username is blank, or if X=X, and if the password is blank, or if X=X. If you think about this for a second, you will see that X always equals X, so this will always be true.

There is no significance to 'OR X=X'; it is simply a statement that will always be true. Attackers try other similar statements, such as the following:

+   ' or 'a' = 'a
+   ' or '1' = '1
+   ' or (1=1)'

The example given here is the most basic version of SQL injection, but this is the most common. You can do far more with SQL injection. The attacker is limited only by her knowledge of SQL and the target database system.

The defense against this attack is to filter all user input before processing it. This process, often referred to as input validation, prevents an attacker from entering SQL commands rather than a username and password. Unfortunately, many sites do not filter user input and are still vulnerable to SQL injection attacks.

Remember that earlier in the text when we first, briefly, mentioned SQL injection, it was suggested that filtering input could prevent such an attack. For example, a programmer creating a website should write the code to first check for any common SQL injection symbols such as the single quote ('), percent sign (%), equal sign (=), or ampersand (&), and if those are found, stop processing and log an error. This would prevent many SQL injection attacks. There are methods to circumvent these security measures, but implementing them would, nonetheless, stop many SQL injection attacks.



With cross-site scripting, an attacker injects client-side scripts into web pages viewed by other users. The key is that the attacker enters scripts into an area that other users interact with. When users go to that part of the site, the attacker's script, rather than the intended website functionality, is executed. For example, say that a shopping site allows users to review products. Rather than typing in a review, an attacker might type in JavaScript that redirects the user to a phishing website. When another user views that "review," the script executes and takes the user to the new site. Again, such attacks can be prevented by simply filtering all user input. As of this writing, all the major online shopping portals, such as Amazon.com, do filter input and are not susceptible to this attack. However, many smaller sites are still susceptible to cross-site scripting.

Cross-site scripting and SQL injection both illustrate why it is critical that all IT personnel, not just security administrators, be familiar with security. If more web developers were more familiar with security, these two attacks would not be widespread.



Cross-site request forgery could be viewed as the other side of cross-site scripting. Whereas cross-site scripting attacks the user, based on the user's trust of a website, cross-site request forgery attacks the website, based on the site's trust of a user. The trusted user, who is authenticated to the