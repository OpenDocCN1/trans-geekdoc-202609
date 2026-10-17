
A logic bomb is software that lays dormant until some specific condition is met. That condition is usually a date and time. When the condition is met, the software does some malicious act, such as delete files, alter system configuration, or perhaps release a virus. In Chapter 5, “Malware,” we will examine logic bombs and other types of malware in detail.

## Compromising System Security

Next we will look at attacks that breach your system’s security. This activity is commonly referred to as hacking, though it is not the term hackers themselves use. We will delve into appropriate terminology in just a few pages; however, it should be noted at this point that cracking is the appropriate word for intruding into a system without permission, usually with malevolent intent. Any attack that is designed to breach your security, either via some operating system flaw or any other means, can be classified as cracking.

Essentially any technique to bypass security, crack passwords, breach Wi-Fi, or in any way actually gain access to the target network fits into this category. That makes this a very broad category indeed.

However, not all breaches involve technical exploits. In fact, some of the most successful breaches are entirely nontechnical. Social engineering is a technique for breaching a system’s security by exploiting human nature rather than technology. This was the path that the famous hacker Kevin Mitnick most often used. Social engineering uses standard con techniques to get users to give up the information needed to gain access to a target system. The way this method works is rather simple: The perpetrator gets preliminary information about a target organization and leverages it to obtain additional information from the system’s users.

Following is an example of social engineering in action. Armed with the name of a system administrator, you might call someone in the business’s accounting department and claim to be one of the company’s technical support personnel. Mentioning the system administrator’s name would help validate that claim, allowing you to ask questions in an attempt to ascertain more details about the system’s specifications. A savvy intruder might even get the accounting person to say a username and password. As you can see, the success of this method is based on how well the prospective intruder can manipulate people and actually has little to do with computer skills.

The growing popularity of wireless networks gave rise to new kinds of attacks. One such activity is war-driving. This type of attack is an offshoot of war-dialing. With war-dialing, a hacker sets up a computer to call phone numbers in sequence until another computer answers to try to gain entry to its system. War-driving is much the same concept, applied to locating vulnerable wireless networks. In this scenario, the hacker simply drives around trying to locate wireless networks. Many people forget that their wireless network signal often extends as much as 100 feet (thus, past walls). At the 2004 DEF CON convention for hackers, there was a war-driving contest where contestants drove around the city trying to locate as many vulnerable wireless networks as they could. These sorts of contests are now common at various hacking conventions. (DEF CON is the largest and oldest hacking conference in the world.)

Recent technological innovations have introduced new variations of war driving/dialing. Now we have war flying. The attacker uses a small private drone equipped with Wi-Fi sniffing and cracking software, flies the drone in the area of interest, and attempts to gain access to wireless networks.

Of course, Wi-Fi hacking is only one sort of breach. Password cracking tools are now commonly available on the Internet. We will examine some of these later in this book. There are also exploits of software vulnerabilities that allow one to gain access to the target computer.

## DoS Attacks

In a DoS, the attacker does not actually access the system. Rather, this person simply blocks access from legitimate users. One common way to prevent legitimate service is to flood the targeted system with so many false connection requests that the system cannot respond to legitimate requests. DoS is a very common attack because it is so easy.

In recent years a proliferation of DoS tools have been available on the Internet. One of the most common such tools is the Low Orbit Ion Cannon (LOIC). Because these tools can be downloaded for free from the Internet, anyone can execute a DoS attack, even without technical skill.

We also have variations, such as the DDoS attack. This attack uses multiple machines to attack the target. Given that many modern websites are hosted in network clusters or even in clouds, it is very difficult for a single attacking machine to generate enough traffic to take down a web server. But a network of hundreds or even thousands of computers certainly can. We will explore DoS and DDoS attacks in more detail in Chapter 4, “Denial of Service Attacks.”

By their nature, web servers have to allow communications. Oftentimes, websites allow users to interact with the website. Any part of a website that allows users to interact with the website is also a potential point for attempting a web-based attack. SQL injections involve entering SQL (Structured Query Language) commands into login forms (username and password text fields) in an attempt to trick the server into executing those commands. The most common purpose is to force the server to log the attacker on, even though the attacker does not have a legitimate username and password. While SQL injection is just one type of web attack, it is the most common.

