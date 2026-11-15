The following installation description is based on a system that does not yet have a PHP installation. The variant shown here is based on the new description in the PHP online documentation, as this offers the best and fastest updatability. PHP is only kept centrally in one folder here, whereas in the previous installations the php.ini file always ended up in the Windows directory, and other extensions either had to be copied there as well or (not recommended) to System32.

> **Note**
> For use with the IIS, the non-thread-safe (NTS) version of PHP is recommended for the CGI variant. In general, the FastCGI version is almost exclusively used for performance reasons.

To install PHP, follow these steps:

+   1. Download the ZIP file with the Windows binaries for PHP 8.3. You can find the Windows downloads at [http://windows.php.net/download](http://windows.php.net/download). You must use the non-thread-safe version and decide whether it should run on an x86 or x64 system. You also need the Visual C++ Redistributable for Visual Studio 2019 package (or Visual C++ Redistributable for Visual Studio 2022 for PHP 8.4) to run PHP—indicated by a small and easily overlooked note on the download page. You can find it at [http://s-prs.co/v602204](http://s-prs.co/v602204), where you must select the processor architecture (32-bit or 64-bit) in which you also want to install PHP.

+   2. Create a new folder for PHP. The default we assume here is C:\\php.

+   3. Unpack the contents of the ZIP file into this folder. Caution: the ZIP no longer automatically contains a php folder! This is why we created it in the previous step.

+   4. Here is a brief inventory: The CGI version of PHP is called php-cgi.exe, not php.exe. The latter, php.exe, is the console version, which is already in the main folder of PHP by default. The SAPI file is php8.dll. However, it is no longer recommended for use with the IIS, as mentioned earlier. The php.ini file is only available in the standard package, as explained earlier, in the form of two templates: php.ini-development and php.ini-production. The former is designed more for test systems, the latter for a production system. However, you will usually have to make your own changes.

+   5. Rename one of the two supplied php.ini template files to php.ini.

+   6. In the next step, you should make it clear to Windows that the php-cgi.exe PHP module and php.ini are located in the main PHP directory (here: C:\\php). Although this is not absolutely necessary, it often makes control easier, especially in conjunction with extensions. This step requires setting a new environment variable:
+   – Switch to Environment Variables via Control Panel • System • System and Security • Advanced System Settings.
+   – Edit the Path entry under Environment Variables • System variables.