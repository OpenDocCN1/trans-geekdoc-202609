
; runs. $argv contains an array of all the arguments passed to PHP when a script
; is invoked. $argc contains an integer representing the number of arguments
; that were passed when the script was invoked. These arrays are extremely
; useful when running scripts from the command line. When this directive is
; enabled, registering these variables consumes CPU cycles and memory each time
; a script is executed. For performance reasons, this feature should be disabled
; on production servers.
; Note: This directive is hardcoded to On for the CLI SAPI
; Default Value: On
; Development Value: Off
; Production Value: Off
; http://php.net/register-argc-argv
register_argc_argv = Off

; When enabled, the SERVER and ENV variables are created when they're first
; used (Just In Time) instead of when the script starts. If these variables
; are not used within a script, having this directive on will result in a
; performance gain. The PHP directives register_globals, register_long_arrays,
; and register_argc_argv must be disabled for this directive to have any effect.
; http://php.net/auto-globals-jit
auto_globals_jit = On

; Maximum size of POST data that PHP will accept.
; http://php.net/post-max-size
post_max_size = 8M

; Magic quotes are a preprocessing feature of PHP where PHP will attempt to
; escape any character sequences in GET, POST, COOKIE and ENV data which might
; otherwise corrupt data being placed in resources such as databases before
; making that data available to you. Because of character encoding issues and
; non-standard SQL implementations across many databases, it's not currently
; possible for this feature to be 100% accurate. PHP's default behavior is to
; enable the feature. We strongly recommend you use the escaping mechanisms
; designed specifically for the database your using instead of relying on this
; feature. Also note, this feature has been deprecated as of PHP 5.3.0 and is
; scheduled for removal in PHP 6.
; Default Value: On
; Development Value: Off
; Production Value: Off
; http://php.net/magic-quotes-gpc
magic_quotes_gpc = Off

; Magic quotes for runtime-generated data, e.g. data from SQL, from exec(), etc.
; http://php.net/magic-quotes-runtime
magic_quotes_runtime = Off

; Use Sybase-style magic quotes (escape ' with '' instead of \').
; http://php.net/magic-quotes-sybase
magic_quotes_sybase = Off

; Automatically add files before PHP document.
; http://php.net/auto-prepend-file
auto_prepend_file =

```
; Automatically add files after PHP document.
; http://php.net/auto-append-file
auto_append_file =
```

```
; By default, PHP will output a character encoding using
; the Content-type: header. To disable sending of the charset, simply
; set it to be empty.
;
; PHP's built-in default is text/html
; http://php.net/default-mimetype
default_mimetype = "text/html"
```

```
; PHP's default character set is set to empty.
; http://php.net/default-charset
;default_charset = "iso-8859-1"
```

```
; Always populate the $HTTP_RAW_POST_DATA variable. PHP's default behavior is
; to disable this feature.
; http://php.net/always-populate-raw-post-data
;always_populate_raw_post_data = On
```

## Paths and Directories

Along with various security and other miscellaneous settings, this section specifies the default value for include_path. (See the section “Writing Modular Code” in Chapter 20 for more on include paths.)

;;;;;;;;;;;;;;;;;;;;;;;;;
; Paths and Directories ;
;;;;;;;;;;;;;;;;;;;;;;;;;

; UNIX: "/path1:/path2"
;include_path = ".:/php/includes"
;
; Windows: "\path1;\path2"
;include_path = ".;c:\\php\\includes"
;

; PHP's default setting for include_path is ".;/path/to/php/pear"
; http://php.net/include-path

; The root of the PHP pages, used only if nonempty.
; if PHP was not compiled with FORCE_REDIRECT, you SHOULD set doc_root
; if you are running php as a CGI under any web server (other than IIS)
; see documentation for security issues. The alternate is to use the
; cgi.force_redirect configuration below
; http://php.net/doc-root
doc_root =

; The directory under which PHP opens the script using /~username used only
; if nonempty.
; http://php.net/user-dir
user_dir =

; Directory in which the loadable extensions (modules) reside.
; http://php.net/extension-dir
; extension_dir = "./"
; On windows:
; extension_dir = "ext"

; Whether or not to enable the dl() function. The dl() function does NOT work
; properly in multithreaded servers, such as IIS or Zeus, and is automatically
; disabled on them.
; http://php.net/enable-dl
enable_dl = Off

; cgi.force_redirect is necessary to provide security running PHP as a CGI under most web servers. Left undefined, PHP turns this on by default. You can turn it off here AT YOUR OWN RISK
; **You CAN safely turn this off for IIS, in fact, you MUST.**
; http://php.net/cgi.force-redirect
;cgi.force_redirect = 1

; if cgi.nph is enabled it will force cgi to always sent Status: 200 with every request. PHP's default behavior is to disable this feature.
;cgi.nph = 1

; if cgi.force_redirect is turned on, and you are not running under Apache or Netscape (iPlanet) web servers, you MAY need to set an environment variable name that PHP will look for to know it is OK to continue execution. Setting this variable MAY cause security issues, KNOW WHAT YOU ARE DOING FIRST.
; http://php.net/cgi.redirect-status-env
; cgi.redirect_status_env =

; cgi.fix_pathinfo provides *real* PATH_INFO/PATH_TRANSLATED support for CGI. PHP's previous behaviour was to set PATH_TRANSLATED to SCRIPT_FILENAME, and to not grok what PATH_INFO is. For more information on PATH_INFO, see the cgi specs. Setting this to 1 will cause PHP CGI to fix its paths to conform to the spec. A setting of zero causes PHP to behave as before. Default is 1. You should fix your scripts to use SCRIPT_FILENAME rather than PATH_TRANSLATED.
; http://php.net/cgi.fix-pathinfo
;cgi.fix_pathinfo=1

; FastCGI under IIS (on WINNT based OS) supports the ability to impersonate security tokens of the calling client. This allows IIS to define the security context that the request runs under. mod_fastcgi under Apache does not currently support this feature (03/17/2002)
; Set to 1 if running under IIS. Default is zero.
; http://php.net/fastcgi.impersonate
;fastcgi.impersonate = 1

; Disable logging through FastCGI connection. PHP's default behavior is to enable this feature.
;fastcgi.logging = 0

; cgi.rfc2616_headers configuration option tells PHP what type of headers to use when sending HTTP response code. If it's set 0 PHP sends Status: header that is supported by Apache. When this option is set to 1 PHP will send RFC2616 compliant header. Default is zero.
; http://php.net/cgi.rfc2616-headers
;cgi.rfc2616_headers = 0

## File Uploads

This section contains settings for HTTP file uploads, as described in “Creating File Upload Forms” in Chapter 9. file_uploads turns file upload capability off or on. upload_tmp_dir specifies where to store uploaded files temporarily until they’re moved by the script. upload_max_filesize sets an upper limit on the size of an uploaded file (note that this limit is also governed by post_max_size in the Data Handling section). Increase this value if you need your visitors to be able to upload larger files.

;;;;;;;;;;;;;;;
; File Uploads ;
;;;;;;;;;;;;;;;

; Whether to allow HTTP file uploads.
file_uploads = On

; Temporary directory for HTTP uploaded files (will use system default if not specified).
;upload_tmp_dir =

; Maximum allowed size for uploaded files.
upload_max_filesize = 2M

## Fopen Wrappers

As you saw in Chapter 11, you can use fopen() to open not just files on the Web server, but also read remote URLs and treat them like files. Similarly, you can use functions like include() and require() to include PHP code from a URL in your script.

Opening URLs uses a protocol handler — also known as a wrapper — and you can configure these wrappers in this section.
