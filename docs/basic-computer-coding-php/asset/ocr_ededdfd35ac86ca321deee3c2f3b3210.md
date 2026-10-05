# Basic Computer Coding: PHP

# AddModule

You must uncomment this line for the static module version of Apache.

AddModule mod_php4.c

# 1.2.3 PHP.INI File Configuration

The PHP configuration file, php.ini, is the final and most immediate way to affect PHP's functionality. The php.ini file is read each time PHP is initialized.in other words, whenever httpd is restarted for the module version or with each script execution for CGI version. If your change isn't showing up, remember to stop and restart httpd. If it still isn't showing up, use phpinfo() to check the path to php.

The configuration file is well commented and thorough. Keys are case sensitive, keyword values are not; whitespace, and lines beginning with semicolons are ignored. Booleans can be represented by 1/0, Yes/No, On/Off, or True/False. The default values in php.ini-dist result in a reasonable PHP installation that can be tweaked later.

Here we are explaining the important settings in php.ini which you may need for your PHP Parser.

# short_open_tag = Off

Short open tags look like this: <?? ?>. This option must be set to On if you want to use XML functions.

# safe_mode = Off

If this is set to On, you probably compiled PHP with the --enable-safe-mode flag. Safe mode is most relevant to CGI use. See the explanation in the section “CGI compile-time options”, earlier in this chapter.

# safe_mode_exec_dir = [DIR]

This option is relevant only if safe mode is on; it can also be set with the --exec-dir flag during the Unix build process. PHP in safe mode only executes external binaries out of this directory.