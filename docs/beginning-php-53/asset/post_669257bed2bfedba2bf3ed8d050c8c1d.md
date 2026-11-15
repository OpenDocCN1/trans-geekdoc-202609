
allow_url_fopen turns these wrappers on or off, and allow_url_include controls whether you can include code using include()/require() (which is a potential security risk). from defines the FTP password to use for anonymous access to ftp:// URLs, and user_agent sets the HTTP User-Agent header that is sent when PHP requests the URL. default_socket_timeout specifies how long PHP will wait when attempting to open a URL before it gives up. Finally, auto_detect_line_endings ensures that the line endings in files created on a different operating system — whether Windows, Mac OS, or UNIX — are interpreted correctly.

```
;;;;;;;;;;;;;;;;;;;;;;;
; Fopen wrappers ;
;;;;;;;;;;;;;;;;;;;;;;;

; Whether to allow the treatment of URLs (like http:// or ftp://) as files.
; http://php.net/allow-url-fopen
allow_url_fopen = On

; Whether to allow include/require to open URLs (like http:// or ftp://) as files.
; http://php.net/allow-url-include
allow_url_include = Off

; Define the anonymous ftp password (your email address). PHP's default setting
; for this is empty.
; http://php.net/from
;from="john@doe.com"

; Define the User-Agent string. PHP's default setting for this is empty.
; http://php.net/user-agent
;user_agent="PHP"

; Default timeout for socket based streams (seconds)
; http://php.net/default-socket-timeout
default_socket_timeout = 60

; If your scripts have to deal with files from Macintosh systems,
; or you are running on a Mac and need to deal with files from
; unix or win32 systems, setting this flag will cause PHP to
; automatically detect the EOL character in those files so that
; fgets() and file() will work regardless of the source of the file.
; http://php.net/auto-detect-line-endings
;auto_detect_line_endings = Off
```

## Dynamic Extensions

The PHP engine is really composed of two parts — the core engine and extension modules. Some extensions are built in, whereas others are stored in separate library files (ending in .so or .dll) and need to be loaded dynamically, either using the dl() function from within a script, or by loading them when PHP starts. To load an extension when PHP starts, add its filename to this section (or uncomment it if it’s already listed).

## Appendix B: Configuring PHP

Extension modules need to be stored in the extension directory, which is specified with the extension_dir directive in the Paths and Directories section.

```
;;;;;;;;;;;;;;;;;;;;;;;;;
; Dynamic Extensions ;
;;;;;;;;;;;;;;;;;;;;;;;;;
; If you wish to have an extension loaded automatically, use the following
; syntax:
; extension=modulename.extension
;
; For example, on Windows:
;
; extension=msql.dll
;
; ... or under UNIX:
;
; extension=msql.so
;
; ... or with a path:
;
; extension=/path/to/extension/msql.so
;
; If you only provide the name of the extension, PHP will look for it in its
; default extension directory.
;
; Windows Extensions
; Note that ODBC support is built in, so no dll is needed for it.
; Note that many DLL files are located in the extensions/ (PHP 4) ext/ (PHP 5)
; extension folders as well as the separate PECL DLL download (PHP 5).
; Be sure to appropriately set the extension_dir directive.
;
;extension=php_bz2.dll
;extension=php_curl.dll
;extension=php_dba.dll
;extension=php_exif.dll
;extension=php_fileinfo.dll
;extension=php_gd2.dll
;extension=php_gettext.dll
;extension=php_gmp.dll
;extension=php_intl.dll
;extension=php_imap.dll
;extension=php_interbase.dll
;extension=php_ldap.dll
;extension=php_mbstring.dll
;extension=php_ming.dll
;extension=php_mssql.dll
;extension=php_mysql.dll
;extension=php_mysqli.dll
;extension=php_oci8.dll ; Use with Oracle 10gR2 Instant Client
;extension=php_oci8_11g.dll ; Use with Oracle 11g Instant Client
;extension=php_openssl.dll
;extension=php_pdo_firebird.dll
;extension=php_pdo_mssql.dll
;extension=php_pdo_mysql.dll
;extension=php_pdo_oci.dll
;extension=php_pdo_odbc.dll
;extension=php_pdo_pgsql.dll
;extension=php_pdo_sqlite.dll
;extension=php_pgsql.dll
;extension=php_phar.dll
;extension=php_pspell.dll
;extension=php_shmop.dll
;extension=php_snmp.dll
;extension=php_soap.dll
;extension=php_sockets.dll
;extension=php_sqlite.dll
;extension=php_sqlite3.dll
;extension=php_sybase_ct.dll
;extension=php_tidy.dll
;extension=php_xmlrpc.dll
;extension=php_xsl.dll
;extension=php_zip.dll
```

