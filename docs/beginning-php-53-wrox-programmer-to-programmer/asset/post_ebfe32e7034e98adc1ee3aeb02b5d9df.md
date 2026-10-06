
# Appendix B: Configuring PHP

```
; Directory in which the loadable extensions (modules) reside.
; http://php.net/extension-dir
; extension_dir = ".*"
; On windows:
; extension_dir = "ext"
```

; Whether or not enable the dl() function. The dl() function does not work
; properly in multithreaded servers, such as IIS or Zeus, and is
automatically
 disabled on them.
; http://php.net/enable-dl
enable_dl = Off

; cgi_redirect is necessary to provide security running PHP as a CGI
under
; most servers. Left undefined, PHP turns this off by default. You can
; turn it off AT YOUR OWN RISK
; **You can safely turn this off in IIS, but you must.**
; http://php.net/cgi.force-redirect
cgi.force_redirect = 1

; cgi.nph is enabled it will enable cgi to always set Status: 200 with
; every request. PHP's default behavior is to disable this feature.
; cgi.nph = 1

; cgi.force_redirect is turned, and you are not running under Apache or
Netscape
; (Internet) web servers, you MAY need to set an environment variable name
that PHP
; will look for to know it is OK to continue execution. Setting this
variable MAY
; security issues, KNOW WHAT YOU ARE DOING FIRST.
; http://php.net/cgi.redirect-status-env
cgi.redirect_status_env = 

; cgi.fix_pathinfo provides *real* PATH_INFO/PATH_TRANSLATED support for CGI,
PHP's
; previous behaviour was to set PATH_TRANSLATED to SCRIPT_FILENAME, and
not grok
; what PATH_INFO is. For more information on PATH_INFO, see the cgi specs
Setting
; this to 1 will cause PHP to fix its paths to the spec. A
; of zero causes PHP to behave as before. You should fix your
scripts
; to use SCRIPT_FILENAME rather than PATH_TRANSLATED.
; http://php.net/cgi.fix-pathinfo
cgi.fix_pathinfo = 1

; FastCGI under IIS (on WINDOW based) supports the ability to impersonate
; security tokens of the calling client. This allows IIS to define the
```
; security context that the request runs under. mod_fastcgi Apache
; does not currently support this feature (03/17/2002)
; Set to 1 if running IIS. Default is zero.
; http://php.net/fastcgi.impersonate
; fastcgi.impersonate = 1;
```

```
; Disable logging through FastCGI connection. PHP's default behavior is to
enable
; this feature.
; fastcgi.logging = 0
```

```
; cgi.rfc2616 headers configuration option tells PHP what type of headers to
; use when sending HTTP response code. If it's set 0 PHP Status: header
that
; it is supported by Apache. When this is set to 1 PHP will send
; RFC2616 compliant header.
; Default is zero.
; http://php.net/cgi.rfc2616-headers
; cgi.rfc2616_headers = 0
```

# File Uploads

This section contains settings for HTTP file uploads, as described in "Creating File Upload Forms" in Chapter 9. file_uploads turns file upload capability off or on. upload_tmp_dir specifies where to store uploaded files temporarily until they are merged by the script. upload_max_filesize sets an upper limit on the size of an uploaded file (this limit is also governed by post_max_size in the Data Handling section). Increase this value if you need your visitors to be able to upload larger files.

- File Uploads
- Whether to allow HTTP file uploads.
  file_uploads = On
- Temporary directory for HTTP uploaded files (will use system default if not
  specified);
  upload_tmp_dir = 
- Maximum allowed size for uploaded files.
  upload_max_filesize = 2M

# Fopen Wrappers

As you saw in Chapter 11, you can use fopen() to open not just files on the Web server, but also read
remote URLs and treat them like files. Similarly, you can use functions like include() and require()
to include PHP code from a URL in your script.
Opening URLs use a protocol handler — also known as wrapper — and you can configure these
wrappers in this section.

```
;;;;;;;;;;;;;;;;
; Fopen wrappers :
;;;;;;;;;;;;;;;;
```

