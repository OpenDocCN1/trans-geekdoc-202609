```
172.17.0.2 - - [30/Sep/2017 00:50:32] "POST /asdf HTTP/1.1" 200 -
172.17.0.2 - - [30/Sep/2017 00:50:32] a=
LICENSE
NOTICE
RELEASE-NOTES
```

It worked, and now even though our exploit doesn’t return data back to the web page, we can create success and error conditions to get information about what’s happening on the back end. We can also use built-in tools to send data around so that we can see the interaction.

The source code is too long to include in this chapter, but if you want to see the code that’s being executed, look at the 42627.py file for the code. At its heart, this exploit is similar to the last one we did in that it’s using ProcessBuilder to execute a command. In this instance, though, the exploit is in XML that’s parsed as part of the exception.

# Padding Oracle Attacks

Padding oracle attacks first became mainstream with a .NET vulnerability in 2014 that allowed you to change viewstate information. The viewstate contains information about the user’s state within an application, so the user could potentially change access rights, execute code, and more with this exploit. After the exploit was released, people realized that lots of devices and applications were vulnerable to the same attack, so the exploit got more attention and tools were released to help with this type of attack.

What is a padding oracle attack, though? When an encryption type called Cipher Block Chaining (CBC) is used, data is split into blocks for encryption. Each block is seeded for encryption by the previous block’s data, which creates additional randomness so that the same message sent to different people will appear differently. When there isn’t enough data to fill out a block, the block is padded with additional data to reach the block length. If all the blocks are full at the end, then an additional block is added that is empty.

With the padding oracle attack, we can take advantage of the way the encryption works to figure out the data in the last block based on possible padding values. With the last block solved, we can move back through the data while decrypting it. Once the data is decrypted, we can re-encrypt it and send it in place of the original data. Ideally, the data being sent would have a checksum to identify whether it has been modified, but vulnerable hosts don’t do this computation, so we can modify things at will.

![](bbox=[0.13, 0.78, 0.25, 0.85])

NOTE This is a very complex subject with tons of math at play. A great article by Bruce Barnett on the subject is provided in the “For Further Reading” section. If you want to