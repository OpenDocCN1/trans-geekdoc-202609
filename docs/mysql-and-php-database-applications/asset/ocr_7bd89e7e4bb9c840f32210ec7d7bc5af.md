# TABLE E-16 URL FUNCTIONS (Continued)

| Function | Returns | Action |
| --- | --- | --- |
| urlencode(string str) | string | URL-encodes string |
| urldecode(string str) | string | Decodes URL-encoded string |
| rawurlencode(string str) | string | URL-encodes string. See Chapter 6 for the difference between this and urllencode(). |
| rawurldecode(string str) | string | Decodes URL-encoded string |

# TABLE E-17 VARIABLE SERIALIZING FUNCTIONS

| Function | Returns | Action |
| --- | --- | --- |
| serialize(mixed variable) | string | Returns a string representation of variable (which can later be unserialized) |
| unserialize(string variable_representation) | mixed | Takes a string representation of variable and recreates it |

# TABLE E-18 MISCELLANEOUS FUNCTIONS

| Function | Returns | Action |
| --- | --- | --- |
| ip2long(string ip_address) | int | Converts a string containing an (IPv4) Internet Protocol dotted address into a proper address |
| long2ip(int proper_address) | string | Converts an (IPv4) Internet network address into a string in Internet standard dotted format |
| getenv(string varm) | string | Gets the value of an environment variable |
| putenv(string setting) | void | Sets the value of an environment by using a format of putenv("ENV_VAR=$foo"); |