
# Introduction and Installation of PHP 7.3

## Downloading and Installing PHP 7.3 for Windows

This section provides a tutorial example on how to download and install the PHP engine 7.0 on a Windows system.

1. Go to [windows.php.net/download/](http://windows.php.net/download/) and download the "VC15 x64 Thread Safe (2018-Dec-06 04:31:24)" binary version for Windows. You will get a file called `php-7.3.0-Win32-VC15-x64` of 21,846,474 bytes.

2. Unzip `php-7.3.0-Win32-VC15-x64` to `\php` folder.

3. Open a command window, and try the following commands:

```
herong> \php\php -v
```

4. If see an error message saying: "The program can't start because VCRUNTIME150.dll is missing from your computer. Try reinstalling the program to fix this problem.", you need to install "Visual Studio 2015 x86".

* Go to "Microsoft Visual C++ Redistributable for Visual Studio 2015" page at [microsoft.com/en-us/download/details.aspx?id=48145](https://www.microsoft.com/en-us/download/details.aspx?id=48145).
* Click the "Download" button.
* Save the download file `vc_redist.x86.exe` to desktop.
* Double-click on `vc_redist.x86.exe` to run it.
* Follow instruction to finish installation.

5. Open a command window, and try the following commands again:

```
herong> \php\php -v

PHP 7.3.0 (cli) (built: Dec  6 2018 01:54:19)
   (ZTS MSVC15 (Visual C++ 2017) x64)
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.3.0-dev, Copyright (c) 1998-2018 Zend Technologies
```

Cool, both Command Line Interface (CLI) and Common Gateway Interface (CGI) of PHP are working!

## "php -help" - Command Line Options

This section provides a tutorial example on how to see all command line options supported by the PHP engine: `php -help`.

If you want to know what command line options are supported by the PHP engine, you can run PHP with the `-help` option:

```
herong> \php\php -help

Usage: php [options] [-f] <file> [--] [args...]
   php [options] -r <code> [--] [args...]
   php [options] [-B <begin_code>] -R <code> [-E <end_code>] [--] [args...]
   php [options] [-B <begin_code>] -F <file> [-E <end_code>] [--] [args...]
   php [options] -- [args...]
   php [options] -a

  -a               Run interactively
  -c <path>|<file> Look for php.ini file in this directory
  -n               No php.ini file will be used
  -d foo[=bar]     Define INI entry foo with value 'bar'
  -e               Generate extended information for debugger/profiler
  -f <file>        Parse and execute <file>.
  -h               This help
  -i               PHP information
  -l               Syntax check only (lint)
  -m               Show compiled in modules
  -r <code>        Run PHP <code> without using script tags <?..?>
  -B <begin_code>  Run PHP <begin_code> before processing input lines
  -R <code>        Run PHP <code> for every input line
  -F <file>        Parse and execute <file> for every input line
  -E <end_code>    Run PHP <end_code> after processing all input lines
  -H               Hide any passed arguments from external tools.
  -S <addr>:<port> Run with built-in web server.
  -t <docroot>     Specify document root <docroot> for built-in web server.
  -s               Output HTML syntax highlighted source.
  -v               Version number
  -w               Output source with stripped comments and whitespace.
  -z <file>        Load Zend extension <file>.

  args...          Arguments passed to script. Use -- args when first argument
                   starts with - or script is read from stdin

  --ini            Show configuration file names

  --rf <name>      Show information about function <name>.
  --rc <name>      Show information about class <name>.
  --re <name>      Show information about extension <name>.
  --rz <name>      Show information about Zend extension <name>.
  --ri <name>      Show configuration for extension <name>.
```

## "php -m" - Built-in Modules

This section provides a tutorial example on how to get a list of all modules that are pre-compiled in the PHP engine: `php -m`.

The Windows binary version of PHP 7.3 engine comes with many modules pre-compiled into the engine. The `-m` option can give you a list of all built-in modules:

```
herong> \php\php -m

[PHP Modules]
bcmath
calendar
Core
ctype
date
dom
filter
hash
iconv
json
libxml
mysqlnd
pcre
PDO
Phar
readline
Reflection
session
SimpleXML
SPL
standard
tokenizer
wddx
xml
xmlreader
xmlwriter
zip
zlib

[Zend Modules]
```

## "php -i" - PHP Engine Information

This section provides a tutorial example on how to get more information about the PHP engine and its execution environment: `php -i`.

If you want to know more information about the PHP engine and its execution environment you run the `php.exe` program with the `-i` option:

```
herong> \php\php -i

phpinfo()
PHP Version => 7.3.0

System => Windows NT Local 6.1 build 7601 (Windows 7 Professional ...
Build Date => Dec  6 2018 01:48:44
Compiler => MSVC15 (Visual C++ 2017)
Architecture => x64
Configure Command => cscript /nologo configure.js  "--enable-snaps...
Server API => Command Line Interface
Virtual Directory Support => enabled
Configuration File (php.ini) Path => C:\windows
Loaded Configuration File => (none)
Scan this dir for additional .ini files => (none)
Additional .ini files parsed => (none)
PHP API => 20180731
PHP Extension => 20180731
Zend Extension => 320180731
Zend Extension Build => API320180731,TS,VC15
PHP Extension Build => API20180731,TS,VC15
Debug Build => no
Thread Safety => enabled
Zend Signal Handling => disabled
Zend Memory Manager => enabled
Zend Multibyte Support => disabled
IPv6 Support => enabled
DTrace Support => disabled

Registered PHP Streams => php, file, glob, data, http, ftp, zip, ...
Registered Stream Socket Transports => tcp, udp
Registered Stream Filters => convert.iconv.*, mcrypt.*, mdecrypt....

This program makes use of the Zend Scripting Language Engine:

...
```

## php.ini - PHP Runtime Configuration

This section describes the PHP runtime configuration file, `php.ini`.

PHP runtime behavior can be controlled by a runtime configuration file called `php.ini` in the `\php` folder. The PHP installation package provides 2 versions of `php.ini`:

```
php.ini-development   - More secure and better performance
php.ini-production    - More verbose in error messages
```

Since we are running PHP on a local machine to learn the PHP language, we should use the `php.ini-development` version. So let's copy `php.ini-development` to `php.ini`:

```
>copy \php\php.ini-development \php\php.ini
        1 file(s) copied.

>type \php\php.ini | more
[PHP]

;;;;;;;;;;;;;;;;;;;
; About php.ini   ;
;;;;;;;;;;;;;;;;;;;
; PHP's initialization file, generally called php.ini, is responsible
; for configuring many of the aspects of PHP's behavior.
; ...

; Name for user-defined php.ini files. Default is ".user.ini"
;user_ini.filename = ".user.ini"

; To disable this feature set this option to empty value
;user_ini.filename =

; TTL for user-defined php.ini files (time-to-live) in seconds.
; Default is 300 seconds (5 minutes)
;user_ini.cache_ttl = 300

; Enable the PHP scripting language engine under Apache.
engine = On

...
```

As you can see the `php.ini` file is very easy to use. The `;` character at the beginning of the line indicates a comment line. Configuration settings are provided in the format of `name = value`. The default version of `php.ini` comes with lots of comments to help you understaning what is the meaning of each setting.
