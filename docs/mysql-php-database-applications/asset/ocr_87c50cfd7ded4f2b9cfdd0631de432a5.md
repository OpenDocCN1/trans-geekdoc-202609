# TABLE F-10 FSOCK FUNCTIONS

| Function | Return Value | Action |
|---|---|---|
| fsockopen(string hostname, int port [, int errno [, string errstr [, float timeout]]]) | int | Opens an Internet or Unix domain-socket connection |
| pfsockopen(string hostname, int port [, int errno [, string errstr [, float timeout]]]) | int | Opens a persistent Internet or Unix domain-socket connection |

# TABLE F-11 HTTP HEADER FUNCTIONS

| Function | Return Value | Action |
|---|---|---|
| header(string header [, bool replace]) | void | Sends a raw HTTP header |
| setcookie(string name [, string value [, int expires [, string path [, string domain [, bool secure]]]]]) | bool | Sends a cookie |
| headers_sent(void) | int | Returns true if headers have already been sent, false otherwise |

# TABLE F-12 HTML-RELATED FUNCTIONS

| Function | Return Value | Action |
|---|---|---|
| htmlspecialchars(string string [, int quote_style[, string charset]]) | string | Converts special characters into HTML entities |
| htmlentities(string string [, int quote_style[, string charset]]) | string | Converts all applicable characters into HTML entities |