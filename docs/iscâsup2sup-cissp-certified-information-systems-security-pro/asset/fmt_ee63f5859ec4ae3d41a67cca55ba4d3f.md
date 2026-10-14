
# S/MIME

S/MIME relies on the use of X.509 certificates for exchanging cryptographic keys. The public keys contained in these certificates are used for digital signatures and for the exchange of symmetric keys used for longer communications sessions. `RSA` is the only public key cryptographic protocol supported by S/MIME. The protocol supports the `AES` and `3DES` symmetric encryption algorithms.

Despite strong industry support for the S/MIME standard, technical limitations have prevented its widespread adoption. Although major desktop mail applications support S/MIME email, mainstream web-based email systems do not support it out of the box (the use of browser extensions is required).

## Web Applications

Encryption is widely used to protect web transactions. This is mainly because of the strong movement toward e-commerce and the desire of both e-commerce vendors and consumers to securely exchange financial information (such as credit card information) over the web. We’ll look at the two technologies that are responsible for the small lock icon within web browsers—Secure Sockets Layer (`SSL`) and Transport Layer Security (`TLS`).

`SSL` was developed by Netscape to provide client/server encryption for web traffic. Hypertext Transfer Protocol Secure (`HTTPS`) uses port `443` to negotiate encrypted communications sessions between web servers and browser clients. Although `SSL` originated as a standard for Netscape browsers, Microsoft also adopted it as a security standard for its popular Internet Explorer browser. The incorporation of `SSL` into both of these products made it the de facto internet standard.

`SSL` relies on the exchange of server digital certificates to negotiate encryption/decryption parameters between the browser and the web server. `SSL`’s goal is to create secure communications channels that remain open for an entire web browsing session. It depends on a combination of symmetric and asymmetric cryptography. The following steps are involved:

1.  When a user accesses a website, the browser retrieves the web server’s certificate and extracts the server’s public key from it.
2.  The browser then creates a random symmetric key, uses the server’s public key to encrypt it, and then sends the encrypted symmetric key to the server.
3.  The server then decrypts the symmetric key using its own private key, and the two systems exchange all future messages using the symmetric encryption key.

This approach allows `SSL` to leverage the advanced functionality of asymmetric cryptography while encrypting and decrypting the vast majority of the data exchanged using the faster symmetric algorithm.

In 1999, security engineers proposed `TLS` as a replacement for the `SSL` standard, which was at the time in its third version. As with `SSL`, `TLS` uses TCP port `443`. Based on `SSL` technology, `TLS` incorporated many security enhancements and was eventually adopted as a replacement for `SSL` in most applications. Early versions of `TLS` supported downgrading communications to `SSL v3.0` when both parties did not support `TLS`. However, in 2011, `TLS v1.2` dropped this backward compatibility.

In 2014, an attack known as the Padding Oracle On Downgraded Legacy Encryption (`POODLE`) demonstrated a significant flaw in the `SSL 3.0` fallback mechanism of `TLS`. In an effort to remediate this vulnerability, many organizations completely dropped `SSL` support and now rely solely on `TLS` security.

### Steganography and Watermarking

`Steganography` is the art of using cryptographic techniques to embed secret messages within another message. Steganographic algorithms work by making alterations to the least significant bits of the many bits that make up image files. The changes are so minor that there is no appreciable effect on the viewed image. This technique allows communicating parties to hide messages in plain sight—for example, they might embed a secret message within an illustration on an otherwise innocent web page.

Steganographers often embed their secret messages within images or `WAV` files because these files are often so large that the secret message would easily be missed by even the most observant inspector. Steganography techniques are often used for illegal or questionable activities, such as espionage and child pornography.

Steganography can also be used for legitimate purposes, however. Adding digital watermarks to documents to protect intellectual property is accomplished by means of steganography. The hidden information is known only to the file’s creator. If someone later creates an unauthorized copy of the content, the watermark can be used to detect the copy and (if uniquely watermarked files are provided to each original recipient) trace the offending copy back to the source.

Steganography is an extremely simple technology to use, with free tools openly available on the internet. [Figure 7.2](#c07.xhtml#figure7-2) shows the entire interface of one such tool, `iSteg`. It simply requires that you specify a text file containing your secret message and an image file that you wish to use to hide the message. [Figure 7.3](#c07.xhtml#figure7-3) shows an example of a picture with an embedded secret message; the message is impossible to detect with the human eye.

![FIGURE 7.2 Steganography tool](images/c07f002.jpg)

[**FIGURE 7.2**](#c07.xhtml#figureanchor7-2) Steganography tool

![FIGURE 7.3 Image with embedded message](images/c07f003.jpg)

[**FIGURE 7.3**](#c07.xhtml#figureanchor7-3) Image with embedded message

## Digital Rights Management

`Digital rights management` (`DRM`) software uses encryption to enforce copyright restrictions on digital media. Over the past decade, publishers attempted to deploy `DRM` schemes across a variety of media types, including music, movies, and books. In many cases, particularly with music, opponents met `DRM` deployment attempts with fierce opposition, arguing that the use of `DRM` violated their rights to freely enjoy and make backup copies of legitimately licensed media files.

### Music DRM

The music industry has battled pirates for years, dating back to the days of homemade cassette tape duplication and carrying through compact disc and digital formats. Music distribution companies attempted to use a variety of `DRM` schemes, but most backed away from the technology under pressure from consumers.

The use of `DRM` for purchased music slowed dramatically when, facing this opposition, Apple rolled back their use of `FairPlay DRM` for music sold through the iTunes Store. Apple co-founder Steve Jobs foreshadowed this move when, in 2007, he issued an open letter to the music industry calling on them to allow Apple to sell DRM-free music. That letter read, in part:

> The third alternative is to abolish DRMs entirely. Imagine a world where every online store sells DRM-free music encoded in open licensable formats. In such a world, any player can play music purchased from any store, and any store can sell music which is playable on all players. This is clearly the best alternative for consumers, and Apple would embrace it in a heartbeat. If the big four music companies would license Apple their music without the requirement that it be protected with a DRM, we would switch to selling only DRM-free music on our iTunes store. Every iPod ever made will play this DRM-free music.

The full essay is no longer available on Apple’s website, but an archived copy may be found at [http://bit.ly/1TyBm5e](http://bit.ly/1TyBm5e).

Currently, the major use of `DRM` technology in music is for subscription-based services such as Napster and Kazaa, which use `DRM` to revoke a user’s access to downloaded music when their subscription period ends.

### Movie DRM

The movie industry has used a variety of `DRM` schemes over the years to stem the worldwide problem of movie piracy. Two of the major technologies used to protect mass-distributed media are as follows:
