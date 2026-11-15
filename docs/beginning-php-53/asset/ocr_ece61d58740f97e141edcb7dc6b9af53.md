```
; from PHP at some point in the near future. The acceptable method for passing a
; value by reference to a function is by declaring the reference in the functions
; definition, not at call time. This directive does not disable this feature, it
; only determines whether PHP will warn you about it or not. These warnings
; should enabled in development environments only.
; Default Value: On (Suppress warnings)
; Development Value: Off (Issue warnings)
; Production Value: Off (Issue warnings)
; http://php.net/allow-call-time-pass-reference
allow_call_time_pass_reference = Off

; Safe Mode
; http://php.net/safe-mode
safe_mode = Off

; By default, Safe Mode does a UID compare check when
; opening files. If you want to relax this to a GID compare,
; then turn on safe_mode_gid.
; http://php.net/safe-mode-gid
safe_mode_gid = Off

; When safe_mode is on, UID/GID checks are bypassed when
; including files from this directory and its subdirectories.
; (directory must also be in include_path or full path must
; be used when including)
; http://php.net/safe-mode-include-dir
safe_mode_include_dir =

; When safe_mode is on, only executables located in the safe_mode_exec_dir
; will be allowed to be executed via the exec family of functions.
; http://php.net/safe-mode-exec-dir
safe_mode_exec_dir =

; Setting certain environment variables may be a potential security breach.
; This directive contains a comma-delimited list of prefixes.  In Safe Mode,
; the user may only alter environment variables whose names begin with the
; prefixes supplied here.  By default, users will only be able to set
; environment variables that begin with PHP_ (e.g. PHP_FOO=BAR).
; Note:  If this directive is empty, PHP will let the user modify ANY
; environment variable!
; http://php.net/safe-mode-allowed-env-vars
safe_mode_allowed_env_vars = PHP_

; This directive contains a comma-delimited list of environment variables that
; the end user won't be able to change using putenv().  These variables will be
; protected even if safe_mode_allowed_env_vars is set to allow to change them.
; http://php.net/safe-mode-protected-env-vars
safe_mode_protected_env_vars = LD_LIBRARY_PATH

; open_basedir, if set, limits all file operations to the defined directory
; and below.  This directive makes most sense if used in a per-directory
; or per-virtualhost web server configuration file.  This directive is
; *NOT* affected by whether Safe Mode is turned On or Off.
```