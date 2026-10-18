
3. Click `Submit & Search` to search the Hashes.com database. After a few moments, you should see a list of cracked passwords:

```
64f12cddaa88057e06a81b54e73b949b:Password1
85f4aaf6ac4fac1d9b55e6b880bcda3e:CaptainMarvel
920ae267e048417fcfe00f49ecbd4b33:P@$$w0rd!
d6566eae841e523df8fd96a42bcbd4ac:superman20
fc525c9683e8fe067095ba2ddc971889:Passw0rd!--snip--
```

![Figure 7-2: Hashes.com takes your NTLM hashes as input and outputs any cracked passwords it finds in its database.](image_fi/502000c07/f07002.png)

Figure 7-2: Hashes.com takes your NTLM hashes as input and outputs any cracked passwords it finds in its database.

Hashes.com found five of the passwords! Because it keeps adding new passwords to its database, it may be able to crack more of the simple passwords we will use over the course of this book.

We’ve been able to recover at least five passwords from our Windows VM using a free online lookup tool—and an attacker may need only `one` username and password to be able to hack into a network, company, or government agency. That’s why it’s important for `every user` in an organization to choose longer, harder-to-guess passwords.

### John the Ripper

John the Ripper, often abbreviated to JtR or simply John, is one of the oldest tools for cracking passwords; it’s been over 20 years since the first version of John was released. John is included in Kali Linux under the Kali menu button’s `05 - Password Attacks` menu.

John runs from the command line terminal, but there’s another version of John, called Johnny, with a graphical user interface (GUI) that’s easier to work with. Johnny isn’t included in the most recent versions of Kali. To install it, open a new terminal window and type the following two commands:

```
kali@kali:~$ sudo apt update
kali@kali:~$ sudo apt install johnny
```

You may have to enter your password (`kali`) after the first command. After installation, Johnny will usually appear on the `05 - Password Attacks` menu below John, but you can also run it from the terminal by typing `johnny`.

We’ll use two methods in Johnny to crack more of our stolen Windows passwords. We’ll try a dictionary attack to crack common passwords and a mask attack to crack passwords with variations. Everything you do in Johnny can also be done from the terminal with John; after you use Johnny, you can look up commands for John and try them to understand the overall process.

#### A Dictionary Attack

We’ll begin by trying a dictionary attack. Also called a `wordlist attack`, a `dictionary attack` tests a list of words against the hashes we’re trying to crack. John the Ripper will hash each password in a long list of common passwords we provide, comparing each hash value to our Windows hashes. If it finds a match, we’ve cracked that password.

Kali has several built-in wordlists, including the RockYou wordlist. RockYou was a company that lost 32 million users’ passwords in a famous 2009 breach involving a poorly protected web application. The list of plaintext passwords exposed by RockYou is still one of the best free wordlists for checking the security of a password.

1. To access the RockYou wordlist, enter the following command in the terminal window:

```
kali@kali:~$ sudo gunzip /usr/share/wordlists/rockyou.txt.gz
```

This command will extract the wordlist as `rockyou.txt` in the `/usr/share/wordlists` folder so that it can be used as a dictionary in John and Johnny.

2. Open Johnny by clicking the Kali menu button and selecting `05 - Password Attacks`▶`johnny`.

3. Click `Open password file`▶`Open password file (PASSWD format)`. Find the `Windows_hashes.txt` file we created earlier, as shown in [Figure 7-3](#c07.xhtml#figure7-3), and select it to load the password hash file.

![Figure 7-3: Opening the `Windows_hashes.txt` password file in Johnny](image_fi/502000c07/f07003.png)

Figure 7-3: Opening the `Windows_hashes.txt` password file in Johnny

4. Click `Options` on the left in Johnny and then click the `Wordlist` tab under Attack mode in the Options window. Type `/usr/share/wordlists/rockyou.txt` into the Wordlist file: text box, as shown in [Figure 7-4](#c07.xhtml#figure7-4).

![Figure 7-4: Loading the `rockyou.txt` wordlist through Johnny](image_fi/502000c07/f07004.png)

Figure 7-4: Loading the `rockyou.txt` wordlist through Johnny

5. Still in the Options window, under Session details, select `NT` from the Current hash format: drop-down list, as shown in [Figure 7-5](#c07.xhtml#figure7-5). This tells Johnny that the password hashes are in NTLM format.

![Figure 7-5: Choosing `NT` as the input password hash format](image_fi/502000c07/f07005.png)

Figure 7-5: Choosing `NT` as the input password hash format

6. Click `Passwords` on the left and then click `Start new attack` at the top.

Almost instantly, Johnny will display several cracked passwords, as shown in [Figure 7-6](#c07.xhtml#figure7-6). (If you don’t see any, make sure you changed the current hash format to NT in step 5.)

![Figure 7-6: It takes Johnny almost no time to crack five or six passwords using the hashes we captured.](image_fi/502000c07/f07006.png)

Figure 7-6: It takes Johnny almost no time to crack five or six passwords using the hashes we captured.

It took us a few minutes to capture the password hashes, but less than a second to crack the first five or six passwords using a dictionary attack with the RockYou wordlist. That’s all the work a malicious hacker needs to do to get your passwords if you’re using simple one- or two-word passwords with just a few numbers and symbols.

The RockYou wordlist contained several of the passwords we set up for our users. The other passwords were complex enough that they didn’t appear in the list. Let’s see how to crack one or two more passwords using another option in Johnny—a mask attack.

#### A Mask Attack

A `mask attack` starts with partial information, like an old password, and adds characters to try cracking similar passwords. There’s a good chance that you or someone you know is reusing an old password by adding digits or symbols to the end, like `badpassword20!`. This behavior is more common than you’d think, and it makes many passwords susceptible to mask attacks.

Mask attacks are also effective if an attacker gains access to a fragment of someone’s password. Imagine Kara, one of our Windows users, has a job at CatCo Worldwide Media. While passing by Kara’s desk, a snoopy co-worker sees a sticky note Kara has thrown in the trash. It’s torn, but it looks like it might have part of a password written on it: `SuperGir` (see [Figure 7-7](#c07.xhtml#figure7-7)).

Social engineers call this `dumpster diving`—literally looking through someone’s trash for useful information, like bank statements, credit card offers, or passwords scribbled on the back of an envelope or on a sticky note like this one.

![Figure 7-7: Kara’s torn sticky note with what looks like part of her password](image_fi/502000c07/f07007.png)

Figure 7-7: Kara’s torn sticky note with what looks like part of her password

In Johnny, we can add wildcard characters to the end of `SuperGir` to try to guess what the rest of Kara’s password might be. A `wildcard` is a placeholder that can be replaced by any one of a group of letters, numbers, or symbols. We can use the wildcard characters `?u` for uppercase letters, `?l` for lowercase letters, `?d` for digits (0–9), `?s` for special symbols, or `?a` for all printable characters (letters, numbers, punctuation, and special characters).
