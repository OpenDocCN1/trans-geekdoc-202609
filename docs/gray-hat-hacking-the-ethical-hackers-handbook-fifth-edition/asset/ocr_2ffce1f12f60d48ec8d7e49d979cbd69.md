NTLMv2 provides two different nonces in the challenge hash creation. The first is specified by the server, and the second by the client. Regardless of whether the server is compromised and has a static nonce, the client will still add complexity through its nonce, thus ensuring that these credentials crack more slowly. This also means that the use of rainbow tables is no longer an efficient way to crack these types of hashes.

![](bbox=[0.13, 0.21, 0.25, 0.29])

NOTE It is worth noting that challenge hashes cannot be used for pass-the-hash attacks. If you don’t know what type of hash you are dealing with, refer to the entry for hashcat Hash Type Reference in the “For Further Reading” section at the end of this chapter. Use the URL provided to identify the type of hash you’re dealing with.

# Using Responder

In order to capture hashes, we need to use a program to encourage the victim host to give up the NetNTLM hashes. To get these hashes, we’ll use Responder to answer the LLMNR and NBNS queries issued. We’re going to use a fixed challenge on the server side, so we’ll only have to deal with one set of randomness instead of two.

# Getting Responder

Responder already exists on our Kali Linux distribution. However, Kali doesn’t always update as frequently as the creator of Responder, Laurent Gaffie, commits updates. Because of this, we’re going to use git to download the latest version of Responder. To ensure we have all the software we need, let’s make sure our build tools are installed in Kali:

```
# apt-get install build-essential git python-dev
```

Now that git is installed, we need to clone the repository. Cloning the repository will download the source code as well as create a location where it is easy to keep our software up to date. To clone the repository, do the following:

```
root@kali:~ # git clone https://github.com/lgandx/Responder.git
Cloning into 'Responder'...
remote: Counting objects: 1324, done.
remote: Total 1324 (delta 0), reused 0 (delta 0), pack-reused 1324
Receiving objects: 100% (1324/1324), 1.53 MiB | 0 bytes/s, done.
Resolving deltas: 100% (860/860), done.
```

In order to update our repository, simply do the following:

```
root@kali:~/Responder # cd Responder/
root@kali:~/Responder # git pull
Already up-to-date.
```