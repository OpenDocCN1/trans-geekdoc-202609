# TABLE E-2 VARIABLE TYPE FUNCTIONS (Continued)

| Function | Returns | Action |
| --- | --- | --- |
| settype(string var, string type) | int | Sets the type of the variable. Returns 1 if the conversion is successful |
| is_bool(mixed var) | bool | Returns true if variable is a Boolean |
| is_long(mixed var) | bool | Returns true if variable is a long (integer) |
| is_double(mixed var) | bool | Returns true if variable is a double |
| is_string(mixed var) | bool | Returns true if variable is a string |
| is_array(mixed var) | bool | Returns true if variable is an array |
| is_object(mixed var) | bool | Returns true if variable is an object |
| is_numeric(mixed value) | bool | Returns true if value is a number or a numeric string |

# TABLE E-3 QUOTE SETTING FUNCTIONS

| Function | Returns | Action |
| --- | --- | --- |
| set_magic_quotes_runtime(int new_setting) | int | Sets the current active configuration setting of magic_quotes_runtime and returns the previous setting |
| get_magic_quotes_runtime(void) | int | Gets the current active configuration setting of magic_quotes_runtime |
| get_magic_quotes_gpc(void) | int | Gets the current active configuration setting of magic_quotes_gpc |