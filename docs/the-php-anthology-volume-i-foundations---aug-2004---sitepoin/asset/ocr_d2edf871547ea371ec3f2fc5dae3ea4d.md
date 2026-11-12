| Setting | Notes |
| :--- | :--- |
| error_reporting
(default: E_ALL & ~E_NOTICE) | When developing, and for maximum portability,
it's best to set this to E_ALL, so that PHP will
inform you of situations where, for example, a
$__GET variable your code relies upon has not
been initialized. This forces you to write code
that is more secure and contains fewer logic er-
rors, in order to avoid warnings. This also en-
sures that your code will run neatly on other
servers configured this way. |
| display_errors
(default: on) | Determines whether PHP sends error messages
to the Web browser. When running your applica-
tion in a live environment, it's generally better
to switch this off, instead using PHP's logging
mechanism to capture errors to a file, for ex-
ample. |
| open_basedir
(default: not set) | Allows you to restrict all PHP file operations to
a given directory or below. This can be a good
idea to prevent a script that is used to display
the contents of files, for example, from being
used to access sensitive files elsewhere on your
server. |
| allow_url_fopen
(default: on) | Allows you to specify remote file locations for
use with functions like fopen (e.g.
fopen( 'http://www.sitepoint.com/', 'r' );).
It's a handy tool but is also potentially a security
risk for a badly written script. Switch it off if
you know you don't need it. |

# Includes and Execution Settings

Table A.2 shows the most important PHP settings that relate to includes, and how well your PHP scripts run.