
## Usability Testing

Cast your mind back to the sample functional testing worksheet shown in Table 20-1. You allocated tasks to your testers such as “Open the login page by clicking the login link on the navigation.”

A similar task in usability testing would be simply phrased “Log in to the system.” The purpose is quite different, of course; hence, the very different phrasing. Usability testing does not concern itself with whether things work. This is established during functional testing. Rather, it asks how effectively or easily the user can perform the task in question.

Perhaps uniquely in software testing, usability testing rarely involves questions put directly to the test subjects. Instead, observation is the key.

When instructed to, for example, “Log in to the system,” the user will be observed (either in person or remotely). It is the user’s actions, or behavior, in achieving (or not achieving) the task required (which are only in part quantifiable in figures) that are of interest.

For example, you may want to attempt to answer the following questions:

- Where does the user physically look for the login link? Is it where you placed it or somewhere else? (Note that the position of a user’s cursor on-screen is often a clue to where the user is looking.)
- What sort of delay is there between when the login screen loads and the user starts typing his or her username?
- Does the user visit any other pages in error prior to finding the login page?

The answers to these questions will provide you with a good indication of the usability of your application. Admittedly, it can be difficult to quantify such research into figures, however.

Usability testing and the useful metrics it can supply is a huge topic in and of itself, and outside the scope of this chapter. More information on the various approaches available can be found on the excellent site www.useit.com, run by Jakob Nielsen.

## Fault Tracking

The testing you carry out using the techniques previously described will inevitably lead to observations, such as the following:

- Functional testing has shown that the recipient address is not correctly copied into the new message when replying to an existing message.
- Load testing has shown that the system does not respond in a sufficiently timely manner to requests made at 530 simultaneous sessions.
- Usability testing has shown that people expect the Previous and Next buttons in the Mailbox view to be at the top of the page, not the bottom.

These observations are relatively useless without the tabulation of corresponding action points. For the issues outlined previously, you might raise action points as follows:

- Ensure that when replying to a message, the recipient is automatically set to be the sender of the message being replied to.
- When 530 sessions are active, divert additional users to a “service unavailable” page explaining that the server is not able to process their requests at this time.
- Move the Previous and Next buttons in the Mailbox view to the top of the page.

These actions are all simple enough for a small project, but on a larger project you may have hundreds, or even thousands, of action points (such as bugs that need fixing and tweaks for fine tuning). How do you keep track?

It’s certainly possible to use the well-known default solution of any office worker thrust without warning into the world of project management — that of Microsoft Excel. It certainly gives you a quick-and-dirty mechanism for keeping track of project fault reports and their status, in the form of a color-coded table updated on a regular basis by all participating on the project.

However, its limitations will soon become clear. No Web-based access means that users must be in the same office where that spreadsheet resides on a local file server. No multiple-user access means that only one user can update the spreadsheet at a time. An onus on those using it to check it and update it frequently and regularly (with no prospect of notifications when issues requiring their attention become prescient) means that issues often go unchecked, even when urgent.

That’s where a purpose-built solution can provide an effective alternative.

## Effective Fault Management Using Mantis

This section takes a look at a fault-management system known as Mantis, a free package currently available from www.mantisbt.org.

The purpose of Mantis is to enable you to effectively keep tabs on all faults and defects in your projects, assign them to developers for resolution, and enable developers to pass comments on them where appropriate.

Mantis is a Web-based application written in PHP (what else?) that typically functions as an extranet. Whether you choose to open it up for access to your clients is entirely up to you. When working with smaller clients, this can often be beneficial because it enables them to feel part of the QA process. Mantis supports multiple users, each with his or her own access levels and rights, so you can offer different access to yourself and, say, your developers.

Many other fault-management systems exist, of course. This discussion examines Mantis specifically because it is freely available, easy to use, and written in PHP. This means that you could, in theory, modify and extend it to better suit your needs if so required.

### Installing Mantis

Download the Mantis installation archive from its Web site and unpack it in the usual manner:

```
tar -xzvf mantis-1.1.2.tar.gz
```

This will create a directory called mantis-1.1.2 containing all the source and configuration files for Mantis. You should have a VirtualHost in Apache's httpd.conf configuration file pointing to this location as follows:

```
<VirtualHost 192.168.168.2>
    ServerAdmin you@example.com
    ServerName mantis.example.com
    CustomLog /home/production/logfile_mantis common
    ErrorLog /home/production/errlog_mantis
    DocumentRoot /home/production/public_html/mantis-1.1.2
</VirtualHost>
```

If you are using a Web server other than Apache, you should set up a virtual server to support Mantis in the manner in which you are accustomed.

### Configuring Mantis for the First Time

Previous versions of Mantis have supported only MySQL. As you have read throughout this book, the authors generally favor PostgreSQL because it provides a genuinely free, open source, and more feature-rich alternative, closer to its commercial enterprise counterparts such as Oracle, at the expense of some loss of performance and, of course, wider support.

Mercifully, in the more recent versions of Mantis, PostgreSQL has been equally well supported. Indeed, it is the use of a database abstraction layer (the likes of which was advocated back in Chapter 6) that has enabled the developers of Mantis to bow to popular demand and add support for PostgreSQL out of the box.

Open your Web browser and point it to the virtual host you set up in the previous section. You should see a screen like the one shown in Figure 20-1 — a “one time run” installation screen. Note that the URL in the browser window has been partially obscured for reasons of security.

## Part III: A Real-World Case Study

![](img/a1b732997d9cb194dceec0570dc79710_550_0.png)

Figure 20-1: Mantis installation

As you can see from Figure 20-1, Mantis wants to know the details for your database. Before you proceed, you must create an empty database in PostgreSQL, as well as a user (with a password) that Mantis can use.

From your shell, use the following syntax to do just that:

```
root@gdmsrv02:~# /usr/local/pgsql/bin/createuser -P mantis
Enter password for new role:
Enter it again:
Shall the new role be a superuser? (y/n) n
Shall the new role be allowed to create databases? (y/n) n
Shall the new role be allowed to create more new roles? (y/n) n
```

Don't forget to make a note of the password you've chosen. Next, create the empty database as follows:

```
root@dmsrv02:~# /usr/local/pgsql/bin/createdb mantis
```

You can now point the Mantis installation screen (still open in your Web browser, it is hoped) at the database you just made and click Install/Upgrade Database.

The installation screen should tell you that all was successful, and provide a link for you to “continue” to log in to Mantis for the first time.

### Logging in As Administrator

Fire up your Web browser and point it at the virtual host you created earlier. You should see a login screen similar to what is shown in Figure 20-2. Again, the full URL has been blanked out for security.

![](img/a1b732997d9cb194dceec0570dc79710_551_0.png)

Figure 20-2: Login message
