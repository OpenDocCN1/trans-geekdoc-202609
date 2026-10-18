
### 2.10.8. Steganography

Steganography is the process of hiding data in something such that to a casual observer it cannot be detected. Data can be hidden in audio, images, or even [plain text!](https://dl.packetstormsecurity.net/crypt/snow/description.html). The hidden data can also be encrypted if an additional layer of security is required. In the field of security, malicious code may be hidden inside other files using steganographic techniques. This makes it more difficult for tools to find them when searching storage.

## 2.11. Lab: Hash it Out

A `hash` is a one-way cryptographic function that produces a `unique` set of characters for a given `message`. In a perfect world, given a hash you should `not` be able to determine what the original message was, but given a hash and the original message you can check that the hash matches the message. Before we dive into the uses of a hash, lets try to further understand it by looking at a simple and consequently poor hashing algorithm.^(\[[³](#fn3))

**Anagram Hash**

Let’s assume we wanted to hash the message "Hello from Karl" so that we can have a string of characters the uniquely represent that phrase. One way to do it would be to strip all the punctuation in the message, make everything lowercase, and then arrange all the letters alphabetically. "Hello from Karl" becomes "aefhklllmoorr". You can think of it like saying, "There is one 'a' in the message, one 'e' in the message, one 'f' in the message', one 'k' in the message, three 'l’s in the message…​" Now our hash, "aefhklllmoorr", can be used to uniquely identify the phrase.

Now assume Karl wants to send us a message but he can’t trust the person sending the message. He could use the untrusted party to send us the message and then put the hash someplace public like on a website. We could use the hash to know the message came from Karl `and` if anyone else got the hash they would not be able to discern the message because a hash is a one-way function. "aefhklllmoorr" reveals very little about the message, but it can be used to check its accuracy.

Hopefully this is beginning to show the power of hashes. Now lets examine another very common usecase and find out exactly why this is a terrible algorithm.

Assume you run a website where a user uses a password to log in. You want to make sure users are using their password when they log in, but you do not want to store the password on your website. This is quite common. If you website was breached you don’t want to leak a bunch of people’s passwords. What do you do? What you could do is store a hash of their password, hash the password when they try to login, and compare the hashes. For example if our password was "password" using our basic hash algorithm the hash would be "adoprssw". We could store "adoprssw" in our database, use it for comparison during login, and if someone were to ever steal the data in our database they wouldn’t know that the original password is "password". This may prevent an attacker from exploiting the fact that many people use the same password on multiple sites.

The problem is that there are many things that hash to "adoprssw" including "wordpass", "drowsaps", or even the hash we’re storing: "adoprssw". When multiple messages have the same hash it is referred to as a `collision` and this particular algorithm is useless because it generates so many of them.

Now that we understand what hashes do and to some extant how they are possible, lets look at a much more useful hash function.

**MD5**

For this section, we are going to be using Docker and a terminal. [Please follow these directions for installing Docker.](https://docs.docker.com/get-docker/) For Windows you can use the [Windows Terminal app](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701) and in MacOS you can use the preinstalled Terminal app. Gray boxes show the commands as typed into the terminal with typical output where possible. Your prompt (the part shown before the command) may differ depending on your OS.

Start by running a BASH shell on a custom Linux container:

```
ryan@R90VJ3MK:/windir/c/Users/rxt1077/it230/docs$ docker run -it ryantolboom/hash ①
root@8e0962021f85:/②
```

1.  *①* Here we are using the Docker run command interactively (-it) as this container runs bash by default

2.  *②* Notice the new prompt showing that we are root on this container

MD5 is a message-digest algorithm that produces significantly better hashes than our Anagram algorithm. Most Linux distributions include a simple utility for creating an MD5 hash based on a file’s contents. This command is named `md5sum`. Typically this is used to detect if a file has been tampered with. A website may provide links to download software as well as an MD5 hash of the files so that you know what you’ve downloaded is correct. Similarly a security system may keep md5sums (MD5 hashes) of certain critical files to determine if they have been tampered with by malware. Let’s practice taking the md5sum of the `/etc/passwd` file:

```
root@8e0962021f85:/# md5sum /etc/passwd
9911b793a6ca29ad14ab9cb40671c5d7  /etc/passwd ①
```

1.  *①* The first part of this line is the MD5 hash, the second part is the file name

Now we’ll make a file with *your* first name in it and store it in `/tmp/name.txt`:

```
root@8e0962021f85:/# echo "<your_name>" >> /tmp/name.txt ①
```

1.  *①* Substitute your actual first name for `<your\_name>`

For our final activity, lets take a look at some of the weaknesses of hashes.

**Hash Cracking**

Passwords in a Linux system are hashed and stored in the `/etc/shadow` file. Let’s print out the contents of that file to see how it looks:

```
root@7f978dd90746:/# cat /etc/shadow
root:*:19219:0:99999:7:::
daemon:*:19219:0:99999:7:::
bin:*:19219:0:99999:7:::
sys:*:19219:0:99999:7:::
sync:*:19219:0:99999:7:::
games:*:19219:0:99999:7:::
man:*:19219:0:99999:7:::
lp:*:19219:0:99999:7:::
mail:*:19219:0:99999:7:::
news:*:19219:0:99999:7:::
uucp:*:19219:0:99999:7:::
proxy:*:19219:0:99999:7:::
www-data:*:19219:0:99999:7:::
backup:*:19219:0:99999:7:::
list:*:19219:0:99999:7:::
irc:*:19219:0:99999:7:::
gnats:*:19219:0:99999:7:::
nobody:*:19219:0:99999:7:::
_apt:*:19219:0:99999:7:::
karl:$y$j9T$oR2ZofMTuH3dpEGbw6c/y.$TwfvHgCl4sIp0b28YTepJ3YVvl/3UyWKeLCmDV1tAd9:19255:0:99999:7::: ①
```

1.  *①* As you can see here the `karl` user has a long hash immediately after their username

One of the problems with hashes are that if people choose simple passwords, they can be easily cracked by a program that takes a wordlist of common passwords, generates their hashes, and then checks to see if the hash is the same. While a hash may be a one-way function, it is still subject to this type of attack. We’re use a program called [John the Ripper](https://www.openwall.com/john/) and do exactly that.

John the Ripper is already installed on this container along with a simple wordlist. We will tell it to use the default wordlist to try and determine what the password is that matches karl’s hash in `/etc/shadow`:

```
root@8e0962021f85:/# john --format=crypt --wordlist=/usr/share/john/password.lst /etc/shadow
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
<karl's password>             (karl)
1g 0:00:00:01 100% 0.6211g/s 178.8p/s 178.8c/s 178.8C/s lacrosse..pumpkin
Use the "--show" option to display all of the cracked passwords reliably
Session completed
```
