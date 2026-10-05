
# Chapter 1 Logon Problems

systems, including Microsoft Windows and Linux, the ultimate authentication “secret” is the pass-word hash. Once you have that, you have the keys to the kingdom.

## Rainbow Tables

As mentioned, most password hackers want to convert any stolen hashes to plaintext equivalents. However, cryptographic hashes, if they are any good, are explicitly designed to prevent someone capturing the hash by easily figuring out what the plaintext root password might be. But hackers can take guesses at what the password might be, the hash guess, and compare the hashed outcome of the guess to the captured password hash, and if they match, conclude they have the equivalent password.

But if the password is long or complex, even the dictionary-based attack leaves millions, if not billions, of possible choices that have to be tried before a successful guess. It is a lot of passwords and hashes to search through. A typical password hash can be 128-256 bits. To find the hash when doing a very fast catch, a password database will start searching for the hash that starts with. For example, if the hash is short, a password database will start searching for every hash that starts with the first character in the hash, and rule out every other hash that doesn't start with. Then, out of all the hashes that begin with, it will look for all the hashes that begin with the first two characters (the digits of the hash), and rule out all that begin not with. Still around the possible pool of hashes, it will look for all the hashes that begin with the first three digits (the hash), and so on, adding one character at a time until it narrows down the exact password through a sequential search. You might wonder why it doesn't just look for the correct hash from the hash at once; it is exponentially harder and searching through an extremely large database with millions of hashes takes a very long time.

## Hacking Multifactor Authentication

There are more efficient password databases called rainbow tables. Rainbow tables convert all longer password hashes ahead of time to an intermediate, shorter format, and do the same for the captured hash. For example, using a long hash (as shown earlier), the intermediate representation may match many different password hashes, but the correct hash is included in the list of passwords represented by the shorter form. For example, few thousand password hashes have the same intermediate form. When the rainbow table converts the targeted password hash to its intermediate form, it still has to search a smaller pool of possible hashes. It can take all the password hashes with the same intermediate form as the targeted hash, and find out which actually matches the full password—and without having to search through billions of longer hashes.

So, a smart password cracker will use a rainbow table program that incorporates a dictionary attack. There are handful to dozens of rainbow table programs for password types. Figure 1.7 shows a popular rainbow table program called Ophcrack (ophcrack.sourceforge.io).

![](img/c78b0f79db6299ee317a35df5629d85f)

Figure 1.7: Ophcrack, a popular rainbow table program

## Password Stealing

One of the most common ways an attacker gets a password is to steal it. They steal it from the user's computer or device or from one of the many sites or services that store their password hash. As explained earlier, if an attacker can gain admin access to a user's computer or device, there are hundreds of hacking tools (such as Mimikatz) that will reveal a user's (and the system's) passwords, either in plaintext or in their hashed forms. Any worth might use one or more of these tools as soon as they gain admin access to a system.

Many automated malware programs, if they successfully exploit a computer or device, will go looking for passwords as either their main objective or one of their primary objectives. They will look for user passwords stored on disk and in memory and steal passwords from browser databases (when the user allows their browser to store their passwords for auto-logons to websites and services requiring authentication).

Any hacker who gains access to a website or service that requires authentication for all users will immediately look for and steal any authentication databases that contain user logon information. This is how password dumps end up on the Internet. Why steal passwords one at a time when you can steal thousands to millions of them for nearly the same effort?

## Password Reuse Risk Is Huge

The biggest risk from any password theft is that even though a password may be stolen from one website or service, it is often reused by the same user at more than one website (and sometimes every website and service they use). Again, as I mentioned, the average user has six or seven passwords that they use. If I was an attacker and I compromise some rinky-dink, no-one-cares-about-website, and find that a logon name roger@banneretc.com has a password of frog11, I'm going to start checking whether that same logon information works on a bunch of other popular websites, like Amazon, Banks, and stock websites as well. And any good hacker will automate that checking process.

Password reuse is a huge risk. One compromise can lead to a bunch of other compromises. Not only can they reveal currently, actively used logons, but they can also reveal patterns between passwords. Most people, if they don't use random passwords, and even if they use different passwords for every website and service, use passwords with a pattern (such as Frog32, Frog33, Frog34...). An attacker seeking that pattern may figure out what the user likes and can break into additional details.

Similarly, sharing passwords is a hazard, especially when they are written down anywhere one can see. It is not uncommon to see de-taped video where password is typed. We were recently giving a lecture on password attacks and on the presentation, laptop, in a general conference room in a state legislature that was freely accessible by the general public. On the laptop was a paper label (see Figure 1.8) that showed the name and password. I chuckled, but I was there to speak about computer security and the laptop that I was to present had the password printed for anyone to use. I said to the host in a kindly way, "You know that printing out a login name and password anywhere one can see is the epitome of what you shouldn't do in computer security. I hope that at least is a stand-alone login and not a networked login that works across your network." I responded, "If you want to tell yourself that makes yourself feel better, sure."

But more importantly, it happens all the time. That customer was far from unique. It points to an inherent issue with passwords and how easy they are to use, and at the same time, how inconvenient they can be for shared assets. I travel for a living, and if I could get a dollar for every hotel check-in lobby desk where I could physically see a documented password from the lobby, I'd have a nice house on the water in the Florida Keys.
