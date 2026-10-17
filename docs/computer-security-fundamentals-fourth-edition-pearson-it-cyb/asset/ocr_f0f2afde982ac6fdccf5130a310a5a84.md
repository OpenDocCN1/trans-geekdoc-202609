A digital signature is not used to ensure the confidentiality of a message but rather to guarantee who sent the message. This is referred to as *nonrepudiation*. Essentially, nonrepudiation means proving who the sender is. Digital signatures are actually rather simple, but they are clever. They simply reverse the asymmetric encryption process. Recall that in asymmetric encryption, the public key (which anyone can have access to) is used to encrypt a message to the recipient, and the private key (which is kept secure and private) can decrypt it. With a digital signature, the sender encrypts something with his private key. If the recipient is able to decrypt that with the sender’s public key, then it must have been sent by the person purported to have sent the message. This process is shown in Figure 8.6.

![](bbox=[0.142, 0.226, 0.626, 0.377])

**Figure 8.6** Digital signatures.

# # Hashing

A *hashing* is a type of cryptographic algorithm that has some specific characteristics. First and foremost, it is one way. That means you cannot unhash something. Second, you get a fixed-length output no matter what input is given. Third, there are no collisions. A collision occurs when two different inputs to the same hashing algorithm produce the same output (called a *hash* or *digest*). Ideally we would like to have no collisions. But the reality is that with fixed-length output, collisions are possible. So the goal is to make collisions so unlikely as to be something we need not think about.

Hashes are exactly how Windows stores passwords. For example, if your password is *password*, then Windows will first hash it and produce something like this:

```
```text
0BD181063899C9239016320B50D3E896693A96DF
```
```

Windows will then store that in the SAM (Security Accounts Manager) file in the Windows System directory. When you log on, Windows cannot unhash your password (because, remember, it is one way). So, what Windows does is take whatever password you type in, hash it, and then compare the result with what is in the SAM file. If they match (exactly), then you can log in.

Storing Windows passwords is just one application of hashing. There are others. For example, in computer forensics it is common to hash a drive before you begin forensic examination. Then later you can hash it again to see if anything was changed (accidently or intentionally). If the second hash matches the first, then nothing has been changed.

There are various hashing algorithms. The two most common of them are MD5 and SHA. (It was SHA-1, but since then later versions, like SHA-256, have become more common.)

# ## MD5

*MD5* is a 128-bit hash that is specified in RFC 1321. It was designed by Ron Rivest in 1991 to replace an earlier hash function, MD4. MD5 produces a 128-bit hash or digest. It has been found to be not as collision resistant as SHA.

# ## SHA