# Core PHP Programming

| | |
|---||
| n | The argument is saved as an unsigned short, which is 2 bytes. Integer is saved in a way that allows safe unpacking on both little-endian and big-endian machines. |
| N | Integer | The argument is saved as an unsigned long, which is 8 bytes. The value is saved in a way that allows safe unpacking on both little-endian and big-endian machines. |
| s | Integer | The argument is saved as an unsigned short, which is usually 2 bytes. |
| S | Integer | The argument is saved as a signed short, which is usually 2 bytes with one bit used for sign. |
| V | Integer | The argument is saved as an unsigned short in little-endian order. |
| V | Integer | The argument is saved as an unsigned long in little-endian order. |
| x | None | This format directive doesn't match with an argument. It writes a null byte. |
| X | None | This format directive causes the pointer to packed string to back up 1 byte. |
| @ | None | This format directive moves the pointer to the absolute position specified by its repeat count. The empty space is padded with null bytes.|

# parse_str(string query)

The parse_str function parses the query argument as if it were an HTTP query. A variable is created in the current scope for each field in the query. You may wish to use this function on the output of parse_url.

# array_parse_url(string query)

The parse_url function breaks a URL into an associative array with the following elements: fragment, host, pass, path, port, query, scheme, user. The query is not evaluated as with the parse_str function.

Figure 9-9. parse_url.