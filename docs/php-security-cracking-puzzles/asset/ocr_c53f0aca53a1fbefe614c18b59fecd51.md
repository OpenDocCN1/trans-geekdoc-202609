# 204 Part II: Solutions

way to bypass the limitation: passing the ' OR = 1 /* ' SQL injection in the password field. This will make the injection query look as shown in Listing II.4.20.

# Listing II.4.20. Circumventing the deletion limit

```
DELETE FROM userslist
WHERE pass = '' OR 1 = 1 /* AND
name = ''
```

Everything following the /* character sequence is treated by MySQL as a comment (including the LIMIT 1 instruction), and completing a comment is not a mandatory result. The results of executing this SQL injection are shown in Fig II.4.12.

![](bbox=[0.166, 0.383, 0.964, 0.722])

Fig. II.4.12. Bypassing the limit on deletions

The most effective protection in this case is to process any user-supplied variables with the mysql_escape_string() function (Listing II.4.21).

# Listing II.4.21. Protecting using the mysql_escape_string() function

```
<?php
...
if(!get_magic_quotes_gpc())

```