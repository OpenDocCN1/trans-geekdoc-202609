```
; Order in which PHP environment, GET, POST, cookie, server and custom
; variables are registered in $_REQUEST
request_order = "GP"
; Specifies whether GET variables should be saved in argv and argc (only
possible if auto_globals_jit is not activated)
register_argc_argv = Off
; Specifies whether environment, server and request variables should only be
created on first use
auto_globals_jit = On
; Maximum size of POST data (there is a separate setting for uploads!)
post_max_size = 8M
; Append/execute a file before/after each PHP script
auto_prepend_file =
auto_append_file =
; Value for the Content-Type HTTP header
default_mimetype = "text/html"
; Character set for the HTTP header
default_charset = "UTF-8"
```

PHP does not offer integrated project management, so in the sense of a modular application, a lot of work is done with external files. The Paths and Directories section contains settings that specify where these files are located, among other things:

```
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
; Paths and Directories ;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
; Path in which included files are searched for via include/include_once/
require/require_once
; UNIX: "/path1:/path2"
;include_path = ".:/php/includes"
;
; Windows: "\path1;\path2"
;include_path = ".;c:\\php\\includes"
; Root directory for PHP scripts
doc_root =
; The directory under which PHP opens a script
user_dir =
; Directory in which the extension modules are located (everything except
Windows)
; extension_dir = "./"
; Directory in which the extension modules are located (Windows variant)
; extension_dir = "ext"
; Additional security for the CGI mode.
; Must be set to 0 for the IIS! ;
cgi.force_redirect = 1
```