These wildcards can be used with commands other than ls. For example, the rm command (to remove a file) can also remove files based on wildcard assignments. Here is a basic script using wildcards:

```
#!/bin/sh
ls *.txt
ls [a-m]???.sh
ls ??.txt
exit 0
```

This is a very simple script but it illustrates the essentials of what we have discussed thus far. Table 10-2 provides a list of the available wildcards.

# TABLE 10-2 Wildcards

| Wildcard | Purpose |
|---|---|
| * | This means literally any character, and any number of characters. For example, *.sh would mean any shell, any file at all, regardless of how many characters are in the name, that ends in the .sh extension. |
| ? | This denotes one character. For example, ????.txt would mean all text files that have a four-character name. |
| ! | This means not, or negation. |
| [abc] | This means containing any of the characters listed. So [abc]???.txt would mean all text files that start with an a, b, or c followed by three characters. |
| [a-m] | This means any characters in the range shown. So [a-l]?? .txt would mean any file starting with some letter from a to e, followed by two characters. |

# Linux Passwords

You were briefly introduced to Linux passwords in Chapter 9. Now we will take a much closer look. First let’s look at the /etc/shadow file from my own Kali Linux, as shown in Figure 10-11.

First notice that various services also have accounts. Let’s examine this so you can understand what you are seeing. First, it is obvious that each line is a separate user and that there are users for service accounts as well as humans. Each field is separated by a colon.

The first field is the username. The second is the password. Now, the password can be stored as a hash or encrypted, depending on the version of Linux. Some versions of Linux (though not the one shown in Figure 10-11) will tell you which it is. There is an ID with the password:

+   1. **$1$** is MD5.
+   2. **$2a$ or $2y$** is Blowfish.
+   3. **$5$** is SHA-256.
+   4. **$6$** is SHA-512.