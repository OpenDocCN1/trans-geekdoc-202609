```
mysql> select trim(both '\n' from '\n mystring');
+-------------------------------------+
| trim(both '\n' from '\n mystring') |
+-------------------------------------+
| mystring                            |
+-------------------------------------+
1 row in set (0.00 sec)
```

Note that remstr will exactly match only the exact sequence of characters. So putting \t\n\n in the remstr argument in the preceding example removes only occurrences where tabs and newlines appear consecutively.

# REPLACE

This function returns the string str with all occurrences of the string from_str replaced by the string to_str:

```
REPLACE(str,from_str,to_str)
RETURNS: string
```

# SOUNDEX

This function returns a soundex string from str:

```
SOUNDEX(str)
RETURNS: string
```

Two strings that sound “about the same” in English should have identical soundex strings. A “standard” soundex string is four characters long, but the SOUNDEX() function returns a string of arbitrary length. You can use SUBSTRING() on the result to get a “standard” soundex string. All non-alphanumeric characters are ignored in the given string. All international alpha characters outside the A–Z range are treated as vowels.

```
mysql> select soundex('functions'), soundex('junctions'),
soundex('fiction');
+----------------+----------------+----------------+
| soundex('functions') | soundex('junctions') | soundex('fiction') |
+----------------+----------------+----------------+
| F52352         | J52352         | F235           |
+----------------+----------------+----------------+
1 row in set (0.00 sec)
```