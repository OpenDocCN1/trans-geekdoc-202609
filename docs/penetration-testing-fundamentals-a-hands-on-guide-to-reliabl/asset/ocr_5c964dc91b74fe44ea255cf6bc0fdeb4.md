# Pass the Hash

The pass the hash attack essentially realizes that the hash cannot be reversed (recall the discussion of hashes in Chapter 3); rather than trying to find out what the password is, the attacker just sends over the hash. If the attacker can obtain a valid username and user password hashes values (just the hash; the attacker does not know the actual password), then the hacker can use that hash, without ever knowing the actual password.

Windows applications ask users to type in their passwords; then they in turn hash them. Often this can be done with an API like LsaLogonUser, converting the password to either an LM hash or an NT hash. Pass the hash skips around the application and just sends the hash.

As a penetration tester, you hope this won’t work. There are countermeasures. One is to add a current date/time to the NTLM hash. That means that if the hash is not sent instantly from an application, it will be considered invalid.

# chntpw

This is a tool that can be downloaded from the Internet (http://www.chntpw.com/). It is used to blank passwords. It can be used from a USB or CD. It will edit the SAM file and simply blank the passwords used. It is a command-line tool, and will blank the passwords in the SAM file. Figure 6-2 shows the installation for USB.

![](bbox=[0.12, 0.55, 0.83, 0.83])

FIGURE 6-2 chntpw Installation for USB.

# Net User Script

This particular exploit first requires access to the target machine with at least guest-level privileges. It is based on the fact that many organizations put the technical support personnel in the domain admins group.