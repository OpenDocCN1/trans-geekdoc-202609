   

Table of Contents

[Chapter 1: Installing the Software](#index_split_006.html#filepos15798)

[Chapter 2: Virtualmin Configuration](#index_split_007.html#filepos27200)

[Chapter 3: Virtualmin “Server Template”](#index_split_008.html#filepos30541)

[Chapter 4: Automation: Custom Scripts](#index_split_009.html#filepos34368)

[Chapter 5: Setup PHP-FPM on existing Websites.](#index_split_010.html#filepos41904)

[Chapter 6: Apache Handlers 101 / PHP-FPM](#index_split_011.html#filepos50294)

[Chapter 7:  Setting up Nginx Reverse-Proxy](#index_split_012.html#filepos56393)

[Chapter 8: Securing your Server (Bonus)](#index_split_014.html#filepos66911)

[Chapter 9: Where to go from here?](#index_split_015.html#filepos81151)

 

Virtualmin Tips & Hacks

 

 

How to Setup and Integrate PHP-FPM  &

Nginx Reverse Proxy into Virtualmin

 

 

 

 

Adrian Ling Kong Heng

Copyright © 2014

[www.ilovevirtualmin.com](http://www.ilovevirtualmin.com/)  

 

 

Copyright 2014  © Adrian Ling. All rights reserved.  

 

No part of this work may be reproduced or transmitted in any form or by any means, electronic or mechanical, including photocopying, recording or by any information storage or retrieval system without prior written permission from the copyright owner and the publisher.

Acknowledgements

I am grateful to God who enabled me to write this book, and to whom I owe my very existence.

 

Special thanks to my beautiful wife and my 2 wonderful kids for supporting me and  giving me the time and space to write.

 

And of course, this book would not have been possible without these two great men who created it -  Jamie Cameron & Joe Cooper in the late 2005 – and who are still actively involved in maintaining and enhancing it.

 

Today, Webmin/Virtualmin is one of the world's most popular web-based Unix/Linux server administration tool, with more than 3 million downloads every year!

Bonuses

All the source code listings are available for download in the “Customers” section on the accompanying website – [www.ilovevirtualmin.com](http://www.ilovevirtualmin.com/). The “Access Code” to download these files are in the last chapter of this book. In addition to the source code listings and scripts required in this book, I've also created 2 standalone shell scripts to help you create the configuration files for Nginx Reverse-Proxy and PHP-FPM pools quickly from the command line.

 

My colleagues suggested that I should sell these scripts separately at $5 per script, but I  want to provide a complete solution for you. Everything you need to install, configure,  integrate and automate PHP-FPM and Nginx in Virtualmin IS in this book. Nothing is left out.

  

*   > createvhost.sh – shell script to to create the Nginx reverse-proxy “vhosts” - you just need to provide the 'userID', 'domain-name' and 'IP address', and the script will create the correct vhost configuration settings for you.  
    
      
    
*   > createpool.sh – this shell script  will create individual “php-fpm” user-pools for each of your existing Virtual Servers. You just need to provide the 'userID' and it will take care of the rest.  
    

 

You will find these 2 scripts really useful if you have many existing websites (virtual servers) in your current Virtualmin setup and you want to migrate them to PHP-FPM and/or Nginx Reverse Proxy.

My goal with this book (as with all my other books in the “Practial Guide Series”) is to empower you to be productive as quickly as possible!  

 

Ok, one last note before we begin –  my lawyer said it should be “framed correctly” in the format below (“Disclaimer and Terms of Use Agreement”) - but if I have my way, the “short and sweet version” version of the TOS is this - “If you mess up your server, it's your own fault, so proceed with caution and always test on a development server/VPS first”.  Cool? Let's proceed!

Disclaimer and Terms of Use Agreement

The author and publisher of this eBook and the accompanying materials have used their best efforts in preparing this eBook. The author and publisher makes no representation or warranties with respect to the accuracy, applicability, fitness, or completeness of the contents of this eBook. The information provided in this book is provided on an “As Is” basis, without warranty and is strictly for educational purposes. Therefore, if you wish to apply the ideas contained in this EBook, you take full responsibility for your actions.  

The author and publisher disclaim any warranties (expressed or implied), merchantability, or fitness for any particular purpose. The author and publisher  shall in no event be held liable to any party for any direct, indirect, punitive, special, incidental or other consequential damages arising direclty or indirectly from any use of this material, which is provided “as is”, and without warranties.

The author and publisher do not warrant the performance, effectiveness or applicability of any sites listed or linked to in this eBook.  All links are for information purposes only and are not warranted for content, accuracy or any other implied or explicit purpose.

Introduction

This is a practical, hands-on guide to help you setup, configure, integrate and automate both PHP-FPM and Nginx reverse-proxy into the Virtualmin web-panel.  There are many tutorials online that shows you how you can do this, but the process is manual and very tedious (you're required to edit multiple configuration files each time).

 

The method I'm about to show you is fully automated. Once you have set it up, you can use the familiar Virtualmin interface to create your Virtual Servers (websites) with PHP-FPM running under its own Virtual-Server ID.  

No more messing with multiple configuration files!

 

NOTE:  Although this book is targetted at the more seasoned Linux users/System Administrators to setup PHP-FPM and Nginx reverse-proxy,  I've included as much introductory text as possible to provide a quick overview of each step. If you're a seasoned System Admin, you can just skip the the 'intro' text and dive into the meaty stuff.

 

Please note that familiarity with Virtualmin is required because this book does not cover the various settings and menus in Virtualmin.  For example,  if the instruction says, go to: “Virtualmin > System Settings > Server Template”  - the reader is assumed to know what that means and knows how to navigate to the appropriate page in Virtualmin.

 

If you've no idea what that means, but you want work with Virtualmin, then you may want to check out my other book – “Webmin & Virtualmin – the Open Source Alternative  to Cpanel” - a newbie friendly book with multiple screenshots to help you get up to speed quickly with Virtualmin.

 

Why PHP-FPM? 

I won't into the details of what is PHP-FPM or what are its pros and cons – but in a nutshell, PHP-FPM offers greater stability and better performance for busy, high-traffic websites while utilizing lower resources.

 

Because of these benefits, many webmasters are turning to PHP-FPM implementation instead of the typical “mod\_php” or “FastCGI” implementation in stock Apache setup.  In Virtualmin, the default setup is to run PHP under the “fcgid” mode – which is great for providing the necessary security and account isolation.

 

However, the main issue with this setup is that fcgid is not as efficient as PHP-FPM.  On a server with limited RAM/memory, a sustained burst of heavy traffic can quickly eat up all the available memory and cause instability to the server.

 

Note: If you want to know more about how PHP-FPM stack up against the other PHP SAPIs,  please visit:  [http://php-fpm.org/about/](http://php-fpm.org/about/)  You will find a comparison chart between vanilla PHP (php out of the box),  PHP-FastCGI and PHP-FPM. 

 

 

Why Nginx?

Nginx is a rising star where web-servers are concerned. Nearly 40% of the world's busiest website runs a highly tuned Nginx to serve thousands of visitors daily. It is fast, stable and it does not use as much resources as the Apache server.  Virtualmin has built-in support to run the Nginx webserver insteadl of Apache – but the support and functionality for Nginx is rather limited compared to Apache. Furthermore, if you want to run the Nginx webserver, you have to disable Apache.

 

We want to run both – Apache as the main webserver, and Nginx as the “reverse-proxy” to handle all the static pages and files. This is not supported inVirtualmin. The information in this book will enable you to have the best of both worlds – the power and flexiblity of the Apache webserver, and the speed and agility of Nginx server as the “reverse proxy” running on the same Virtualmin powered server.

 

Why this book? 

There are many tutorials on the internet that shows one how to do this, but unfortunately, many of them are outdated and contains errors. Furthermore, the process is “Manual” - i.e. each time the webmaster create a new virtual server (hosting account), the webmaster has to manually edit multiple configuration files – the php-fpm pools, the Apache /etc/httpd/conf/httpd.conf file, etc.

 

I wrote this book because I'm a great fan of automation. I want Virtualmin to automate the entire process – i.e. when I create a new virtual server (hosting account), I want everything to be automatically setup – the php-fpm pools running under its own UserID (virtual server ID) and the appropriate Apache directives automatically appended to the /etc/httpd/conf/httpd.conf file.

 

This book is birthed after many days of searching the Internet for relevant information – from various developer forums, tech blogs and the official Virtualmin documentation, and putting all these bits and pieces together in this cohesive book. The custom config files provided and custom shell scripts are the results of many man-hours.

 

Assumption about the Reader

The reader is expected to be familiar with the Virtualmin interface and the various menus and settings. The following skills are expected from the reader as well:

  

*   > Ability to use one of the built-in Unix/Linux editors such as 'vi' , 'joe' or 'nano'. 
    
*   > Ability to run commands from the command line/shell. 
    

 

Overview

Before we start, please take note that steps outlined in Chapter 1 – 5 are meant for a brand new server or VPS.  In other words, there are no existing websites or Virtual Servers configured in Virtualmin. This is important because we need to do some preparatory work to configure Virtualmin before creating our first Virtual Server (website).

 

NOTE:  If you have existing websites (virtual servers), you can still follow along but do NOT create any new virtual server until you've read Chapter 5.

Otherwise, your existing sites will 'stop working' because it could not find the correct Apache handler to process the php files.  

 

FAIR WARNING:  There is always a possibility that your existing sites may break if you decide to implement the steps outlined in this guide on your production server. This is because every server environment and setup is different. There are no identical setup – unless you have set them up exactly the same way from scratch at the same time.  

 

Murphy's Law tends to strike when one least expect it. Because of this, I would strongly recommend that you try this on a development server (you can easily get cheap VPS for $5 - $10/mth to test).

 

Once you're confident that it will work in your environment, then you can apply it to your production server.  Let's dive in!

Chapter 1: Installing the Software

If you have just installed Virtualmin on a stock server or VPS, you're probably running CentOS 6  at the time of this writing (October 2014). CentOS 7 has just been released recently, and Virtualmin support for it is not as matured or stable compared to CentOS 6

 

CentOS 6.5 (and 6.6)  ships with the following default software:

  

*   > PHP 5.3.3  (this version of PHP has reached its end of life and is no longer supported by the PHP team) 
    
*   > MySQL 5.1.73  (a very old version of MySQL server. Current stable version is MySQL 5.5) 
    
*   > Apache 2.2.15  (although aged, it is considered one of the most stable version of Apache ever released. The RedHat/CentOS team is still actively maintaining it) 
    

 

For the purpose of this book, we will be updating PHP to the latest stable 5.4 and upgrading the aged MySQL server to the current 5.5 from the “EPEL” and “REMI” repositories. We will also install “mod\_fastcgi” which is required for Apache to “communicate” with PHP-FPM from the “RepoForge” repository.

 

A quick note about Software repositories – some 3rd party software repositories may use the same package name as the base CentOS packages – enabling and using these software repositories may cause you to accidentally over-write the standard base packages with those from these 3rd party repositories. Hence, use these 3rd party repositories with care.

 

TIP:  When you run the “yum install ...” command (without the '-y' flag), it will display the package name PLUS the name of the repository it is located. You need to manually enter “y” to confirm the install if want to go ahead and install the software.   

 

EPEL (Extra Packages for Enterprise Linux)

Ref:  [https://fedoraproject.org/wiki/EPEL](https://fedoraproject.org/wiki/EPEL) 

EPEL is a Fedora Special Interest Group that creates, maintains, and manages a high quality set of additional packages for Enterprise Linux such as RHEL (RedHat's commercial OS), CentOS (Same as RHEL, but community supported), Scientific Linux (SL) and Oracle Enterprise Linux (OEL).

 

EPEL packages are usually based on their Fedora counterparts and does not conflict with or replace packages in the base Enterprise Linux distributions. EPEL uses much of the same infrastructure as Fedora, including buildsystem, bugzilla instance, updates manager, mirror manager, etc.

 

Download and Install the EPEL repository:

`# wget `[`http://dl.fedoraproject.org/pub/epel/6/i386/epel-release-6-8.noarch.rpm`](http://dl.fedoraproject.org/pub/epel/6/i386/epel-release-6-8.noarch.rpm) 

`# rpm -ivh epel-release-6.8.noarch.rpm`

(Note: If you're using a different CentOS distro, e.g. 64-bit instead of 32-bit, please visit the EPEL page and download the appropriate rpm package for your machine.

To check for the latest news/updates or software versions, please visit:

 

REMI: 

Ref: [http://blog.famillecollet.com/pages/Config-en](http://blog.famillecollet.com/pages/Config-en) 

The REMI software repository a yum repo maintained by a French programmer -  Remi Collet. It usually has the latest version of the software in found in the core CentOS and Red Hat repositories, and it uses the same package names as in the official repositories.

 

For example, the official CentOS repository uses the name “php-cli” (the command line version of PHP and is based on PHP 5.3.3).   IF you install “php-cli” from the REMI  repository,  it will automatically upgrade the “php-cli” to the latest PHP 5.4.34

 

Because of this (packages using the same naming convention as the official repos), the REMI repository is “disabled” by default so that you don't accidently “upgrade” a system software without realizing it.

 

You'll have to explicity 'enable' this repo if you want to install a particular software from this repo.  The Remi repository also depends on the EPEL repository which is why we have to install the EPEL repo first.

 

Download and Install the REMI repository:

`# wget `[`http://rpms.famillecollet.com/enterprise/remi-release-6.rpm`](http://rpms.famillecollet.com/enterprise/remi-release-6.rpm) 

`# rpm -ivh remi-release-6.rpm`

 

 

RPMFORGE:    [http://repoforge.org/use/](http://repoforge.org/use/) 

RPMFORGE is another popular softwaare repository trusted by many open-source enthusiast. It is now known as “RepoForge”, a project that maintains various RPM packages for Red Hat Enterprise Linux (RHEL), CentOS and Scientific Linux. It provides a set of repositories compatible with various RHEL-derived distributions.  

 

Download & Install RepoForge:

`# wget `[`http://pkgs.repoforge.org/rpmforge-release/rpmforge-release-0.5.3-1.el6.rf.i686.rpm`](http://pkgs.repoforge.org/rpmforge-release/rpmforge-release-0.5.3-1.el6.rf.i686.rpm)` `

 

If you're using a different CentOS distro, please visit [http://repoforge.org/use](http://repoforge.org/use) and select the appropriate version for your server.  

 

NOTE:  Do not install it  YET – because later, when we run the 'yum update' command to update the installed repositories, the default “AWStats” package will be replaced by the package in RepoForge repository which will cause the AWStats reporting to break. We'll address this issue later. 

` `

Now it's time to update the software repositories (EPEL & REMI)

Update the EPEL repository.

The command below will update the latest packages from the EPEL repository

`# yum update`

![](images/00017.jpg)Type “y” and hit the enter key.

 

Install/Upgrade MySQL 5.5 and PHP 5.4

The command below (with the flag `--enablerepo=remi`) will activate the REMI repo and tells the yum package manager to install/upgrade the software from REMI:

  

`# yum --enablerepo=remi upgrade mysql`

 

\*Note: the command above will also upgrade PHP 5.3 to PHP 5.4 because the yum utility will ensure all the interlinked software dependencies are met (e.g. one of which was the php-mysql which was linked to MySQL 5.1 – so when we upgrade MySQL to 5.5, the yum utility will also upgrade the corresponding “php-mysql” packages to PHP 5.40).

![](images/00006.jpg)When prompted, type  'y' and press the enter key.

 

Note:  The 4th column tells you which software repository the software package is being installed from.  Once the software upgrade has been completed, run this command to update some of the essential tables in MySQL:  
 

`# mysql_upgrade `

` `

Install PHP-FPM 

Now that all the system software is up to date, let's install PHP-FPM from the REMI repo

`# yum --enablerepo=remi install php-fpm`

 

This will create the directory:  /etc/php-fpm.d/ with the default “www.conf” pool file. We will need to create a new 'pool template' called “www.bare” in this directory later.

![](images/00022.jpg)`  `

  

Ok, now we will install the “RepoForge” repository so that we can install the “mod\_fastcgi” package.  This “mod\_fastcgi” required for Apache to communicate with the PHP-FPM server.

`# rpm -ivh rpmforge-release-0.5.3-1.el6.rf.i686.rpm`

`# yum install mod_fastcgi`

` `

![](images/00039.jpg) 

The the command above will install a file called “fastcgi.conf” in the /etc/httpd/conf.d/ directory.  Edit that file with your favorite editor and replace ALL the content in that file with just these 3 lines of code:

  

 

(note: the source code for the 3 lines above is found in the “fastcgi.conf” file)

Chapter 2: Virtualmin Configuration

Ok, now that all the necessary software has been updated and installed, let's login to Virtualmin now.  

 

Note: if this is the first time you are logging into Virtualmin, it will prompt you to go through  series of “Post Installation Steps” where it will fine-tune some of the server settings (e.g. optimizing the MySQL /etc/my.cnf for you based on the memory setting you choose and assigning a root password for MySQL).

 

Once the post-installation steps have been completed, proceed to Virtualmin's Configuration page.  Click on the the Virtualmin menu, and click:  “System Settings” > Virtualmin Configurations”

![](images/00023.jpg)You will then see the following page.

 

![](images/00041.jpg) 

Select “Actions upon server and user creation” from the drop-down list:

You will see the following:

![](images/00037.jpg)

 

The 2 important fields to note are the:

  

*   > Command to run before making changes to a server. `/root/updatehandler.sh`  
    
*   > Command to run after making changes to a server.  `/root/phpfpm.sh`  
    

 

This is the “key” to making all the PHP-FPM automation work.  Basically, this feature allows you to run custom scripts prior to making changes to a server (e.g. before a Virtual Server is created), as well as run another custom script AFTER making changes to a server (after Virtualmin has completed setting up a new virtual server).  

 

This applies to “deleting” a virtual server as well.  In the screenshot above, we have entered 2 scripts:

 

  

*   > “updatehandler.sh” is a simple shell script to check if the default “php.conf' file exist in /etc/httpd/conf.d/ - and if it does, to rename it to 'php.conf.orig'. This is to prevent Apache from loading the “mod\_php” module which takes priority over the “mod\_fastcgi” - in other words, Apache will run PHP as “Apache 2.0 Handler” instead of talking to PHP-FPM. 
    
*   > “phpfpm.sh” is the main script that creates new PHP-FPM pool under the Virtual Server's ID and restart the PHP-FPM service in the background. It is also remove this PHP-FPM pool if the Virtual server is destroyed. 
    

Chapter 3: Virtualmin “Server Template”

Now, let's create a new Server Template that includes the required Apache directives to communicate with the PHP-FPM service via the “mod\_fastcgi” module.

 

In Virtualmin, click on the “System Settings” > Server Templates”

![](images/00036.jpg)If you haven't created a Server Template yet, click on the “Create a Template from Default Settings”.  

![](images/00046.jpg) 

Give it a name, e.g. “Server-X1” or “PHP-FPM” and click the “Create and Next” button

If you already have an existing custom  Server Template, you can click on that template and then click on the “Clone it” button.

![](images/00007.jpg) 

For example, I have an existing template called “Server-X1” - I clicked on it and then  click on the “Clone Template” button.

![](images/00047.jpg)Give it the cloned template a new name, say  “PHP-FPM”.

 

There are many options and settings that you can set in the Server Template, in our case, we are only interested in the “Apache Website” section.  

 

Click the drop-down list  (at the “Edit template section”) and  select “Apache Website” 

![](images/00024.jpg) 

You will then see a page with a box with the description: “Directives and settings for new websites”.  Select the “Apache Directives Below” from the radio-button 

![](images/00018.jpg) 

 Then, paste the following code at the very bottom, after the existing codes in the box.

![](images/00043.jpg) 

(the sourcecode for the above is found in the “ifmodule\_modfastcgi.txt” )

 

NOTE:  The “FastCgiExternalServer ...”  line should be just one long line, there is NO  carriage return or the script will fail.  You can download the custom script package that is provided with this book - The download link is  at Chapter 10.

 

Further down on this  same page,  you will see this section:

![](images/00040.jpg)

 

The default setting in Virtualmin is to execute PHP as 'FCGId'.

 

Change it to “Apache mod\_php (run as Apache's user)”  (see the screenshot above)

 

This option does not add any additional FCGID directives to the “httpd.conf” file which may cause problem.

 

The shell script (“updatehandler.sh”) that we had set in the Virtualmin Configuration page earlier will ensure that the 'mod\_php' module is not loaded.

Chapter 4: Automation: Custom Scripts

In Chapter 2, we've setup Virtualmin to run 2 custom scripts – “updatehandler.sh” before creating the virtual server, and “phpfpm.sh” after the virtual server has been created. In this chapter, we'll take a closer look at these 2 shell scripts, plus a few other “helper” scripts.

You can download the scripts here: [http://ilovevirtualmin.com/books-scripts/php-fpm](http://ilovevirtualmin.com/books-scripts/php-fpm)

Download the “vserver.tgz” file and extract it in the /root directory.  You will see the following files and directory:

  

*   > `updatehandler.sh` 
    
*   > `phpfpm.sh` 
    
*   > `createpool.sh` 
    
*   > `www.bare` 
    
*   > `fastcgi.conf` 
    
*   > `nginx/  ← this is a folder.` 
    
      
    *   > > `nginx.conf` 
        
    *   > > `proxy.inc` 
        
    *   > > `microcache.inc` 
        
    *   > > `virtualserver.com` 
        
    *   > > `nginx-proxy` 
        
    *   > > `createvhost.sh` 
        

` `

Let's look at each of these custom scripts:

 

1\. “updatehandler.sh”

Basically, this script checks if the /etc/httpd/conf.d/php.conf exist. If it does, then  will rename it to “php.conf.orig” to prevent Apache from loading this module and running the PHP interpreter as 'mod\_php'.  This will enable 'mod\_fastcgi' module to run and communicate with the PHP-FPM server.

 

It will also make a backup copy of all the files in the /etc/httpd/conf/ and /etc/httpd/conf.d/ to the “/root/config-bak/” for safe-keeping.

![](images/00027.jpg)  

2\. “phpfpm.sh”

This script makes use of the conditional statement “If the $VIRTUALSERVER\_ACTION“ provided by Virtualmin.  This is a cool feature in Virtualmin that allows one to create some really funky scripts by using the various conditional statements provided by Virtualmin.   Here's the  code listing:

![](images/00005.jpg) 

This script (phpfpm.sh) uses the 'sed' command to create a new PHP-FPM pool under the Virtual Server's userID (account owner) in the /etc/php-fpm.d/ directory.

 

It uses the base pool template file (“www.bare”) and replaces ALL occurences of “www” with the “userID”.   

 

You can also tweak the settings in the “www.bare” file to suit your server environment.   

 

If If the $VIRTUALSERVER\_ACTION test returns 'DELETE\_DOMAIN' (i.e. the virtual server was deleted from Virtualmin, then this script will remove the PHP-FPM pool file and restart the PHP-FPM service to remove that user's process.

 

\*NOTE:  The additional “if” statement, i.e.

`if [ -f /root/nginx-proxy ]; then `

`  …CODE to create/delete Nginx vhosts…`

`fi`

 

The conditional statement above checks if the file “nginx-proxy” (it's a blank/empty file) exist in the “/root” folder.  By default, it doesn't, but resides in the “ngnix” folder instead. So, if you want to the script to automatically create the Nginx reverse-proxy vhost files, you need to copy the “nginx-proxy” file to /root  

(OR you can just issue this command:  `# touch /root/nginx-proxy `)

 

3\. “www.bare” 

This is the php-fpm pool template file that will be used by the '/root/phpfpm.sh' script. All occurences of 'www' will be replaced with the Virtual-server's userID.

![](images/00026.jpg)You can tweak the variables, e.g. the “pm.\_\*” to suit your server environment/resources.

 

4\. “fastcgi.conf” 

This is the custom (and much simpler) 3 liner which tells Apache to load the 'mod\_fastcgi' module and create a new PHP handler (called “php-fpm”) to process all .php files.  We wil use this file to replace the default “fastcgi.conf” that came with the 'mod\_fastcgi' module.

![](images/00015.jpg)  

Once all these custom scripts are in place, you're good to go.  Create your Virtual Servers  as you normally would, and Virtualmin will automatically setup the new virtual-server to run PHP-FPM under its own userID.

 

If you want to do more fancy stuff with automating the Virtual Server creattion, refer to this documentation: [http://www.virtualmin.com/documentation/developer/prepost](http://www.virtualmin.com/documentation/developer/prepost) 

It has a few sample scripts to get you started, and below are the list of variables which are useful:

 

List of Virtualmin's Environment Variables

![](images/00049.jpg)`  `

Congratulations! You now have a fully automated PHP-FPM powered Virtualmin server.

Chapter 5: Setup PHP-FPM on existing Websites.

The earlier chapters assumes a brand new Virtualmin server that does not have any existing Virtual Servers (websites). This allowed us to configure Virtualmin to  discard the other PHP Sapi and uses PHP-FPM only.  If you have existing websites (Virtual Servers) in Virtualmin, we need to reconfigure the existing sites first – otherwise, those sites will stop working after PHP-FPM has been installed.

 

This chapter will guide you through the necessary steps to achieve this.  I do strongly recommend that you do NOT do this on a Production server because the chances of breaking something is quite high, e.g. a small typo error can cause havoc.  Test it out on a development server (VPS) first, and once you've the steps down pat, only then you can implement it on your live server.

 

Ok, with that out of the way, let's proceed!

 

Backup! 

Needless to say, the first step is to backup ALL the existing Apache's configuration so that in case anything goes awry, you can restore them.

`# cd /etc/httpd/`

`# mkdir -p /root/apache-config/`

`# cp -R conf/ conf.d/  /root/apache-config`

 

The 3 commands above will copy all the existing configuration to the /root/ directory.

Once you've backed-up the configuration files, you can follow the steps outlined from Chapter 1 – 4 to setup PHP-FPM to work with Virtualmin.  

 

BUT, do NOT create/modify/delete any virtual servers yet!  

 

This is to prevent Virtualmin from triggering our custom scripts.  

We need to make the following changes first:

 

Step 1. Modify /etc/httpd/conf/httpd.conf

After installing PHP-FPM , mod\_php will no longer be loaded in Apache, and neither will “FCGId”  - so we need to modify all the existing Virtualhost configured in the /etc/httpd/conf/httpd.conf to work with PHP-FPM instead.

 

Open the file with your favorite editor – find and delete ALL the following lines of code that beings with:

AddHandler fcgid-script .php

AddType application/x-httpd-php .php

AddHandler fcgid-script .php

AddHandler fcgid-script .php5

FCGIWrapper /home/pixms/fcgi-bin/php5.fcgi .php

FCGIWrapper /home/pixms/fcgi-bin/php5.fcgi .php5

RemoveHandler .php

RemoveHandler .php5

IPCCommTimeout

FcgidMaxRequestLen

 

And ALL occurences of that starts with “php\_”

For example,  “`php_admin_value engine Off`”

 

After that, you need to append the following lines of code for EACH virtual host, e.g.

`<IfModule mod_fastcgi.c> `

`   Alias /php-fpm /home/``USER``/cgi-bin/php-fpm `

`   FastCgiExternalServer /home/``USER``/cgi-bin/php-fpm -socket /home/``USER``/cgi-bin/``USER``.sock -pass-header Authorization -idle-timeout 100 `

`</IfModule> `

` `

Replace “USER” with the actual UserID of that Virtual Server.   You can find the 'USER' for each virtualhost by looking for the “DocumentRoot” line.

 

For example:

`DocumentRoot /home/``pixms``/public_html`

This tells you that the 'USER' in this case is 'pixms'

 

Step 2. Rename /etc/httpd/conf.d/php.conf

Rename 'php.conf' to php.conf.orig. This is to prevent Apache from loading the mod\_php module.

`# cd /etc/httpd/conf.d/`

`# mv php.conf php.conf.orig`

 

Step 3. Create the individual PHP-FPM pools 

Make sure the template pool file (www.bare)  exist in /etc/php-fpm.d/

If not, then either create it (from the source code listing in Chapter 4 or copy it from the downloaded custom script package.

 

\# cd /etc/php-fpm.d/

We are going to use the powerful 'sed' utility to do the heavy lifting for us.

The syntax is:  

`sed 's/www/USER/g' www.bare > USER.conf`

where 'USER' is the virtual server account-owner ID.

For example, assuming the UserID for our virtual server is “pixms”, we would issue the following commmand:

` `

\# sed 's/www/pixms/g' www.bare > pixms.conf

![](images/00019.jpg) 

OR, you can use provided script, “createpool.sh”  to automatically create them.

![](images/00045.jpg) 

Source code for:  createpool.sh 

(note: this scripts needs the template file, “www.bare”  in the /etc/php-fpm.d directory)

![](images/00031.jpg)  

 

Step 4: Final Check

  

*   > Have you edited all the <VirtualHost> containers in the /etc/httpd/httpd.conf file? 
    
*   > Have you created a dedicated php-fpm pool file for each VirtualHost (VirtualServer)?   
    
*   > Once everything has been checked, you can start the PHP-FPM service: 
    
    > `# service php-fpm start` 
    
*   > Before restarting the Apache server, issue this command to check that there are no errors in the /etc/httpd/conf/httpd.conf file: 
    
    > `# httpd -M`   
    

If there are errors in the config file (/etc/httpd/conf/httpd.conf), it will be displayed on the screen, e.g.  if I missed removing one of the 'php\_admin\_' directive.

![](images/00009.jpg) 

If there are no errors, you can safely  restart Apache:

`# service httpd restart`

Chapter 6: Apache Handlers 101 / PHP-FPM

This is an “informational” chapter – to give you some theory and background about Apache Handlers and PHP-FPM.  It is not required reading, but recommended so that you'll have a better understand of what is an Apache Handler and what is PHP-FPM?”

 

In the early (or was it late) 90s, a web-server can only process and display HTML and images. It cannot access databases, and it can do any of those fancy 'dynamic' stuff that we see today.

 

To overcome the problem, the programmers came up with “CGI” protocol – a way for web-servers to communicate with other 'programs' (or applications) written in some other programming language such as Perl, C/C++,

 

The developers of the Apache webserver then came up with the concept of “Handlers” - basically a module/method that tells Apache how to communicate with external programs (e.g. Perl script, PHP scripts, etc) when it encounters a specific file type.

 

For example, if a web-visitor requested for a \*.cgi file, then an appropriate handler will instruc Apache to invoke the CGI script/parser to process that file. If the requested file is a \*.php file, then the appropriate PHP handler will instruct Apache how to process the \*.php file.

 

So, in a nutshell, that is what an Apache “Handler” is (in layman's terms) – it instructs Apache how to handle/process different file types.

 

For PHP files, there are essentially 3 different type of “Handlers”

  

*   > Load and run the entire PHP engine (interpreter) within Apache itself. This is known as “mod\_php” or “Apache 2.0 Handler”. This is the default method. 
    
      
    
*   > The “CGI” handler –  Apache will invoke the /usr/bin/php-cgi script to process the PHP file and passes all the environment variables to the cgi program.  The cgi program will process the requests and then pass the results back to Apache. Once that is done, the cgi process is killed. 
    
      
    
*   > The “Fast-CGI” handler  – this is an enhancement to the CGI protocol where the “fast-cgi” process is not killed after it has completed its job. It can potentially “live forever” and is usually run as a daemon process alongside Apache. Also, the communication between Apache and the FastCGI application is via the IPC (Inter Process Communications) such as the Unix socket or TCP socket. 
    

 

In the first case, i.e.  “mod\_php” - each instance of the child apache process has the entire PHP stack/engine within itself. This cause un-necessary bloat to the Apache processes because not every web requests are going to PHP scripts, some web requests are just requesting for images, css, javascripts.  Hence, running “mod\_php” causes in-efficient memory usage – and can be an issue if a heavy traffic website has lots of graphics.

 

Usually, 'mod\_suexec' and 'mod\_suPHP' will be used together with 'mod\_php' to enable Apache to run the PHP scripts under the same userID as the Virtual Server to provide extra security and account isolation, i.e. the scripts in one virtual server cannot access the files on another virtual server.

 

The CGI handler is no longer used in modern applications because the action of spawning/killing CGI processes is very CPU intensive and inefficient.  

 

The FastCGI handler is preferred. It allows PHP scripts to be executed by the PHP engine/parser outside of the Apache web server, i.e.  each request is passed from the Apache web server to the FastCGI process via a communication socket (IPC).

 

The advantages of FastCGI is that the processes are 'persistent' - Multiple persistent processes can configured to run in the background to handle incoming PHP requests.  This avoids the costly CPU intensive operation of spawning/terminating processes in the 'CGI' method.  

 

So, where does PHP-FPM comes into the picture?  PHP-FPM is actually “FastCGI” with its own built-in “Process Manager” (PM).

 

One thing to take note of is that most FastCGI applications/processes run in parallel in daemon (server) mode alongside Apache. These FastCGI applications are managed by a “PM” (Process Manager).

 

In Apache, when we used the “fastcgid” module (the default setting in Virtualmin), Apache uses its own built-in “PM” to manage the FastCGI processes.

 

But when we use the 'mod\_fastcgi' module (installed from the RepoForge repository),  Apache hands over the control of the “Process Manager” to the PHP-FPM engine which has its own “PM” - which is far more efficient.

 

By the way, the “FPM” stands for “FastCGI (F) Process (P) Manager(M)”

For more information about PHP-FPM, visit:  [http://php-fpm.org/about/](http://php-fpm.org/about/) 

 

It has been noted that PHP-FPM can serve up millions of PHP requests without any issues. Of course, this would also depend on the hardware specifications.

Chapter 7:  Setting up Nginx Reverse-Proxy

Virtualmin has built-in support for running “Nginx” as the primary Web-server instead of Apache. If you opt to run Nginx, then you will need to disable the Apache webserver in Virtualmin, as well as a number of other packages such as the Awstats package. At the time of this writing (Nov 2014), the Nginx support (as the primary web-server) in Virtualmin is not as robust or full-featured compared to the Apache web-server

 

The goal of this chapter is to run Nginx as the “reverse-proxy” to our Apache web-server, i.e. Nginx will serve all the static files & pages (all the image, css, and html files), while the PHP files will be served by Apache+PHP-FPM.

 

A Word about Performance before we begin.

Nginx's role as a reverse-proxy is to boost website performance by offloading some of the load from the Apache web-server.  Personally, I've not been able to detect significant performance boost from using Nginx as a reverse-proxy – but most probably it is  because my website doesn't have thousands of visitors a day.  

 

Running Apache with PHP-FPM is sufficient for most people, but anyway, it is always good to be prepared … who knows, perhaps one day your website will be 'slashdotted' and you'll be glad that you have Nginx on your side.

 

The first step is to download and install the Nginx repository:

Go to [http://nginx.org/en/linux\_packages.html#stable](http://nginx.org/en/linux_packages.html#stable)  

 

`# wget `[`http://nginx.org/packages/centos/6/noarch/RPMS/nginx-release-centos-6-0.el6.ngx.noarch.rpm`](http://nginx.org/packages/centos/6/noarch/RPMS/nginx-release-centos-6-0.el6.ngx.noarch.rpm) 

`# rpm -ivh nginx-release* `

`# yum install nginx`

![](images/00034.jpg) 

Type “y” and press the 'enter' key.

 

This will install the latest Stable version of Nginx on your server.  But take note that the default Nginx install above assumes that it will act as the “main webserver” and not as a “Reverse Proxy”.

 

In order to set it up to act as a reverse proxy, I've prepared the necessary configuration files. In Chapter 4,  the extracted the custom script package (vserver.tgz) has a folder called “nginx” with the following files:

  

*   > `nginx.conf` 
    
*   > `proxy.inc` 
    
*   > `microcache.inc` 
    
*   > `virtualserver.com` 
    
*   > `createvhost.sh` 
    
*   > `nginx-proxy  ← this is a blank/empty file` 
    

 

Copy all these files to the  /etc/nginx/  

`# cd /root/nginx`

`# cp * /etc/nginx/`

`# mkdir -p /etc/nginx/vhosts`

 

Note:  You will need to overwrite  the existing “nginx.conf”.

Copy the “nginx-proxy” (this is a blank/empty file) to the /root directory.

The script “phpfpm.sh” checks if this file (nginx-proxy) exist in /root – if yes, then it will proceed to create the necessary Nginx reverse proxy configuration (vhosts) files when you create a new Virtual Server from Virtualmin. Without this file (nginx-proxy), the “phpfpm.sh” script will NOT create the nginx vhost configuration file.

` `

`# cp nginx-proxy /root/ `

` `

Now let's login to Virtualmin and make some adjustment the following settings:

Webmin > Servers > Apache Webserver

and click on the “Global Configuration” tab:

 

![](images/00002.jpg) 

Then click on the “Networking and Addresses” icon

 

![](images/00044.jpg) 

Change the default port “80”  to  “8080”, like so:

![](images/00021.jpg) 

Now, as before, we need to create a new Server Template in Virtualmin to use port “8080” instead of port 80.

 

Virtualmin > System Settings > Server Templates

You can clone one of the existing templates (e.g. the one we had created earlier for creating PHP-FPM).

Select the “Apache website” from the “Edit template section” drop-down list as before.

![](images/00025.jpg)Scroll down the page, and look for “Port Number for Virtual Hosts” and change it to “8080” as shown below:

![](images/00012.jpg)   

VERY Important Final Step!

We need to modify the “Default Settings” template and change the port to 8080 too!

Click on the “Virtualmin > System Settings > Server Templates” again.

And click on the “Default Settings” template.

![](images/00016.jpg) 

As before, select the “Apache Website” section from the drop-down list. Scroll down the page to the Port section and change the default port 80 to “8080”

 

![](images/00012.jpg) 

Even though we won't be using this “Default Template” when creating our Nginx-reverse-Proxy powered site, we still have to do this, otherwise, the default port 80 will be enforced in the “httpd.conf” file and Nginx will fail to start.

 

Once you've done this, we're ready to create our first Nginx-Reverse-Proxy powered site.

 

VERY IMPORTANT NOTE:  If you have existing websites (virtual servers) running on port 80 via Apache, do NOT restart Apache or Nginx OR create a new virtual server. If you do, then all your existing websites will fail to load. 

 

You need to modify/update the Apache config file /etc/httpd/conf/httpd.conf and replace port 80 with “8080”, for example:

` `

Original:  <VirtualHost X.X.X.X:80\>

Change to:  <VirtualHost X.X.X.X:8080\>

where X.X.X.X is the IP address of your own server.

 

Then, you need to create EACH of the nginx vhosts files for every existing website you have.  In the /root/nginx/ directory, there is standard template vhost file - “virtualserver.com” which you can use a reference for the syntax.

 

We will use the provided script - “createvhost.sh” to create the required vhosts, i.e. you just need to run the script, enter the “userID” (account owner ID of this virtual server) and the domain name (e.g. pixms.com). It will prompt you for the server IP address if you did not define it in the script (replace “X.X.X.X” with your server IP and uncomment it)

![](images/00032.jpg) 

The script takes the default vhost template ('virtualserver.com') and replace the appropriate tokens with the input that you provide for the new Nginx vhosts.

 

Here's the source code of the “createvhost.sh” script:

![](images/00010.jpg)  

You can also manually edit the file if you want to see how it works. Below is the snippet of the file. You need to change the following for EACH virtualhost:

 

IP\_ADDRESS:   The actual IP address of your server 

NGINX:   The domain-name (without the 'www'). E.g.:  “ilovevirtualmin.com” 

XUSER:   The userID of for this virtual server (account-owner)  
 

![](images/00014.jpg) 

Chapter 8: Securing your Server (Bonus)

Server Security is huge topic, and it is simply not possible to cover everything in a chapter or even one whole book.  In this chapter, we will just cover the 4 essential steps which I believe every server administrator should take to “lock down” the server -  regardless of whether the server is running Virtualmin or any other control-panel.

 

These 4 steps are:

  

*   > Run only the services required, stop all the other services 
    
*   > Secure /tmp 
    
*   > Install a Firewall 
    
*   > Install LMD (Linux Malware Detect) 
    
      
    

Essential Services Only

Every service that we run on our server listens to a “port” - for example, the Apache webserver listens to port 80,  SSH server listens at port 22,   Mailserver at port 25, etc.

 

Think of these 'ports' as “doors” on a fortress wall – the more doors you have on the fortress wall, the more targets the 'hackers' would have to practise on.

 

To minimize this, we should shut down any services that we intend to use on our server. For example, if we don't intend to provide the mailing list service or the DAV login service to our users, then we should turn them off.

 

We can do this from the command line by using the 'chkconfig' command or from the Webmin's Bootup and Shutdown interface, i.e.  

 

“Webmin > System > Bootup and Shutdown” 

![](images/00013.jpg)

The default setup in Virtualmin is quite sane, but the following services can be safely  turned-off as well:

  

*   > xinetd 
    
*   > splash-manager 
    
*   > mailman (if you don't intend to provide mailing list service) 
    
      
    

 

Securing /tmp

In most cases, the /tmp directory in a freshly installed/commissioned Linux server is NOT secured, i.e. it allows anyone (or script) to upload files to the /tmp directory and execute them.

 

Run this simple test to find out whether your /tmp/ directory has the executable bit set:

Create a simple 'hello world' Shell script in the /tmp directory:

 

`#!/bin/bash`

`echo “hello world”`

` `

Then,chmod +x the script and try to run it.

`# chmod 755 hello.sh`

`# ./hello.sh `

` `

If you see:  `“hello world”`  printed on the screen, then we need to fix it.

Repeat this for the /var/tmp directory as well.

 

To do this, we just need to edit the `/etc/fstab` file and add these 2 lines:

 

![](images/00033.jpg)`  `

NOTE:  The entries in your /etc/fstab may be different – depending on your Operating System and if your server is a VPS,  your hosting company may provide a different “fstab” layout. If in doubt, please check with your hosting provider.  

 

Once you've done with editing the /etc/fstab,  you can either reboot your server or issue this command to remount all your partitions for this to take effect.

 

`# mount -a` 

 

Note: The command above \*should\* causes all filesystems mentioned in /etc/fstab to be remounted, except the partitions with noauto option, but on certain VPSes, it may not work. Try running the 'hello.sh' file again to see if it runs. If yes, then best option is to reboot your VPS.

 

Installing Firewall

Although Virtualmin comes with its own interface to help you manage the “iptables” rules and chains, it can be quite cryptic and daunting, especially if you are new to it.

(The Virtualmin Firewall Interface can be found at:  Webmin > Networking > Firewall)

 

An easier and more intuitive alternative is the CSF firewall from [www.configserver.com](http://www.configserver.com/)

Login to your server via SSH and install csf firewall from the command line:

![](images/00042.jpg)

Edit the csf config file, e.g.     `# vi etc/csf/csf.conf `

Look for this line (near the top of the file)

`# lfd will not start while this is enabled `

`TESTING = "0" `← the default is “1”. Change it to “0” to enable CSF firewall. ` `

 

Then, look for this section:  “IPv4 Port Settings” and add port “10000” and “20000”  to the “TCP\_IN” and “TCP\_OUT” line. See the underlined (in red) below.

![](images/00020.jpg)  

NOTE:  If you've changed the Webmin/Virtualmin port to “11000”, then you need to update the ports here as well.

`# service csf start `

Now, let's install the CSF plugin for Webmin:

Point your browser to:     Webmin >  Webmin Configuration >  Webmin Modules  

Select Install “From local file”  - and enter this path into the field:  `/usr/local/csf/csfwebmin.tgz` 

![](images/00008.jpg) 

Then, click “Install Module ” button.   Once installed, you can access the CSF firewall interface from:    Webmin > System > ConfigServer Security and Firewall   

The first time you click on the link, you'll be prompted to update a symlink, i.e.

![](images/00011.jpg)Click on the link provided and you will then see the CSF web-interface.

![](images/00035.jpg)

The first thing you should do is click on the “Check Server Security”  button.

This will cause the CSF firewalll tu run a scan/security audit on your server setup. It will give you a summary of what needs to be “fixed” or changed to beef up the security of your VPS/server.

 

Then, follow the recommendation to further secure your server.

NOTE: You'd probably see CSF complained that both “portreserve” and “rpcbind” being enabled even t hough you have already issued the command:

 

`# chkconfig  rpcbind off  && chkconfig  portreserve off`

 

And the Webmin > Bootup & Shutdown menu showed that they are not running either. The reason why CSF showed them as 'enabled' is because they are still enabled on run levels 2, 4, 5.  To completely turn them off at ALL runlevels,  run this  command:

` `

\# chkconfig --level 2345 portreserve off

\# chkconfig --level 2345 rpcbind off  
 

Consider shutting down the following services as well:

\# service xinetd stop && chkconfig --level 2345 off

\# service saslauthd stop && chkconfig --level 2345 saslauthd off

 

Installing LMD

Linux Malware Detect (LMD) is a malware scanner for Linux. It is designed around the threats faced in shared hosted environments and released under the GNU GPLv2 license.

(LMD is also popularly known as “Maldet” - Malware Detect).

 

It uses threat data from network edge intrusion detection systems to extract malware that is actively being used in attacks and generates signatures for detection. In addition, threat data is also derived from user submissions with the LMD checkout feature and from malware community resources.

 

The signatures that LMD uses are MD5 file hashes and HEX pattern matches, they are also easily exported to any number of detection tools such as ClamAV.

To download and install the latest version of LMD:

![](images/00030.jpg) 

This will install the “maldet” scripts at  /usr/local/maldetect  and create a symbolic  executable. The Installation Summary:

![](images/00038.jpg) 

 

To update the script to the latest version:

`# maldet --update-ver `

 

To update the latest malware database:

`# maldet --update `

Maldet Configuration File is located at:  `/usr/local/maldetect/conf.maldet ` 

Edit this file and make the following changes:

![](images/00029.jpg) 

You can leave the rest of the configuration at its default values.  Sample Usage :  

To scan a directory:  the syntax is:  `maldet -a <path_to_directory> ` 

For example:   

`# maldet -a /home/USERID/public_html `

 

It will report the number of files it had scanned, as well as the number of 'hits' (if malware is found) and the number of malware cleaned (if any)

![](images/00028.jpg) 

To view the report of the scan generated, type:

`# maldet --report <SCAN_ID> `

 

 To restore a file that has been quarantined:  

`# maldet --restore /usr/local/maldetect/quarantine/<FILENAME> `

 

Creating a daily cronjob to scan your files: 

When you first installed LMD, the installation script will create a daily cronjob at `/etc/cron.daily/maldet ` 

 

The file paths for the following control-panels are supported/built-in:

  

*   > Cpanel 
    
*   > Plesk (PSA) 
    
*   > Ensim 
    
*   > DirectAdmin 
    
*   > Default Apache DocRoot (/var/www/html) 
    

 

The file paths setup in Virtualmin is similar to Cpanel – so you don't have to make any changes to the script.

 

NOTE: You may have noticed that maldet uses the question mark (?) instead of the usual asterix (\*) to denote wildcard. For example, if you want to scan all the user-accounts under the /home/ directory, you would use:

 

`# maldet -a /home/?/public_html` 

 

note: The “?” denotes the wildcard characteristics  instead of the typical \*   

 

Chapter 9: Where to go from here?

We have covered a lot of ground in this short book. The various code snippets that you see here are the results of many man-hours of research, testing and debugging.

 

While there are many ways to achieve a certain goal, I've done my best follow the age-old UNIX principle of “K.I.S.S” (Keep It Super Simple) and give you the simplest and easiest way to achieve the goal of setting up an automated PHP-FPM server in Virtualmin.

 

But having said that, remember that technology is always changing, and by the time you're reading this, some things may have already changed.

 

To keep abreast with the latest changes and updates in Virtualmin – check out the official website from time to time – [http://virtualmin.com](http://virtualmin.com/).

 

Script/Software Download.

 

You can download the source code and scripts here: [http://ilovevirtualmin.com/book-2](http://ilovevirtualmin.com/book-2) 

 

You will need to enter this “Access Code”:   VMPHP2014

 

to access the download files.

 

This page will also contain all the relevant updates and book errata found.

Did you benefit from this book? 

 

If you have benefited from this book, please consider leaving a review at Amazon so that it will help others who are looking for a similar PHP-FPM solution in Virtualmin. You can click on the link below to go directly to the book:

 

[http://ilovevirtualmin.com/book-comments/book2.php](http://ilovevirtualmin.com/book-comments/book-2.php) 

 

If there is anything lacking in this book, or if you think I should cover more grounds, do let me know as it will help me improve this book in the next edition.  

![](images/00050.jpg) 

You contact me at: [`adrian.ling@gmail.com`](mailto:adrian.ling@gmail.com) 

 

Other Books in the “Practical Guide Series”

1\. “Webmin & Virtualmin:  The Best Open-Source Alternative to Cpanel”  - this is a newbie friendly book for those who are not familiar with Webmin & Virtualmin's interface.

![](images/00001.jpg) 

For example, in Cpanel, the term “addon domain” is known as a “Sub-server” in Virtualmin.  This book will help you get up to speed quickly.

 

This is the book that I wished I had when I moved from Cpanel/WHM to Virtualmin. If you're wondering why I decided to move away from Cpanel, well, the main reason is that Webmin/Virtualmin is a lot more powerful and flexible compared to Cpanel/WHM.

 

You've seen this for yourself in this book – where we can easily add automated PHP-FPM support into Virtualmin even though it's not officially supported.

 

We can also create “extra admins” - for certain roles – for example, if we need to hire a DBA to tweak our MySQL server, we can create an “Extra Admin” with access to the MySQL server only and nothing else.  We cannot do this in Cpanel/WHM.  

 

And of course, not having to pay a monthly license fee to use Virtualmin is a big added bonus :-)

 

If you want to know more about this powerful Control Panel, check it out here: [http://ilovevirtualmin.com/go/book1.php](http://ilovevirtualmin.com/go/book1.php) 

 

2\. “Apache, PHP-FPM & Nginx: How to Build A Secure, Fast and Powerful Web-Server” 

This is my 3rd book in the “Practical Guide” series – which is scheduled to be published on 30th November 2014.  This book will guide you through the setting up of PHP-FPM on a stock CentOS server – how to upgrade from the default PHP 5.3.3 to the current stable PHP 5.4.x, how to setup automated PHP-FPM pools for each individual virtual-servers and more importantly, how to secure PHP-FPM on your server so that your users cannot use it to “snoop” and view sensitive system files such as the /etc/passwd!

 

Not many people know this, but nearly all web-hosting servers come with the default PHP settings which is NOT secure!  

 

Anyone with a little  php coding skills can quickly cobble a script to view sensitive system files – such as the /etc/passwd file.  

 

Let me show you the  screenshot of the content of the /etc/passwd file:

![](images/00048.jpg) 

The PHP code to do this is only 3 lines!  

If I'm a malicious hacker, I will target the user 'pony' because he has 'shell' access whereas the user 'donkey' does not.

 

This book will show you the above was done, and how you as the system administrator can prevent it from happening to your own server.

There will be a chapter on performance turning with 2 mini-case studies on the “ideal” settings in the PHP-FPM pool file.

 

You can pre-order this book now: [http://ilovevirtualmin.com/go/book3.php](http://ilovevirtualmin.com/go/book3.php)