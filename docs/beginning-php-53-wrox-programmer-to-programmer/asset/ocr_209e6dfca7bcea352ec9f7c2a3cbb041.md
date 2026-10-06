# Appendix B: Configuring PHP

```
; NOTE: Every character in this directive is considered separator!
; http://php.net/arg-separator.input
; Example:
; arg_separator.input = ":&";
```

```
; This directive determines which global arrays are registered when PHP
; starts up. if the register_globals directive is enabled, it also determines
; what order variables are populated into the global space. G,P,C,E & S are
; abbreviations for the respective global variables: GET, POST, COOKIE,
; ENV and SERVER. This is a performance penalty paid for the registration of
; these arrays because ENV is not as commonly used as the others, ENV is
; is not recommended on productions servers. You can still get access to
; the environment variables through getenv() should you need to.
; Default Value: "GPCS"
; Development Value: "GPCS"
; Production Value: "GPCS"
; http://php.net/variables-order
variables_order = "GPCS";
```

```
; This directive determines which super global data (G,P,C,E & S) should
; be registered into the super global array REQUEST. If so, it also determines
; the order in which that data is registered. The values for this directive are
; specified in the same manner as the variables_order directive, EXCEPT one.
; leaving this directive empty will cause PHP to leave the value set in the
; variables_order directive. It does not mean it will leave the super globals
; array REQUEST empty.
; Default Value: None
; Development Value: "GP"
; Production Value: "GP"
; http://php.net/request-order
request_order = "GP";
```

Whether or not to register the EPGCS as global variables. You may\want to turn this off if you do not want to clutter your scripts' global scope
with user data. This makes most sense when coupled with track_vars - in which
y can access all of the GC global variables through the $_HTTP_VARS[],
with variables.
You should do your best to write your scripts so that they do not require
register_globals to be on. Using form variables as globals can easily lead
to prevent possible security problems, if the code is not well thought of.
http://php.net/register-globals
register_globals = Off

```
; Determines whether the deprecated long $_HTTP_*VARS predefined variables
; case are registered by PHP or not. As they are deprecated, we obviously don't
recommend using them. They are by default for compatibility reasons but
; they are not recommended on productions servers.
; Default Value: On
; Development Value: Off
; Production Value: Off
; http://php.net/register-long-arrays
register_long_arrays = Off
```

```
; This directive determines whether PHP registers $argv &argc each time it
```

732