
![](img/be3c5789b9e58d6dc55dc804718f15b4_21_0.png)

FIGURE 1.10 The Mac OS X DVD installation menu.

## Installing MySQL

Click the button in the Mac OS X DVD installation menu to begin installing MySQL 5.0. At the screen shown in Figure 1.11, click the Continue button.

![](img/be3c5789b9e58d6dc55dc804718f15b4_21_1.png)

FIGURE 1.11 Beginning a MySQL installation operation on the Mac.

Click the Continue button to move to the next step, which contains information regarding installation. Click the Continue button to move to the next step, which contains licensing information. Click the Continue button to move to the next step, which is to choose the destination. Select the appropriate drive, as shown in Figure 1.12, and then click the Continue button to move on.

![](img/be3c5789b9e58d6dc55dc804718f15b4_22_0.png)

FIGURE 1.12 Select the MySQL destination.

The next screen verifies your installation location and requires you to click the Install button to continue. At this point, you receive a prompt for the administrator username and password (unless you are installing as root) before the installation process continues. When it continues, let the process run its course until you see the installation is complete, as shown in Figure 1.13.

![](img/be3c5789b9e58d6dc55dc804718f15b4_23_0.png)

FIGURE 1.13 MySQL has been installed.

## Installing PHP

Click the option on the Mac OS X DVD installation menu to install PHP; an installation package will open, as shown in Figure 1.14.

![](img/be3c5789b9e58d6dc55dc804718f15b4_23_1.png)

FIGURE 1.14 Beginning installation of PHP on Mac OS X.

Click Continue to move to the next step, which asks you to choose the destination. Select the appropriate drive, as shown in Figure 1.15, and then click the Continue button to move on.

![](img/be3c5789b9e58d6dc55dc804718f15b4_24_0.png)

FIGURE 1.15 Select the PHP destination.

The next screen verifies your installation location and requires you to click the Install button to continue. At this point, you receive a prompt for the Administrator username and password (unless you are installing as root) before the installation process continues. When it continues, let the process run its course until you see the installation is complete, as shown in Figure 1.16.

![](img/be3c5789b9e58d6dc55dc804718f15b4_24_1.png)

FIGURE 1.16 PHP has been installed.

To test whether PHP is now a part of your web server, create a simple script called phpinfo.php that looks like this:

```
<?php
phpinfo();
?>
```

Place this file in your web server document root at /Library/WebServer/Documents. In your web browser, visit http://localhost/phpinfo.php on your new server and you should see a page giving lots of information on the PHP configuration.

## Troubleshooting

All the steps in these quick-start guidelines have been tested with the versions of the software supplied on the DVD in this package.

If you experience installation problems, first check that you have followed the steps exactly as given here, and then try the extended installation and troubleshooting information found in the chapters immediately following this one. These chapters provide troubleshooting tips and links to additional sites that can help you work through your installation issues.

## Installing and Configuring MySQL

This is the first of three installation-related chapters in which you will learn how to set up your development environment. We'll tackle the MySQL installation first because building the PHP module requires bits of the MySQL installation to be complete if you're going to use MySQL with PHP.

In this chapter, you will learn:

- How to install MySQL
- Basic security guidelines for running MySQL
- How to work with the MySQL user privilege system

## Current and Future Versions of MySQL

The installation instructions in this chapter refer to MySQL 5.0.51, which is the current production version of the software. This version number can be read as “minor release number 51 of the major version 5.0 software.” MySQL AB, now owned by Sun Microsystems, is the company responsible for creating and distributing MySQL; the company uses minor release numbers for updates containing security enhancements or bug fixes. Minor releases do not follow a set release schedule; when enhancements or fixes are added to the code and thoroughly tested, MySQL AB releases a new version with a new minor version number.

It is possible that by the time you read this, the minor version number will have changed to 5.0.52 or beyond. If that is the case, you should read the list at http://dev.mysql.com/doc/refman/5.0/en/news-5-0-x.html for any changes regarding the installation or configuration process that makes up the bulk of this chapter.

Although it is unlikely that any installation instructions will change between minor version updates, you should get in the habit of always checking the changelog of software that you install and maintain. If a minor version change does occur, but the changelog notes no installation changes, simply make a mental note and substitute the new version number wherever it appears in the installation instructions and accompanying figures.

> NOTE: By the time this is printed, it is likely that MySQL 5.1 will have been officially released. Although we do not cover the enhancements to MySQL 5.1, nothing covered here or in the video lessons is negated by the release of MySQL 5.1. In other words, if you choose to install MySQL 5.1 instead of MySQL 5.0, you should be able to perform all exercises in the videos. For information on the changes between MySQL 5.0 and MySQL 5.1, please see http://dev.mysql.com/doc/refman/5.1/en/mysql-nutshell.html.

## How to Get MySQL

> NOTE: Linux distribution CDs usually contain some version or another of the open source MySQL software, although these are usually several minor versions behind the current release.

MySQL AB, the company that develops and maintains the MySQL database server, distributes MySQL on its website: http://www.mysql.com/. Binary distributions for all platforms, installer packages for Mac OS X, and RPMs and source code files for Linux/UNIX platforms can be found at the website.

The installation instructions in this chapter are based on the official MySQL 5.0.x Community Server distribution from MySQL AB. All files can be downloaded from http://dev.mysql.com/downloads/mysql/5.0.html, and the current versions as of the time of writing can be found on the DVD.

## Installing MySQL on Mac OS X

The MySQL installation process for Mac OS X is fairly straightforward—the developers from MySQL AB have created an installation package for Mac OS X. Go to the MySQL downloads page at http://dev.mysql.com/downloads/mysql/5.0.html and look for the section titled “Mac OS X downloads (package format).” From there, download the appropriate standard version for your system; the version you choose will depend on your Mac OS X version (10.3, 10.4 or 10.5) and architecture (PowerPC, PowerPC 64-bit, or Intel x86).

When the download is complete, unpack the installer file and double-click the *.pkg file. Follow these installation steps to complete the process:

1. The MySQL installer launches automatically, as shown in Figure 2.1. Click Continue to move to the next step.

![](img/be3c5789b9e58d6dc55dc804718f15b4_28_0.png)

FIGURE 2.1 The MySQL Installer for the Mac has started.

2. The next few screens contain general information regarding installation and the MySQL license. Read these screens and click Continue to move through them.

3. After stepping through the information and licensing screens, you must select an installation destination. Select the appropriate drive as shown in Figure 2.2 and then click the Continue button.

![](img/be3c5789b9e58d6dc55dc804718f15b4_29_0.png)

FIGURE 2.2 Select an installation location.

4. The next screen verifies your installation location selection and requires you to click the Install button to continue. At this point, you might be prompted to enter the administrator username and password before the installation process continues. When it continues, let the process run until you see that the installation is complete, as shown in Figure 2.3.

![](img/be3c5789b9e58d6dc55dc804718f15b4_29_1.png)

FIGURE 2.3 MySQL has been installed.