### Module Settings

The last (and longest) section of the php.ini file lets you configure each extension module, whether built-in or dynamically loaded. Each extension's configuration is grouped into a section starting with the extension name in square brackets (for example, [sqlite]). Each configuration directive is defined in the normal way:

```
directive_name = directive_value
```

Here are the default module settings as included in php.ini-development. (Note that just because a certain module is configured here, it doesn't necessarily mean that the module is loaded.)

## Appendix B: Configuring PHP

```
;;;;;;;;;;;;;;;;;;;
; Module Settings ;
;;;;;;;;;;;;;;;;;;;

[Date]
; Defines the default timezone used by the date functions
; http://php.net/date.timezone
;date.timezone =

; http://php.net/date.default-latitude
;date.default_latitude = 31.7667

; http://php.net/date.default-longitude
;date.default_longitude = 35.2333

; http://php.net/date.sunrise-zenith
;date.sunrise_zenith = 90.583333

; http://php.net/date.sunset-zenith
;date.sunset_zenith = 90.583333

[filter]
; http://php.net/filter.default
;filter.default = unsafe_raw

; http://php.net/filter.default-flags
;filter.default_flags =

[iconv]
;iconv.input_encoding = ISO-8859-1
;iconv.internal_encoding = ISO-8859-1
;iconv.output_encoding = ISO-8859-1

[intl]
;intl.default_locale =

[sqlite]
; http://php.net/sqlite.assoc-case
;sqlite.assoc_case = 0

[sqlite3]
sqlite3.extension_dir =

[Pcre]
;PCRE library backtracking limit.
; http://php.net/pcre.backtrack-limit
;pcre.backtrack_limit=100000

;PCRE library recursion limit.
;Please note that if you set this value to a high number you may consume all
the available process stack and eventually crash PHP (due to reaching the
stack size limit imposed by the Operating System).
; http://php.net/pcre.recursion-limit
;pcre.recursion_limit=100000

[Pdo]
; Whether to pool ODBC connections. Can be one of "strict", "relaxed" or "off"
; http://php.net/pdo-odbc.connection-pooling
pdo_odbc.connection_pooling=strict

;pdo_odbc.db2_instance_name

[Pdo_mysql]
; If mysqlnd is used: Number of cache slots for the internal result set cache
; http://php.net/pdo_mysql.cache_size
pdo_mysql.cache_size = 2000

; Default socket name for local MySQL connects. If empty, uses the built-in
; MySQL defaults.
; http://php.net/pdo_mysql.default-socket
pdo_mysql.default_socket=

[Phar]
; http://php.net/phar.readonly
;phar.readonly = On

; http://php.net/phar.require-hash
;phar.require_hash = On

;phar.cache_list =

[Syslog]
; Whether or not to define the various syslog variables (e.g. $LOG_PID,
; $LOG_CRON, etc.). Turning it off is a good idea performance-wise. In
; runtime, you can define these variables by calling define_syslog_variables().
; http://php.net/define-syslog-variables
define_syslog_variables = Off

[mail function]
; For Win32 only.
; http://php.net/smtp
SMTP = localhost
; http://php.net/smtp-port
smtp_port = 25

; For Win32 only.
; http://php.net/sendmail-from
;sendmail_from = me@example.com

; For Unix only. You may supply arguments as well (default: "sendmail -t -i").
; http://php.net/sendmail-path
;sendmail_path =

; Force the addition of the specified parameters to be passed as extra parameters
; to the sendmail binary. These parameters will always replace the value of
; the 5th parameter to mail(), even in safe mode.
;mail.force_extra_parameters =

; Add X-PHP-Originating-Script: that will include uid of the script followed by the filename
mail.add_x_header = On

; Log all mail() calls including the full path of the script, line #, to address and headers
;mail.log =

[SQL]
; http://php.net/sql.safe-mode
sql.safe_mode = Off

[ODBC]
; http://php.net/odbc.default-db
;odbc.default_db = Not yet implemented
```
