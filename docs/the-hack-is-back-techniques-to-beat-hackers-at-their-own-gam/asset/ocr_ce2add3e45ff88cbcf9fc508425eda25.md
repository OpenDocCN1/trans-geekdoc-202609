+   3. **UID.** This is the user ID for the account.
+   4. **GID.** This is the primary group ID for the account, all other groups assigned to the specific account can be found in the **/etc/group** file.
+   5. **GECOS.** This is the User Comment field, which is used to store specific comments about an account. This is commonly used to place full names, emails, and phone numbers for users.
+   6. **Home Directory.** This is the directory that the user is given when they initially log into the system. Users will place various configuration and operational files within their home folders.
+   7. **Default Shell.** This is the default shell interpretation program assigned to the user when they log in. Assigning the **/sbin/nologin** prevents any logins for a user account when attempting to log into the system directly.

Now that we understand the various parts of each entry in a passwd file, we can read the system’s current passwd file to understand what other accounts may be present. Keep in mind that any user account is generally UID 1000 or above. Users tend to leave secrets, passwords, or authentication material lying around and are a prime target for exploitation.

To read the file, we can use the **cat** command. Remember, this file should be world readable by default on a system, so anytime we establish a foothold or attempt to find a directory traversal vulnerability we should be able to read this file regardless of which account is running the service. We can read the file with **cat /etc/passwd** which will print out the passwd file to the terminal. The following information is from a default installation of a Kali Linux VM with an additional user added.

```
```text
$ cat /etc/passwd
root:x:0:0:root:/root:/usr/bin/zsh
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
*** REDUCED FOR BRIVITY ***
geoclue:x:132:140::/var/lib/geoclue:/usr/sbin/nologin
king-phisher:x:133:141::/var/lib/king-phisher:/usr/sbin/nologin
kali:x:1000:1000:Kali,,,:/home/kali:/usr/bin/zsh
redis:x:134:143::/var/lib/redis:/usr/sbin/nologin
_gvms:x:135:144::/var/lib/openvas:/usr/sbin/nologin
mosquitto:x:136:145::/var/lib/mosquitto:/usr/sbin/nologin
polkitd:x:999:999:polkit:/nonexistent:/usr/sbin/nologin
chris:x:1001:1001::/home/chris:/bin/sh
```
```

First thoughts? There are a LOT of entries in this file – but don’t let it overwhelm you! Keep in mind what we’ve learned so far. Note that there are only two user accounts with a UID of 1000 or higher, the **kali** account and the **chris** account. These two accounts indicate that they are interactive logins for users and they may have additional secrets within the system. What else is interesting about these two accounts? We know that their password hash is stored in the **/etc/shadow** file based on the **x** in the passwd file, and also that they both have their home directories in the **/home** folder. Keep this in mind as we continue to move through the system!