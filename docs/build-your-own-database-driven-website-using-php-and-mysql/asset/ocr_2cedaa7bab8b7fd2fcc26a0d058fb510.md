# RIGHT(str, len)

Returns the rightmost len characters of str. If str is shorter than len characters, str is returned with no extra padding.

# SUBSTRING(str,pos,len)
SUBSTRING(str FROM pos FOR len)
MID(str,pos,len)

Returns a string up to len characters long taken from str beginning at position pos (where 1 is the first character). The second form of SUBSTRING is the ANSI standard.

# SUBSTRING(str, pos)
SUBSTRING(str FROM pos)

Returns the string beginning from position pos in str (where 1 is the first character) and going to the end of str.

# SUBSTRING_INDEX(str,delim,count)

MySQL counts count occurrences of delim in str, then takes the substring from that point. If count is positive, MySQL counts to the right from the start of the string, and then takes the substring up to but not including that last delimiter. If count is negative, MySQL counts to the left from the end of the string, and then takes the substring that starts right after that last delimiter, and runs to the end of str.

# LTRIM(str)

Returns str with any leading whitespace trimmed off.

# RTRIM(str)

Returns str with any trailing whitespace trimmed off.

# TRIM([[BOTH | LEADING | TRAILING] [remstr] FROM] str)

Returns str with either whitespace (by default) or occurrences of the string remstr removed from the start of the string (LEADING), end of the string (TRAILING), or both (BOTH, the default).

# SOUNDEX(str)

Produces a string that represents how str sounds when read aloud. Words that sound similar should have the same 'soundex string'.

```
E.g.:
SOUNDEX("tire") = "T600"
SOUNDEX("tyre") = "T600"
SOUNDEX("terror") = "T600"
SOUNDEX("tyrannosaur") = "T6526"
```