| Function | Returns | Action |
|---|---|---|
| `mysql_field_len(int result, int field_offet)` | int | Returns the length of the specified field |
| `mysql_field_type(int result, int field_offset)` | string | Gets the type of the specified field in a result |
| `mysql_field_flags(int result, int field_offset)` | string | Gets the flags associated with the specified field in a result |
| `mysql_free_result(int result)` | int | Frees result memory |

# TABLE E-21 ASPELL FUNCTIONS

| Function | Returns | Action |
|---|---|---|
| `aspell_new(string master [, string personal])` | int | Loads a dictionary |
| `aspell_suggest(aspell int, string word)` | array | Returns array of suggestions |
| `aspell_check(aspell int, string word)` | bool | Returns TRUE if a word is valid, FALSE if it is not |
| `aspell_check_raw(aspell int, string word)` | int | Returns TRUE if word is valid |

![](bbox=[0.18, 0.7, 0.26, 0.76])

To use the aspell functions, you need the aspell library from http://metalab.unc.edu/kevina/aspell/. That PHP is configured with --with-aspell