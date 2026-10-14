![](bbox=[0.11, 0.067, 0.698, 0.282])

However, attackers learned that if they began with “../” in their path, some web-server programs would allow them to break out of the WWW root box and get to the directory above the WWW root. In operating systems, “..” means go up one level. To go down one level, the command gives the name of the directory. For instance, to go up one level and down to the etc directory, the path would be “../etc”.

Typing URLs with “..” in them can give access to sensitive directories, including the command prompt directory. This is the basic **directory traversal attack**. With directory traversal, the path ../etc/passwd would allow the attacker to download the passwd file in the etc directory (on a Unix computer).

# THE DIRECTORY TRAVERSAL WITH HEXADECIMAL CHARACTER ESCAPES

As usually happens, vendors responded with a patch that rejected HTTP request messages containing a series of two dots.

Attackers soon found a variant of the basic attack that would succeed against this countermeasure. For instance, IIS allows hexadecimal input, in which % is followed by two symbols between 0 and F. Each symbol represents four bits, so the two symbols together represent a byte.

Then attackers were sending HTTP directory traversal messages with two hexadecimal codes for dot. For a while, this **hexadecimal directory traversal attack** was successful. Then vendors issued a patch to stop it.

**Figure 8-14** Webserver Attacks (Study Figure)

**Figure 8-15** Directory Traversal

![](bbox=[0.11, 0.752, 0.699, 0.974])