- Whether to allow the treatment of URLs (http:// or ftp://) as files.
; http://php.net/allow-url-fopen
allow_url_fopen = On

- Whether to include/require to open URLs (http:// or ftp://) as files.
; http://php.net/allow-url-include
allow_url_include = Off

- Define the anonymous password (your email address). PHP's default setting
for this is empty.
; http://php.net/from
from="john@doe.com"

- Define the User-Agent string. PHP's default setting for this is empty.
; http://php.net/user-agent
user_agent="PHP"

- Define timeout for socket based streams (seconds)
; http://php.net/default-socket-timeout
default_socket_timeout = 60

- If your scripts have to deal with files from Macintosh systems,
or you are running on Mac or win32 systems, this flag will cause PHP to
automatically detect the EOL character in those files so that
fgets(file) works regardless of the source of the file.
; http://php.net/auto-detect-endpoints
auto_detect_endpoints = off

# Dynamic Extensions

The PHP engine is really composed of two parts — the engine and extension modules. Some extensions are built in, whereas others are stored in separate library files (ending in .so or .dll) and need to be loaded dynamically, either using the dl() function within a script, or by loading them when PHP starts. To load an extension when PHP starts, add its filename to this section (or uncomment it if it's already listed). Extension modules need to be stored in the extension directory, which is specified with the extension_dir directive in the Paths and Directories section.

```
;;;;;;;;;;;;;;;;
; Dynamic Extensions ;
;;;;;;;;;;;;;;;;
```

- If you wish to have an extension loaded automatically, use the following
syntax:
; extension=modulename.extension
; For example, on Windows:
extension=msql.dll
; ... or under UNIX:
extension=msql.so
; or with a path:
extension=path/to/extension/msql.so
; If you only provide the name of the extension, PHP will look for it in its
default extension directory.

; Windows Extensions
; Note that ODBC server is built in, so no dll is needed for it.
Note that many DLL files are located in the extensions/ (PHP 4) ext/ (PHP 5
folders as well as the separate DLL download (PHP 5). Be sure to appropriately set the extension_dir directive.
extension=php_bz2.dll
extension=php_curl.dll
extension=php_dba.dll
extension=php_exif.dll
extension=php_fileinfo.dll
extension=php_gd.dll
extension=php_gettext.dll
extension=php_gmp.dll
extension=php_intl.dll
extension=php_imap.dll
extension=php_interbase.dll
extension=php_ldap.dll
extension=php_mbstring.dll
extension=php_mysqli.dll
extension=php_msql.dll
extension=php_mysql.dll
extension=php_mysqli.dll      ; Use with Oracle 10gr2 Instant Client
extension=php_occi18_dll      ; Use with Oracle 11g Instant Client
extension=php_openssl.dll
extension=php_pdo_firebird.dll
```

```
extension=php_pdo_mysqli.dll
extension=php_pdo_mysql.dll
extension=php_pdo_oci.dll
extension=php_pdo_odbc.dll
extension=php_pdo_pgsql.dll
extension=php_pdo_sqlite.dll
extension=php_pgsqlql.dll
extension=php_dban.dll
extension=php_pspell.dll
extension=php_shmop.dll
extension=php_snmp.dll
extension=php_soap.dll
extension=php_sockets.dll
extension=php_sqlite.dll
extension=php_sqlite3.dll
extension=php_sybase_ct.dll
extension=php_tidy.dll
extension=php_xmlrpc.dll
extension=php_xsl.dll
extension=php_zip.dll
```

# Module Settings

The last (and longest) section of the php.ini files lets you configure each extension module, whether built-in or dynamically loaded. Each extension's configuration is grouped into a section starting with the extension name in brackets (for example, [sqlite]). Each configuration directive is defined in the normal way:

```
directive_name = directive_value
```

Here are the default module settings as included in php.ini-development. (Note that because a certain module is configured here, it doesn't necessarily mean the module is loaded.)

```
;;;;;;;;;;;;;;;;
; Module Settings ;
;;;;;;;;;;;;;;;;
```

[Date]
; Defines the default timezone used by the date functions
; http://php.net/date.timezone
;date.timezone =
```

```
; http://php.net/date.default-latitude
;date.default_latitude = 31.7667
```

```
; http://php.net/date.default-longitude
;date.default_longitude = 35.2333
```

```
; http://php.net/date.sunrise-zenith
;date.sunrise_zenith = 90.583333
```
