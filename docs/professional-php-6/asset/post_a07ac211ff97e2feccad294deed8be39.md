
local network, a second subnet has been introduced: 192.168.2.x instead of 192.168.1.x. Keeping subnets different enables you to configure virtual private network (VPN) access to your remote data center more easily, should you ever wish to do so. It's also a lot less confusing.

If your live production environment uses multiple servers in a load-balanced configuration, you would be wise to run your staging environment off a single server. After all, your staging environment is unlikely to attract the kinds of loads that warrant the use of multiple servers.

It may be prudent to protect your live staging environment with a username and password, because it is, strictly speaking, publicly accessible. It would be potentially disastrous if a member of the general public saw content that was, for example, subject to a press embargo. Imagine the fallout if people could check up on what Apple was about to unveil at their latest Worldwide Developer's Conference (WWDC) just by visiting `http://staging.apple.com`!

However, avoid using an `.htaccess` file to accomplish this because that file risks being accidentally replicated onto your production environment during deployment, which would expose your live environment to that same password protection.

Instead, you can add this layer of security directly into your Apache configuration file:

```
<VirtualHost 192.168.2.1:80>
    ServerName staging.widgets.com
    ServerAdmin ed@example.com
    CustomLog /home/widgets/logfile_wid-staging common
    ErrorLog /home/widgets/errlog_wid-staging
    DocumentRoot /home/widgets/public_html/staging/php
    <Directory /home/widgets/public_html/staging/php>
        AuthType Basic
        AuthName Staging
        AuthUserFile /home/widgets/.htpasswd
        Satisfy All
        Require valid-user
    </Directory>
</VirtualHost>
```

The .htpasswd file is created in the normal manner (that is, using `/usr/local/apache/bin/htpasswd`).

It's important to keep the location of the .htpasswd file outside the directory structure of your Web site. In this case, it's three folders up under `/home/widgets`. This ensures that the password file can't be retrieved by a simple HTTP request from a malicious intruder.

As an aside, it's worth remembering that this kind of basic authentication (as it is known) is not exactly industrial strength. If you have truly sensitive material on your live staging environment, you should consider using the Apache directives `Allow` and `Deny` to restrict by IP address, too.

## The Live Production Environment

Your live production environment provides the environment that the public sees — the live Web site itself. This may not be the general public if this is a closed system, but it is nonetheless the place for fully tested, fully approved, ratified code.

A typical Apache configuration might read as follows:

```
<VirtualHost 192.168.2.1:80>
	ServerName www.widgets.com
	ServerAdmin ed@example.com
	CustomLog /home/widgets/logfile_wid-live common
	ErrorLog /home/widgets/errorlog_wid-live
	DocumentRoot /home/widgets/public_html/live/php
</VirtualHost>
```

## Development Databases

Assuming that your application is database-driven, you must make a conscious decision about what instance of the database (that is, which physical server and which database on that server) should be used for each of your environments.

This is particularly pertinent considering that certain evolutions of code may require modifications to database schema that, if made against a production database still being driven by an older release of code, would surely cause errors.

With this in mind, consider the following strategy:

- Individual development environments (if used) should employ a locally hosted database, specific to that individual. For example, John Doe should use a database called `widgets-johndoe`.
- The master development environment should employ a locally hosted database (perhaps simply named `widgets-dev`), not specific to any individual developer, but reflecting the latest database schema required to support the very latest versions from your version control platform.
- The studio staging environment should employ a locally hosted database (perhaps simply named `widgets-stg`), not specific to any individual developer, but reflecting the latest database schema required to support the latest release-tagged versions from your version control platform.
- The live production environment should, naturally, use the live database server and the live database.
- The live staging environment should also use the live database so that when it’s being used by the client for testing and approval purposes, it provides an accurate reflection of how the live environment will behave once the changes are deployed.

Of course, with at least four databases in existence at any one time, keeping track of necessary changes to the database schema itself can be tricky.

Version control software is of little use here. Yes, it is possible to maintain a dump of the database structure in your repository, but simply retrieving this dump will not physically update the database schema when it is downloaded. Simply dropping and recreating the database is an option, but this will lose any test data stored therein. It is also difficult to use such a SQL "dump" file to determine differences in database schema when you're working on larger projects.

The best approach, therefore, is one of good communications. Version control can play an important part here. Create a folder called `db-changes` in your repository. Instructing your developers to add text files containing a series of `ALTER` statements whenever they make changes to the database schema will mean that any developer performing "get latest versions" will also receive a series of changes to make to his or her own database.

Such files can also be tagged as `release` so that those responsible for maintaining the master development and studio staging environments can ensure that both databases are kept up-to-date to the appropriate degree.

> Telling your application which database to use can result in awkward `switch` statements or, worse, hard-coded values that need changing by hand. There is another way, however. You doubtlessly have a file called `constants.php` (or similar) that dictates database IP address, database name, username, password, and so forth. By adapting this to consult the `$_SERVER[ "HTTP_HOST" ]` property, the database IP, name, username, and password can be conditionally and dynamically determined, and the correct database selected automatically, depending on the virtual server being used. That way, everyone can share the same constants file.

## The Deployment Workflow

Simply having these development environments does not automatically facilitate best practice deployment strategy. The workflow of source code is important, too.

You may find the diagram shown in Figure 21-1 useful for illustrating the source code flow, from deployment to live.

Start
Developers work on code on their own development environments, updating their database schema as and when required
Code is committed to version control repository
Code is automatically deployed to master development environment (MDE)
Are MDE Database Updates required?
Updates from version control repository are applied
Project Manager evaluates code on MDE for readiness
Is all code ready?
Tag relevant versions of code for 'release'
'Release' tagged code deployed to Studio Staging Environment (SSE)
Are SSE database updates required?
Updates from version control repository are applied
Project Manager evaluates code on SSE for readiness
Is all code ready?
Code deployed to Staging Live Environment (SLE)
Are live database updates required?
Updates from version control repository are applied
CLIENT evaluates code on SLE
Is all code ready?
DEPLOY SLE to Live Production Environment (LPE)

Figure 21-1: Source code flow
