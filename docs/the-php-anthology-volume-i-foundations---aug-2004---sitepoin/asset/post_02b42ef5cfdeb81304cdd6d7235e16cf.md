
## Appendix B: Hosting Provider Checklist

PHP, and, more generally, the LAMP combination of Linux, Apache, MySQL and PHP/Perl/Python, is widely available via literally thousands of Web hosts at very affordable prices. You can easily get quality Web hosting that will suit 90% of your needs for under $10 a month per site. That said, all PHP installations are not created equal, and depend largely on the configuration settings defined in php.ini as well as the extensions the host has installed for you. There are also a number of general issues relating to the amount of control you're given over your own environment, and these are important if you don't want big trouble later on.

This is a summary of the key issues you should investigate before paying for a hosting service. Contact potential providers and have them respond on each of these points. Follow up by asking for opinions from other people who know/have used the service in question. There are many online forums where you'll find people who are able to offer advice. Be aware, though, that the ratio of "knowledgeable" to "ignorant" is stacked highly in favor of ignorance; gem up on technical detail so you're able to verify that the answers you were given were actually well-informed.

Some of the points I've provided here may seem a little extreme, but once you've been around the block a few times, you'll probably want to get value for your money, rather than spending your Saturday mornings fixing the problems your host made for you on Friday night.

### General Issues

- [ ] Require Linux and Apache (1.3)

From the point of view of performance and reliability, this is the best combination. Avoid any host using Apache 2.x (it's not yet completely stable with PHP). Ask for details of the Linux distribution. Although Red Hat and Suse are popular, you may find hosts using Debian (or, better yet, Rock Linux) know more about what they're doing.

- [ ] Does the host provide you with SSH access to the server?

SSH gives you a secure connection to the server to perform tasks from the Linux command line or transfer files with SCP (secure copy). Avoid any host who allows you to use telnet (a fundamentally insecure way to connect to a server over the Internet). For Windows users, Putty[1] makes an excellent command line tool over SSH, while WinSCP[2] provides a secure file transfer mechanism using an SSH connection. Oh, and don't transfer files with ftp—it's as insecure as telnet.

[1] http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html
[2] http://winscp.sourceforge.net/eng/

### Is the host a reseller or do they maintain the server themselves?

Resellers can provide significant value if you need help at a basic technical level (if, for example, you call yourself a newbie), but they generally have the same level of control over the server as you. Going “straight to the source” means you won’t have to deal with delays when there are system problems, as you'll likely be dealing directly with those who maintain the server. The down side is that they tend to be less “newbie tolerant” so you may get answers—but not ones you can understand.

### To what degree does the host “overload” the server?

Many Web hosting companies create far more accounts on a server than the maximum for which the system is specified. The best metric is the uptime command (to which you require access); this will tell you the server load averages over 1, 5 and 15 minutes. Ideally, the server should never have load averages above 1. Obviously, the problem isn't as simple as this, but once you see your server hit averages in excess of 5, you'll begin to experience significant delays in your PHP-based applications.

### What is the hosting provider's policy on running scripts and programs from the command line?

MySQLDump is a very handy tool for backing up your database, but it's no good if you can't run it. Some hosts automatically kill any command line application that executes for longer than a given time.

### Does the host provide you access to cron, the Unix utility that allows you to schedule batch jobs?

If so, make sure the host allows command line scripts to be executed. Some hosts have taken to implementing cron so that it executes scripts via a Web URL. This is no use if the script in question uses the MySQLDump application to back up your database—a PHP script executed via Apache will typically run as a user, which will not have the correct permissions required for the job.

### PHP-Related Issues

- Can you see the output of phpinfo on the server you will actually be assigned to?

Some hosts may claim this is a security risk, but expert hosts know that security by obscurity is no substitute for _real_ security. The information provided by phpinfo is _not_ a security risk to hosting providers that know what they're doing, and have Linux, Apache, and firewalls correctly set up. What phpinfo tells you is the best way to confirm the facts.

- Is PHP installed as an Apache module (not the CGI variant)?

This provides much better performance.

- Is the Apache setting AllowOverride set to Options or All?

This will let you modify php.ini settings with .htaccess files.

- Is PHP Safe Mode disabled?

The safe_mode option in php.ini is, in theory, a way to make PHP secure, and prevent users from performing certain tasks or using certain functions that are security-sensitive. Safe Mode is nothing but a large headache if you're doing any serious work in PHP.

- Check the upgrade policy of your host.

Ask the host how much warning you will get before upgrades are performed. Check that they will provide you with a copy of the php.ini file they'll be using for the upgrade (before it happens). The number of hosts that, overnight, switch from register_globals = on to register_globals = off is considerable. Make sure you test your applications on your development system against the new version before the host performs the upgrade.

- Ask for a list of installed PHP extensions.

Confirm that these extensions match the requirements of your applications. Few hosts, for example, bother to provide the XSLT extension. Confirm also that the host guarantees all extensions will remain available between PHP upgrades.

- [ ] Will PHP be available for use from the command line?

If not, you might alternately require access to Perl or Python, or the ability to run shell scripts, if you're happy with those languages. Usually, running a serious Website will require that you have the ability to run routine batch jobs (with cron), for tasks like backups, mailing you the PHP error log, and so on.

- [ ] Last but not least, throw in one or two questions that will test your hosting providers' knowledge of PHP. Although it may not be their job to write PHP code, when you find yourself in the position of knowing a lot more about PHP than your host, the end result is depressing. It's important to have a host that understands your needs.

## Appendix C: Security Checklist

Given that online PHP applications are exposed to essentially anyone and everyone, security should be one of, if not _the_ top concern as you develop your applications. To some extent, the ease with which PHP applications can be developed is also one of its greatest weaknesses, in that, for beginners who aren't aware of the possible dangers, it's very easy to deploy an application for which the line of security resembles swiss cheese.

Make sure you're informed, and, if in any doubt, ask. The Open Web Application Security Project (OWASP)[1] is a corporate-sponsored community focused on raising awareness of Web security, and is an excellent source of information on potential dangers. They recently published a “Top 10” list of common security flaws in Web applications, the relevant points of which I’ve summarized here.

### The Top Security Vulnerabilities

- Unvalidated data

Never trust anything you get from a Web browser. The browser is completely outside of your control, and it's easy to fake values like the HTTP referrer. It's also easy to fake a hidden field in a form.

More importantly, when dealing with forms, for example, validate the data carefully. Use a “deny all, permit a little” policy. For example, if a registration form has a field for the user name, allow only alphabetical characters and perhaps the numbers 0–9, rather than simply rejecting particular special characters. Use regular expressions to limit data to exactly what you require. Packages like PEAR::QuickForm, as you saw in Chapter 9, provide built-in mechanisms for validating forms and do a lot to help cover weaknesses you might otherwise neglect.

Also, where things like include files are concerned, watch out for logic like this:

```
include($_GET['page']);
```

Make sure you check the value of `$_GET['page']` against a list of files your code is designed to include:

[1] http://www.owasp.org/
