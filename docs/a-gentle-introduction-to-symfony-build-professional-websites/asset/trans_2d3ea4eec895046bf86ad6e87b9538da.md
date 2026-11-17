

```
$ php symfony configure:database "mysql:host=localhost;dbname=dbname" root mYsEcret
```

The configure:database task takes three arguments: the PDO DSN<sup>25</sup>, the username, and the password to access the database. If you don't need a password to access your database on the development server, just omit the third argument.

> If you want to use Propel instead of Doctrine, add `--orm=Propel` when creating the project with the generate:project task. And if you don't want to use an ORM, just pass `--orm=none`.

## Application Creation

Now, create the frontend application by running the generate:app task:

```
$ php symfony generate:app frontend
```

> Because the symfony shortcut file is executable, Unix users can replace all occurrences of 'php symfony' by './symfony' from now on.
> On Windows you can copy the 'symfony.bat' file to your project and use 'symfony' instead of 'php symfony':

```
c:\> copy lib\vendor\symfony\data\bin\symfony.bat .
```

Based on the application name given as an argument, the generate:app task creates the default directory structure needed for the application under the apps/frontend/ directory.

## Security

By default, the generate:app task has secured our application from the two most widespread vulnerabilities found on the web. That's right, symfony automatically takes security measures on our behalf. To prevent XSS attacks, output escaping has been enabled; and to prevent CSRF attacks, a random CSRF secret has been generated.

Of course, you can tweak these settings thanks to the following options:

- --escaping-strategy: Enables or disables output escaping
- --csrf-secret: Enables session tokens in forms

If you know nothing about XSS<sup>26</sup> or CSRF<sup>27</sup>, take the time to learn more about these security vulnerabilities.

## Directory Structure Rights

Before trying to access your newly created project, you need to set the write permissions on the cache/ and log/ directories to the appropriate levels, so that both your web server and command line user can write to them:

- 25. http://www.php.net/manual/en/pdo.drivers.php
- 26. http://en.wikipedia.org/wiki/Cross-site_scripting
- 27. http://en.wikipedia.org/wiki/CSRF

```
$ symfony project:permissions
```

> ### Tips for People using an SCM Tool
> 
> symfony only ever writes to two directories of a symfony project, cache/ and log/. The content of these directories should be ignored by your SCM (by editing the svn:ignore property if you use Subversion for instance).

## Web Server Configuration

### The ugly Way

In the previous chapters, you have created a directory that hosts the project. If you have created it somewhere under the web root directory of your web server, you can already access the project in a web browser.

Of course, as there is no configuration, it is very fast to set up, but try to access the config/databases.yml file in your browser to understand the bad consequences of such a lazy attitude. If the user knows that your website is developed with symfony, he will have access to a lot of sensitive files.

**Never ever use this setup on a production server**, and read the next section to learn how to configure your web server properly.

### The secure Way

A good web practice is to only put the files that need to be accessed by a web browser under the web root directory, such as stylesheets, JavaScripts and images. By default, we recommend storing these files under the web/ sub-directory of a symfony project.

If you have a look at this directory, you will find some sub-directories for web assets (css/ and images/) and the two front controller files. The front controllers are the only PHP files that need to be under the web root directory. All other PHP files can be hidden from the browser, which is a good idea as far as security is concerned.

## Web Server Configuration

Now it is time to change your Apache configuration, to make the new project accessible to the world.

Locate and open the httpd.conf configuration file and add the following configuration at the end:

```
# Be sure to only have this line once in your configuration
NameVirtualHost 127.0.0.1:8080

# This is the configuration for your project
Listen 127.0.0.1:8080

<VirtualHost 127.0.0.1:8080>
    DocumentRoot "/home/sfproject/web"
    DirectoryIndex index.php
    <Directory "/home/sfproject/web">
        AllowOverride All
        Allow from All
</Directory>
Alias /sf /home/sfproject/lib/vendor/symfony/data/web/sf
<Directory "/home/sfproject/lib/vendor/symfony/data/web/sf">
AllowOverride All
Allow from All
</Directory>
</VirtualHost>
```

The /sf alias gives you access to images and javascript files needed to properly display default symfony pages and the web debug toolbar.
On Windows, you need to replace the Alias line with something like:

```
Alias /sf "c:\dev\sfproject\lib\vendor\symfony\data\web\sf"
```

And /home/sfproject/web should be replaced with:

```
c:\dev\sfproject\web
```

This configuration makes Apache listen to port 8080 on your machine, so the website will be accessible at the following URL:

```
http://localhost:8080/
```

You can change 8080 to any number, but favour numbers greater than 1024 as they do not require administrator rights.

## Configure a dedicated Domain Name

If you are an administrator on your machine, it is better to setup virtual hosts instead of adding a new port each time you start a new project. Instead of choosing a port and adding a Listen statement, choose a domain name (for instance the real domain name with .localhost added at the end) and add a ServerName statement:

```
# This is the configuration for your project
<VirtualHost 127.0.0.1:80>
ServerName www.myproject.com.localhost
<!--- same configuration as before --->
</VirtualHost>
```

The domain name www.myproject.com.localhost used in the Apache configuration has to be declared locally. If you run a Linux system, it has to be done in the /etc/hosts file. If you run Windows XP, Vista or Win7, this file is located in the C:\WINDOWS\system32\drivers\etc\ directory.

Add the following line:

```
127.0.0.1 www.myproject.com.localhost
```

## Test the New Configuration

Restart Apache, and check that you now have access to the new application by opening a browser and typing http://localhost:8080/index.php/, or http://www.myproject.com.localhost/index.php/ depending on the Apache configuration you chose in the previous section.

![](img/0f886a7f4cbcc3939be96e985ca35ff4_44_0.png)

If you have the Apache mod_rewrite module installed, you can remove the index.php/ part of the URL. This is possible thanks to the rewriting rules configured in the web/.htaccess file.

You should also try to access the application in the development environment (see the next section for more information about environments). Type in the following URL:

```
http://www.myproject.com.localhost/frontend_dev.php/
```

The web debug toolbar should show in the top right corner, including small icons proving that your sf/ alias configuration is correct.

![](img/0f886a7f4cbcc3939be96e985ca35ff4_45_0.png)

The setup is a little different if you want to run symfony on an IIS server in a Windows environment. Find how to configure it in the related tutorial 28.

## Using the Sandbox

If your goal is to give symfony a try for a few hours, keep reading this chapter as we will show you the fastest way to get you started.

The fastest way to experiment with symfony is to install the symfony sandbox. The sandbox is a dead-easy-to-install pre-packaged symfony project, already configured with some sensible defaults. It is a great way to practice using symfony without the hassle of a proper installation that respects the web best practices.

> As the sandbox is pre-configured to use SQLite as a database engine, you need to check that your PHP supports SQLite. You can also read the Configuring the Database section to learn how to change the database used by the sandbox.

You can download the symfony sandbox in .tgz or .zip format from the symfony installation page 29 or at the following URLs:

```
http://www.symfony-project.org/get/sf_sandbox_1_4.tgz
http://www.symfony-project.org/get/sf_sandbox_1_4.zip
```

Un-archive the files somewhere under your web root directory, and you are done. Your symfony project is now accessible by requesting the web/index.php script from a browser.

