```
;;;;;;;;;;;;;;;;;;;;;;;;
; Resource Limits ;
;;;;;;;;;;;;;;;;;;;;;;;;
max_execution_time = 30 ; Maximum script runtime
max_input_time = 60 ; Maximum time for parsing the input
max_input_nesting_level = 64 ; Maximum nesting depth
; in the input ;
max_input_vars = 1000 ; Maximum number of input variables
;max.multipart.body_parts = 1500 ; Maximum parts for multipart requests
memory_limit = 128M ; Maximum memory consumption
```

When errors occur, there are several ways to react. Among other things, PHP offers logging of errors (with Apache) and the option of not sending an error message to the web browser. The latter is unfavorable during development and testing but is extremely useful on the production server:

```
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
; Error handling and logging ;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
; Stufen für error_reporting:
; E_ALL - All errors and warnings
; E_ERROR - (Fatal) runtime errors
; E_RECOVERABLE_ERROR - Almost fatal runtime errors
; E_WARNING - Non-fatal runtime errors
; E_PARSE - Parser errors
; E_NOTICE - Run-time notices
; E_CORE_ERROR - errors when starting PHP ;
; E_CORE_WARNING - warnings when starting PHP ;
; E_COMPILE_ERROR - errors when compiling ;
; E_COMPILE_WARNING - warnings when compiling
; E_USER_ERROR - user-specific error messages
; E_USER_WARNING - user-specific warnings
;
E_USER_NOTICE - User-specific notices ;
E_DEPRECATED - Warnings for code that will no longer work in future
; PHP versions ;
E_USER_DEPRECATED - User-specific warnings for obsolete code
;
; Examples:
;
; - Everything except warnings and compatibility notes
;
; error_reporting = E_ALL & ~E_NOTICE & ~E_STRICT & ~E_DEPRECATED
;
```