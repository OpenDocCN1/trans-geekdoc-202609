Unix shell commands can come in handy in a Windows environment. If you would like to use tools like tar, gzip or grep on Windows, you can install Cygwin18. The adventurous may also like to try Microsoft's Windows Services for Unix19.

# PHP Configuration

As PHP configurations can vary a lot from one OS to another, or even between different Linux distributions, you need to check that your PHP configuration meets the symfony minimum requirements.

First, ensure that you have PHP 5.2.4 as a minimum installed by using the phpinfo() built-in function or by running php -v on the command line. Be aware that on some configurations, you might have two different PHP versions installed: one for the command line, and another for the web.

Then, download the symfony configuration checker script at the following URL:

```
Listing 3-2
http://sf-to.org/1.4/check.php
```

Save the script somewhere under your current web root directory.

Launch the configuration checker script from the command line:

```
Listing 3-3
$ php check_configuration.php
```

If there is a problem with your PHP configuration, the output of the command will give you hints on what to fix and how to fix it.

You should also execute the checker from a browser and fix the issues it might discover. That's because PHP can have a distinct php.ini configuration file for these two environments, with different settings.

Don't forget to remove the file from your web root directory afterwards.

If your goal is to give symfony a try for a few hours, you can install the symfony sandbox as described at the end of this chapter. If you want to bootstrap a real world project or want to learn more about symfony, keep reading.

# Symfony Installation

# Initializing the Project Directory

Before installing symfony, you first need to create a directory that will host all the files related to your project:

```
Listing 3-4
$ mkdir -p /home/sfproject
$ cd /home/sfproject
```

Or on Windows: