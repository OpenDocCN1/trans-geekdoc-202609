# Appendix B: Configuring PHP

+   ; The following is a summary of its search order:
; 1. SAPI module specific location.
; 2. The PHPRC environment variable. (As of PHP 5.2.0)
; 3. A number of predefined registry keys on Windows (As of PHP 5.2.0)
; 4. Current working directory (except CLI) or directory of PHP
; 5. The web server's directory (for SAPI modules), or directory of PHP (otherwise in Windows)
; 6. The directory specified by the --config-file-path compile option, or the Windows directory (C:\windows or Wwint)
; 7. See the PHP docs for more specific information.
; http://php.net/configuration.file

+   ; The syntax of PHP is extremely simple. Whitespace and Lines
; beginning with a semicolon are silently ignored (as you guessed).
; Section headers (e.g. [Foo]) are also silently ignored, even though
; they mean nothing in the future.

+   ; Directives following the section heading [PATH=//mysite] only
; apply to PHP lines in the /www/mysite directory. Directives
; following the section heading [HOST=//www.example.com] only apply to
; PHP files served from example.com. Directives set in these
; special sections cannot be overridden by user-defined INI files or
; at runtime. Currently, [PATH]= and [HOST]= sections only work under
; CGI/FastCGI.
; http://php.net/ini.sections

+   ; Directives are specified using the following syntax:
; directive = value
; Directive names are "case sensitive" - foo=bar is different from FOO=bar.
; Directive variables are used to configure PHP or PHP extensions.
; There is no name validation. IF PHP can't find an expected
; directive because it is not set or a default value will be used.

+   ; The value can be a string, a number, a PHP constant (e.g. E_ALL & M_PI), one
; of the INI constants (On, True, False, Yes or None) or an
; expression
; (e.g. E_ALL & ~E_NOTICE), a quoted string "*bar", or a reference to
; previously set variable or directive variable (e.g. $foo)

+   ; Expressions in the INI file are limited to bitwise operators and
parentheses:
| bitwise OR
| ^ bitwise XOR
| & bitwise AND
| bitwise NOT
| boolean NOT

+   ; Boolean flags can be turned on using the values 1, True, or Yes.
; They can be turned off using the values 0, Off, False or No.

+   ; An empty string can be denoted by simply writing anything after the equal
; sign, or by using the None keyword:

+   ; foo = ; sets foo to an empty string