SQL injection is still quite common, though it has been known for many years. Unfortunately, not enough web developers take the appropriate steps to remediate the vulnerabilities that make such an attack possible. Given the prevalence of this type of attack, it warrants a bit more detailed description.

Consider one of the simplest forms of SQL injection, used to bypass login screens. The website was developed in some web programming language, such as PHP or ASP.NET. The database is most likely a basic relational database such as Oracle, SQL Server, MySQL, or PostgreSQL. SQL is used to communicate with the database, so we need to put SQL statements into the web page that was written in some programming language. That will allow us to query the database and see if the username and password are valid.

SQL is relatively easy to understand; in fact, it looks a lot like English. There are commands like SELECT to get data, INSERT to put data in, and UPDATE to change data. In order to log in to a website, the web page has to query a database table to see if that username and password are correct. The general structure of SQL is like this:

```
select column1, column2 from tablename
```

```
select * from tablename; Conditions: select columns from tablename where condition;
```

For example:

```
SELECT * FROM tblUsers WHERE USERNAME = 'jsmith'
```

This statement retrieves all the columns or fields from a table named tblUsers where the username is jsmith.

The problem arises when we try to put SQL statements into our web page. Recall that the web page was written in some web language such as PHP or ASP.NET. If you just place SQL statements directly in the web page code, an error will be generated. The SQL statements in the programming code for the website have to use quotation marks to separate the SQL code from the programming code. A typical SQL statement might look something like this:

Click here to view code image

```
"SELECT * FROM tblUsers WHERE USERNAME = '" + txtUsername.Text + "' AND PASSWORD = '" + txtPassword.Text + "'";
```

If you enter username 'jdoe' and the password 'password', this code produces this SQL command:

Click here to view code image

```
SELECT * FROM tblUsers WHERE USERNAME = 'jdoe' AND PASSWORD = 'password'
```

This is fairly easy to understand even for nonprogrammers. And it is effective. If there is a match in the database, that means the username and password match. If no records are returned from the database, that means there was no match, and this is not a valid login.

The most basic form of SQL injection seeks to subvert this process. The idea is to create a statement that will always be true. For example, instead of putting an actual username and password into the appropriate text fields, the attacker will enter ' or '1' = '1' into the username and password boxes. This will cause the program to create this query:

Click here to view code image

```
SELECT * FROM tblUsers WHERE USERNAME = '' or '1' = '1' AND PASSWORD = '' or '1' = '1'.
```

So you are telling the database and application to return all records where username and password are blank or if 1 = 1. It is highly unlikely that the username and password are blank. But I am certain that 1 = 1 always. Any true statement can be substituted. Examples are a = a and bob = bob.

The tragedy of this attack is that it is so easy to prevent. If the web programmer would simply filter all input prior to processing it, then this type of SQL injection would be impossible. Filtering means that before any user input is processed, the web page programming code looks through that code for common SQL injection symbols, scripting symbols, and similar items. It is true that each year fewer and fewer websites are susceptible to these attacks. However, there are still many sites that are vulnerable. SQL injection is still one of the top vulnerabilities found in websites according to OWASP (The Open Web Application Security Project). Subsequent chapters provide more coverage of most of these attacks, including tools used for them.

## Cross-Site Scripting

Cross-site scripting is a type of attack that is closely related to SQL injection. It involves entering data other than what was intended, and its success depends on the web programmer not filtering input. The perpetrator finds some area of a website that allows users to type in text that other users will see and then instead injects client-side script into those fields.

> **Note**
>
> Before I describe this particular crime, I would point out that the major online retailers such as eBay and Amazon.com are not susceptible to this attack; they do filter user input.

To better understand this process, let’s look at a hypothetical scenario. Let’s assume that ABC Online Book Sales has a website. In addition to shopping, users can have accounts with credit cards stored, post reviews, and more. The attacker first sets up an alternate web page that looks as close to the real one as possible. Then the attacker goes to the real ABC Online Book Sales website and finds a rather popular book. He goes to the review section, but instead of typing in a review, he types in this:

Click here to view code image

```
<script> window.location = "http://www.fakesite.com"; </script>
```

Now when users go to that book, this script will redirect them to the fake site, which looks a great deal like the real one. The attacker then can have the website tell the user that his session has
