Password1. Hybrid dictionary attacks try simple modifications of common words contained in a dictionary file. These predefined modifications are called mangling rules. Mangling rules are customizable and can create a dizzying array of possible passwords from a single dictionary word. Hybrid dictionary attacks are effective against derivatives of common passwords. Some of these include, but are not limited to, the following:

+   - Adding numbers (1password, password1, 1492password, etc.)
+   - Reverse spelling (drowssap)
+   - Entering the password twice (passwordpassword)
+   - Trying the password with all possible changes in case (PaSsWoRd)
+   - Using leet “1337” spellings (pa55word)
+   - Deleting characters (pswrd)
+   - Trying key patterns (asdfghjkl, qwertyuiop, etc.)
+   - Adding all prefixes and suffixes (passworded, postpassword, etc.)
+   - Trying derivations of username, e-mail, or other account information contained in the password file

Hybrid dictionary attacks are effective because most users choose passwords that come from dictionaries. Dictionary words are easy to remember and usually have meaning for the user. Unfortunately, users tend to believe that minor modifications of dictionary words will prevent attackers from guessing their passwords. Attackers are already aware of the common modifications users make to their passwords.

# RAINBOW TABLES

Another way of cracking a password is to look up the hash of the password in a rainbow table. A rainbow table is a list of pre-computed password hashes that are indexed. An attacker could create a large table of possible passwords and their hashes. The attacker would then index the hashes to expedite the cracking process. This results in a time–memory trade-off where more memory is used to store the pre-computed password hashes, but the time it takes to crack a password is greatly reduced.

For example, it is possible to create a collection of rainbow tables (NTLM hashes) containing every possible password hash for every possible combination of numbers, uppercase letters, lowercase letters, and special characters (non-alphanumeric). For all passwords containing one to six characters, it would take about 37 days to create the

# Test Your Understanding

+   14. a. What is brute-force password guessing?
+      b. Why is it important to not simply use all lowercase letters in passwords?
+      c. What are complex passwords?
+      d. Why is password length important?
+      e. What is a dictionary attack?
+      f. Why are dictionary attacks faster than brute-force guessing?
+      g. What are hybrid dictionary attacks?
+      h. How are mangling rules applied to list of dictionary words?
+   15. a. What are rainbow tables?
+      b. How would rainbow tables reduce the time needed to crack a password?
+      c. Would it be possible to create rainbow tables for all possible passwords with 1–20 characters? Would it be practical?