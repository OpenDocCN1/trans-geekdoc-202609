
## 6  
### Feistel Networks  

**In this chapter we will cover the following:**  

```  
![image](Images/image00483.jpeg) Cryptographic keys  
![image](Images/image00483.jpeg) Feistel functions  
![image](Images/image00483.jpeg) Pseudo-Hadamard transforms  
![image](Images/image00483.jpeg) MDS matrix  
![image](Images/image00483.jpeg) S-boxes and P-boxes  
![image](Images/image00483.jpeg) Symmetric algorithms  
![image](Images/image00483.jpeg) Methods for improving symmetric algorithms  
```  

This chapter is the first of two chapters regarding symmetric ciphers. Before I dive into the topic of this chapter, Feistel networks, you need to understand what a symmetric cipher is and the different types of symmetric ciphers. A *symmetric cipher* is an algorithm that uses the same key to decrypt the message that was used to encrypt the message, as demonstrated in [Figure 6-1](#part0015.xhtml#ch06fig01).

![Images](Images/image00611.jpeg)

* * *

**FIGURE 6-1    Symmetric cryptography**

The process is rather straightforward, and a decryption key functions much like a key in a physical door—that is, the same key used to lock the door is used to unlock it. This is probably the modality of cryptography that is easiest for cryptography novices to learn. Symmetric cryptography offers some significant advantages over *asymmetric* cryptography (which we will examine in [Chapters 10](#part0020.xhtml#ch10) and [11](#part0021.xhtml#ch11)). For example, symmetric cryptography is faster than asymmetric and it is just as secure though it uses a smaller key.

Although the classic cryptography discussed in [Chapters 1](#part0009.xhtml#ch01) and [2](#part0010.xhtml#ch02) could be considered symmetric ciphers, for the purposes of our current discussion we are contemplating only modern ciphers. With that in mind, symmetric algorithms can be classified in two major ways: block ciphers and stream ciphers. A block cipher literally encrypts the data in blocks—64-bit blocks are common, although some algorithms use larger blocks (for example, AES uses a 128-bit block). Stream ciphers encrypt the data as a stream, 1 bit at a time.

Modern block ciphers use a combination of substitution and transposition to achieve both confusion and diffusion (recall those concepts from [Chapter 3](#part0011.xhtml#ch03)). Remember that *substitution* is changing some part of the plain text for some matching part of cipher text. The Caesar and Atbash ciphers are simple substitution ciphers. *Transposition* is the swapping of blocks of cipher text. For example, for the text *I like icecream*, you could transpose or swap every three-letter sequence (or block) with the next and get *ikeI l creiceam*. (Of course, modern block ciphers accomplish substitution and transposition at the level of bits, or rather blocks of bits, and this example uses characters. However, the example illustrates the concept.)

There are two major types of block ciphers: *Feistel networks* (such as the Data Encryption Standard, DES) and *substitution-permutation networks* (Advanced Encryption Standard, AES). In this chapter we will examine several Feistel ciphers. Some, such as DES, will be discussed in thorough detail; others will be describe in general terms. [Chapter 7](#part0016.xhtml#ch07) discusses substitution-permutation networks as well as stream ciphers.

It is not critical that you memorize every algorithm in this chapter, even those that are described in detail. It is recommended, however, that you pay particular attention to DES and Blowfish. Then study the other algorithms just enough to understand how they differ from DES and Blowfish. The goal of this chapter is to provide you with a solid understanding of Feistel ciphers.

**Note**

As with previous chapters, I will also provide sources of more information, such as books and web sites. I am aware that web sites may not always be up and available, but they are also easy and free to access. If a given URL is no longer available, I suggest you simply use your favorite search engine to search the topic. My web site, [www.cryptocorner.com/](http://www.cryptocorner.com/), will always include links if you want to explore these topics.

#### Cryptographic Keys  

Before we start looking at Feistel ciphers, you need to have a basic understanding of cryptographic keys and how they are used. With all block ciphers, there are two types of keys: cipher keys and round keys.

The cipher key is a random string of bits that is generated and exchanged between parties that want to send encrypted messages to each other. When someone says a particular algorithm has a certain key size, they are referring to this cipher key. For example, DES uses a 56-bit cipher key. How that key is exchanged between the two parties is not relevant at this point. Later in the chapter, when I discuss asymmetric cryptography and Secure Sockets Layer/Transport Layer Security (SSL/TLS), you’ll read about key exchange.

**Note**

The cipher key is actually a pseudo-random number, but we will discuss that in more detail in [Chapter 12](#part0023.xhtml#ch12). For now, just understand that the cipher key is a number generated by some algorithm, such that it is at least somewhat random. The more random it is, the better.

In addition to the cipher key, all block ciphers have a second algorithm called a *key schedule* which derives a unique key, called a *round key*, from the cipher key for each round of the cipher. For example, DES has a 56-bit cipher key, but it derives 48-bit round keys for each of its 16 rounds. The key schedule is usually rather simple, mostly consisting of shifting bits. Using a key schedule, each round uses a key that is slightly different from the previous round. Because both the sender (who encrypts the message) and the receiver (who must decrypt the message) are using the same cipher key as a starting point and are using the same key schedule, they will generate the same round keys.
