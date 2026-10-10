
### CERTIFICATION OBJECTIVE 4.03

### Looking at Password Attacks

A very important type of attack to be familiar with is a password attack. A password attack is an attempt by a hacker to figure out the passwords for user accounts stored on the system. This section discusses the different types of password attacks and how to prevent password attacks from occurring in your environment. Note that these are also known as `cryptographic attacks`, which is the term under which you will find them listed in the Security+ objectives.

![Image](exam.jpg)

**You should know the different types of password attacks.**

#### Types of Password Attacks

The three major types of password attacks are dictionary attacks, brute-force attacks, and hybrid attacks. You will learn about each of these password attack types in this section along with other password attack concepts such as password spraying, rainbow tables, and plaintext passwords.

![Images](video.jpg)**To see an example of a password-cracking attack, check out the video included in the online resources that accompany this book.**

##### Dictionary Attack

A dictionary attack involves the hacker using a program that has a list of popular usernames in one text file and a list of words in a language dictionary that are to be tried as passwords in another file. The dictionary file normally contains all of the words in a language and can be downloaded from the Internet. [Figure 4-10](#ch04.xhtml#ch4fig10) displays a dictionary attack tool called NetBIOS Authentication Tool (NAT) and its sample user list file and password list file.

![Image](f0167-01.jpg)

FIGURE 4-10  

Using NAT to do a dictionary attack

The benefit of a dictionary attack from a hacker's point of view is it is a very fast and efficient type of attack because all it does is read the contents of a file—there is no mathematical calculation needed on the part of the password-cracking software. The disadvantage of the dictionary attack is that most passwords today are complex passwords in the sense that they require letters, numbers, and symbols. This makes the dictionary attack ineffective because those passwords are not dictionary words.

##### Brute-Force Attack

A brute-force attack is a password attack that involves using the password-cracking software to mathematically calculate every possible password. Normally, the hacker would configure the password-cracking software with requirements such as the number of characters and whether to use letters, numbers, and symbols.

The benefit of a brute-force attack from the hacker's point of view is that it is very effective—it will crack the passwords on a system if it has enough time to do so. The disadvantage of a brute-force attack is the time it takes to complete it. Due to the large number of possible passwords, it could take years for the password crack to complete!

![Images](job.jpg)**You can use password-cracking tools to assess the complexity of passwords on your network, but remember that hacking is illegal—no matter what the reason. Be sure to obtain written permission from upper-level management before you run any attack tools in a production environment.**

##### Hybrid Attack

Another type of password attack is known as a hybrid attack. A hybrid attack involves the password-cracking software using a dictionary file, but after the software tries a word from the dictionary file, it then tries to modify the word. Examples of modifications that the cracking software will use are to place numbers after the word and possibly to replace characters. For example, after the word "house" is attempted, the software will then try "house1," "house2," and so on. Examples of popular character replacement scenarios include replacing an "a" in the word with an "@" symbol, replacing an "L" with the number "1," and replacing the "o" with a "0." [Figure 4-11](#ch04.xhtml#ch4fig11) displays the results of a password audit using LC4. Note that a few passwords were figured out through dictionary attack, but the password for user5 was figured out via a hybrid attack.

![Image](f0168-01.jpg)

FIGURE 4-11  

Using LC4 to do dictionary, hybrid, and brute-force attacks

##### Password Spraying

Password spraying is a type of attack on user accounts that involves the attacker sending a commonly used password to many different accounts to see if any of the accounts are using the common password.

![Image](exam.jpg)

**For the Security+ certification exam, know password spraying. Also know that if you are looking at a log file and see the same password being used with different account names, that is a potential password spraying attack. If you see the same user account being used with different logon attempts in a short period of time, that is an indication of a dictionary or brute-force attack, not a password spraying attack.**

##### Rainbow Tables

`Rainbow tables` are used to speed up the process of performing a brute-force attack. Recall that brute-force attacks can take a very long time. To speed the process up, the hacker can generate a rainbow table, which is a file generated that contains all mathematically possible passwords based on criteria given by the rainbow table generator. Rainbow tables are beneficial when the hacker is performing the attack because the calculations are already in the table (file); the hacker is simply reading a file. So the hacker gets the complexity of a brute-force attack but the speed of a dictionary attack.

##### Plaintext/Unencrypted

Another common type of password attack is called the `known-plaintext attack (KPA)`, or unencrypted attack. With a known-plaintext attack, the hacker knows the plaintext value of a password (known as the crib) and the corresponding encrypted version (known as ciphertext). With this information, the hacker can then work on figuring out the encryption keys and other passwords.

#### Cryptographic Attacks and Concepts

In [Chapter 2](#ch02.xhtml#ch2) you were introduced to confidentiality and integrity concepts, and in [Chapters 12](#ch12.xhtml#ch12) and [13](#ch13.xhtml#ch13) you will learn more about these cryptography services, but in this section I want to introduce you to attacks against cryptography services.

##### Birthday

A `birthday attack` is a type of attack performed on hashing functions. It has been found that if you try enough data input, you will find that two different data inputs generate the same hash value. This is known as a birthday attack because the theory is based on the fact that when you select a large, random group of people, you will have people with duplicate birth dates.

##### Collision and Downgrade Attacks

Hashing protocols are known to create collisions, which is when two different pieces of data create the same hash value. The higher number of bits the hash value is, the less of a chance there is that two different pieces of data create the same hash value.

A downgrade attack is a cryptography attack where the attacker forces a network connection between two systems to drop the high-quality encryption protocol and go with a less secure encryption protocol. The attacker does this so that they have better chances of cracking the weaker encrypted communication.

#### Online vs. Offline Attacks

As mentioned earlier, password attacks can be either online or offline. With an `online attack`, the hacker is trying to crack the password against the live system. The problem with this is that the hacker risks getting detected and locking out the accounts. If the hacker can get a copy of the user account database on a flash drive, the hacker can then take that away with them and try to crack the passwords `offline`.
