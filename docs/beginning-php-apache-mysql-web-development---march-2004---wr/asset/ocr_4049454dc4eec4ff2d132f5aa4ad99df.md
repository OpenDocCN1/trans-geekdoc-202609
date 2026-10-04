# Introduction and Installation Configuration

# Customizing Your Installation

The configuration file holds the key to how your PHP runs on your computer php.ini; it can be found in the root directory where you extracted your installation files. For the purposes of our discussion, assume you have extracted the files to c:\ and renamed the installation directory to c:\php\.

The php.ini file includes a brief explanation of each of the configuration settings, which are beyond the scope of this discussion. However, you are encouraged to read through the entire introduction of the php.ini file before you making changes. In the table below, we touch on some of the more commonly changed settings.

| Setting | What It Does |
|---|---|
| short_open_tag | Allows short tags to be parsed (<? ?> as opposed to <?php and ?>)|
| asp_tags | Allows ASP-style tags to be parsed (<% %) |
| precision | Determines the number of digits to be displayed in floating point numbers. Default is 12, and this should suffice for most applications. |
| output_buffering | Allows headers to be sent after HTML. The default is "Off," and most third-party hosts maintain this default. It is not advisable to change this setting, especially if you depend on a third-party host |
| max_execution_time | Sets the limit for how long a script can take to run. Expressed in seconds. |
| max_input_time | Sets the limit for how long a script can take to parse the data. Expressed in seconds. |
| memory_limit | Sets the limit for how much memory a script can use. Expressed in MB. |
| error_reporting | There are many levels you can use to set what errors will be shown to you, for the purposes of our book, we assume that error_reporting is set to E_ALL. When set to E_ALL, all errors and warnings are shown |
| display_errors | Determines whether or not errors will be printed. Let's leave this on while you develop your site and learn PHP, but once the site is ready to live, we recommend that you switch this to "off" for security purposes |
| log_errors | Allows errors to be written into a log file for future reference. We recommend that you switch this setting to "on." |
| error_log | Points to the name of your PHP error log file. |

Table continued on following page

19