
![tip](images/tip.png)Some of these tools require physical access to the systems you’re testing. You may be wondering what value physical access adds to password cracking. If a hacker can obtain physical access to your systems and password files, you have more than just basic information security problems to worry about, right? True, but this kind of access is entirely possible! What about a summer intern, a disgruntled employee, or an outside contractor with malicious intent? The mere risk of an unencrypted laptop’s being lost or stolen and falling into the hands of someone with ill intent should be reason enough.

To understand how the preceding password-cracking programs generally work, you need to understand how passwords are encrypted. Passwords typically are encrypted when they’re stored on a computer, using an encryption or one-way hash algorithm such as SHA2 or MD5. Then hashed passwords are represented as fixed-length encrypted strings that always represent the same passwords with exactly the same strings. These hashes are irreversible for all practical purposes, so in theory, passwords can never be decrypted. Furthermore, certain passwords, such as those in Linux, have a random value called a `*salt*` added to them to create a degree of randomness. This value prevents the same password used by two people from having the same hash value.

![remember](images/remember.png)In Windows, after the password hashes are obtained, attackers can leverage an attack called `pass the hash` to send the hash rather than the actual password to the system for authentication. You can find a good article on using Metasploit and the `psexec` module for this purpose at [`https://www.offensive-security.com/metasploit-unleashed/psexec-pass-hash/`](https://www.offensive-security.com/metasploit-unleashed/psexec-pass-hash/).

Password-cracking utilities take a set of known passwords and run them through a password-hashing algorithm. The resulting encrypted hashes are compared at lightning speed with the password hashes extracted from the original password database. When a match is found between the newly generated hash and the hash in the original database, the password has been cracked. The process is that simple.

Other password-cracking programs attempt to log on by using a predefined set of user IDs and passwords. This method is how many dictionary-based cracking tools work, such as Brutus ([`www.hoobie.net/brutus`](http://www.hoobie.net/brutus)) and SQLPing3 ([`www.sqlsecurity.com/downloads`](http://www.sqlsecurity.com/downloads)). I cover cracking web application and database passwords in [chapters 15](#c15.xhtml) and [16](#c16.xhtml).

Passwords that are subjected to cracking tools eventually lose. You have access to the same tools as the bad guys. These tools can be used for both legitimate security assessments and malicious attacks. You want to find password weaknesses before the bad guys do. In this section, I show you some of my favorite methods for assessing Windows and Linux/Unix passwords.

![warning](images/warning.png)When trying to crack passwords, the associated user accounts may be locked out, which could interrupt your users. Be careful if intruder lockout is enabled in your operating systems, databases, or applications. If lockout is enabled, you might lock out some or all computer/network accounts, resulting in a denial of service situation for your users.

#### Dictionary attacks

Dictionary attacks quickly compare a set of known dictionary-type words — including many common passwords — against a password database. This database is a text file with hundreds, if not thousands, of dictionary words, typically listed in alphabetical order. Suppose that you have a dictionary file that you downloaded from one of the sites in the following list. The English-dictionary file at the Purdue University site contains one word per line starting with `*10th, 1st*` all the way to `*zygote*.`

Many password-cracking utilities use a separate dictionary that you create or download from the Internet. Here are some popular sites that house dictionary files and other miscellaneous word lists:

*   [`ftp://ftp.cerias.purdue.edu/pub/dict`](ftp://ftp.cerias.purdue.edu/pub/dict)

*   [`www.outpost9.com/files/WordLists.html`](http://www.outpost9.com/files/WordLists.html)

Don’t forget to use other language files as well, such as Spanish and Klingon.

![remember](images/remember.png)Dictionary attacks are only as good as the dictionary files you supply to your password-cracking program. You can easily spend days or even weeks trying to crack passwords with a dictionary attack. If you don’t set a time limit or a similar expectation going in, you’ll likely find that dictionary cracking is a mere exercise in futility. Most dictionary attacks are good for weak (easily guessed) passwords. Some special dictionaries, however, have common misspellings or alternative spellings of words, such as `pa$$w0rd` (password) and `5ecur1ty` (security). Additionally, special dictionaries can contain non-English words and thematic words from religions, politics, or `*Star Trek*`.

#### Brute-force attacks

Brute-force attacks can crack practically any password, given sufficient time. Brute-force attacks try every combination of numbers, letters, and special characters until the password is discovered. Many password-cracking utilities let you specify such testing criteria as the character sets, password length to try, and known characters (for a mask attack). Sample [Figure 8-1](#c08.xhtml#c08-fig-0001) shows some example brute-force password-cracking options.

![ FIGURE 8-1:  Brute-force password-cracking options in Proactive Password Auditor.](images/9781119485476-fg0801.png)

[FIGURE 8-1](#c08.xhtml#rc08-fig-0001)  Brute-force password-cracking options in Proactive Password Auditor.

![warning](images/warning.png)A brute-force test can take quite a while, depending on the number of accounts, their associated password complexities, and the speed of the computer that’s running the cracking software. As powerful as brute-force testing can be, it can take forever to exhaust all possible password combinations, which isn’t practical in every situation.

![warning](images/warning.png)Smart hackers attempt logins slowly or at random times so that the failed login attempts aren’t as predictable or obvious in the system log files. Some malicious users even call the IT help desk to attempt a reset of the account they just locked out. This social engineering technique could be a major issue, especially if the organization has no (or minimal) mechanisms in place to verify that locked-out users are who they say they are.

Can an expiring password deter a hacker’s attack and render password cracking software useless? Yes. After the password is changed, the cracking must start again if the hacker wants to test all the possible combinations. This scenario is one reason why it’s a good idea to change passwords periodically. Still, I’m not a big fan of forcing users to change their passwords often. Shortening the change interval can reduce the risk of passwords being cracked but can also be politically unfavorable in your business and end up creating the opposite of the effect you’re going for. You have to strike a balance among security, convenience, and usability. In many situations, I don’t think it’s unreasonable to require password changes every 6 to 12 months or (especially) after a suspected compromise. Keep in mind that there is a direct relationship between password change interval and password length. The longer the interval is the longer the password needs to be.
