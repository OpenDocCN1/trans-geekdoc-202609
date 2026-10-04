# Appendix E: PHP Function Reference

Table E-9 PRINT FUNCTIONS

| Function | Returns | Action |
| --- | --- | --- |
| sprintf(string format [, mixed arg1 [, mixed ...]) | string | Returns a formatted string |
| printf(string format [, mixed arg1 [, mixed ...]) | int | Outputs a formatted string |
| print_r(mixed var) | void | Prints out information about the specified variable |
| var_dump(mixed var) | void | Dumps a string representation of the variable to output |

Table E-10 HTTP HEADER FUNCTIONS

| Function | Returns | Action |
| --- | --- | --- |
| header(string header) | void | Sends a raw HTTP header |
| setcookie(string name [, string value [, int expires [, string domain [, string secure]]]])]) | void | Sends a cookie |
| headers_sent(void) | int | Returns true if headers have already been sent; returns false otherwise |