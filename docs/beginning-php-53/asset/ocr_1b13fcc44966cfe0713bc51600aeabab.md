# Appendix B: Configuring PHP

```
; http://php.net/ignore-repeated-errors
ignore_repeated_errors = Off
```

```
; Ignore source of message when ignoring repeated messages. When this setting
; is On you will not log errors with repeated messages from different files or
; source lines.
; http://php.net/ignore-repeated-source
;ignore_repeated_source = Off
```

```
; If this parameter is set to Off, then memory leaks will not be shown (on
; stdout or in the log). This has only effect in a debug compile, and if
; error reporting includes E_WARNING in the allowed list
; http://php.net/report-memleaks
report_memleaks = On
```

```
; This setting is on by default.
;report_zend_debug = 0
```

```
; Store the last error/warning message in $php_errormsg (boolean). Setting this
; value
; to On can assist in debugging and is appropriate for development servers. It
; should
; however be disabled on production servers.
; Default Value: Off
; Development Value: On
; Production Value: Off
; http://php.net/track-errors
track_errors = On
```

```
; Turn off normal error reporting and emit XML-RPC error XML
; http://php.net/xmlrpc-errors
;xmlrpc_errors = 0
```

```
; An XML-RPC faultCode
;xmlrpc_error_number = 0
```

```
; When PHP displays or logs an error, it has the capability of inserting html
; links to documentation related to that error. This directive controls whether
; those HTML links appear in error messages or not. For performance and security
; reasons, it's recommended you disable this on production servers.
; Note: This directive is hardcoded to Off for the CLI SAPI
; Default Value: On
; Development Value: On
; Production value: Off
; http://php.net/html-errors
html_errors = On
```

```
; If html_errors is set On PHP produces clickable error messages that direct
; to a page describing the error or function causing the error in detail.
; You can download a copy of the PHP manual from http://php.net/docs
; and change 'docref_root' to the base URL of your local copy including the
; leading '/'. You must also specify the file extension being used including
; the dot. PHP's default behavior is to leave these settings empty.
```