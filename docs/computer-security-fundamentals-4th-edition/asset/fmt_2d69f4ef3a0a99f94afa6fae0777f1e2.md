
All relational databases use SQL, which includes commands such as `SELECT`, `UPDATE`, `DELETE`, `INSERT`, and `WHERE`. At least the basic queries are very easy to understand and interpret.

Most basic SQL injection works like this: Many websites/applications have a page where a user enters a username and password. That username and password will have to be checked against some database to see if they are valid. Regardless of the type of database (Oracle, SQL Server, MySQL), all databases speak SQL. SQL looks and functions a great deal like English. For example, to check a username and password, you might want to query the database to see if there is any entry in the users table that matches the username and password that was entered. If there is such an entry, you have a match. The SQL statement to ask this might look something like this:

[Click here to view code image](Images/ch06_images.xhtml#p163pro01)

```
`SELECT * FROM tblUsers WHERE USERNAME = 'jdoe' AND PASSWORD = 'letmein'`
```

The problem with this query is that, although it is valid SQL, it hard codes the username and password. For a real website, you would have to take whatever the user entered into the username field and password field and check that. This can be easily done (regardless of what programming or scripting language the website is programmed in). It would look something like this:

[Click here to view code image](Images/ch06_images.xhtml#p164pro01)

```
`SELECT * FROM tblUsers WHERE USERNAME = '" + txtUsername.Text + ' AND PASSWORD = '" +
txtPassword.Text +"'"
```

If you enter username `'jdoe'` and password `'letmein'`, this code produces the following SQL command:

[Click here to view code image](Images/ch06_images.xhtml#p164pro02)

```
SELECT * FROM tblUsers WHERE USERNAME = 'jdoe' AND PASSWORD = 'letmein'
```

Now if there is a username jdoe in tblUsers, and the password for it is letmein, then this user will be logged on. If not, then an error will occur.

SQL injection works by putting some SQL into the username and password block that is always true. For example, suppose you enter `'OR X=X'` into the username and password boxes. This will cause the program to create this query:

[Click here to view code image](Images/ch06_images.xhtml#p164pro03)

```
SELECT * FROM tblUsers WHERE USERNAME = ''OR X=X' AND PASSWORD = ''OR X=X'
```

Notice that you start with a single quotation mark (`'`) before the `OR X=X`. This closes the open quote the attacker knows must be in the code. And if you see `''`, that essentially is a blank or null, and it tells the database to log you in if the username is blank, or if `X=X`, and if the password is blank, or if `X=X`. If you think about this for a second, you will see that X always equals X, so this will always be true.

There is no significance to `'OR X=X'`; it is simply a statement that will always be true. Attackers try other similar statements, such as the following:

```
' or 'a' ='a
' or '1' ='1
' or (1=1)
```

The example given here is the most basic version of SQL injection, but this is the most common. You can do far more with SQL injection. The attacker is limited only by her knowledge of SQL and the target database system.

The defense against this attack is to filter all user input before processing it. This process, often referred to as *input validation*, prevents an attacker from entering SQL commands rather than a username and password. Unfortunately, many sites do not filter user input and are still vulnerable to SQL injection attacks.

Remember that earlier in the text when we first, briefly, mentioned SQL injection, it was suggested that filtering input could prevent such an attack. For example, a programmer creating a website should write the code to first check for any common SQL injection symbols such as the single quote (`'`), percent sign (`%`), equal sign (`=`), or ampersand (`&`), and if those are found, stop processing and log an error. This would prevent many SQL injection attacks. There are methods to circumvent these security measures, but implementing them would, nonetheless, stop many SQL injection attacks.

#### Cross-Site Scripting

With *cross-site scripting*, an attacker injects client-side scripts into web pages viewed by other users. The key is that the attacker enters scripts into an area that other users interact with. When users go to that part of the site, the attacker’s script, rather than the intended website functionality, is executed. For example, say that a shopping site allows users to review products. Rather than typing in a review, an attacker might type in JavaScript that redirects the user to a phishing website. When another user views that “review,” the script executes and takes the user to the new site. Again, such attacks can be prevented by simply filtering all user input. As of this writing, all the major online shopping portals, such as Amazon.com, do filter input and are not susceptible to this attack. However, many smaller sites are still susceptible to cross-site scripting.

Cross-site scripting and SQL injection both illustrate why it is critical that all IT personnel, not just security administrators, be familiar with security. If more web developers were more familiar with security, these two attacks would not be widespread.

#### Cross-Site Request Forgery

*Cross-site request forgery* could be viewed as the other side of cross-site scripting. Whereas cross-site scripting attacks the user, based on the user’s trust of a website, cross-site request forgery attacks the website, based on the site’s trust of a user. The trusted user, who is authenticated to the website, is tricked into sending requests to the website.

#### Directory Traversal

*Directory traversal* allows attackers to access restricted directories—including those containing application source code, configuration files, and critical system files—and execute commands outside the web server’s root directory.

Attackers can manipulate variables that reference files with “dot-dot-slash (../)” sequences and its variations, as in these examples:

[http://www.example.com/process.aspx=../../../../some](http://www.example.com/process.aspx=../../../../some) dir/some file

[http://www.example.com/../../../../some](http://www.example.com/../../../../some) dir/some file

#### Cookie Poisoning

Many web applications use cookies in order to save information (user ID, timestamp, and so on) on the client’s machine. For example, when a user logs in to a site, a login web script may validate his username and password and set a cookie with his numerical identifier.

When the user checks his preferences later, another web script (say, preferences.asp) retrieves the cookie and displays the user information records of the corresponding user. Because cookies are not always encrypted, they can be modified; an attack that includes this type of modification is called *cookie poisoning*. In fact, JavaScript can modify, write, or read a cookie. So this type of attack can be combined with cross-site scripting.

#### URL Hijacking

*URL hijacking*, also called *typosquatting*, involves a fake URL that is very close to a real one. For example, my website is [www.Chuckeasttom.com](http://www.Chuckeasttom.com). Someone might set up the site [www.Chuckeastom.com](http://www.Chuckeastom.com), with only one *t* in the last name.

#### Wireless Attacks

A number of wireless attacks are commonly used. For example, with the *evil twin attack*, a rogue wireless access point (WAP) is set up that has the same SSID as one of your legitimate access points. That rogue WAP might be used to initiate a denial of service attack on your legitimate access point, making it unable to respond to users, so they are redirected to the evil twin.
