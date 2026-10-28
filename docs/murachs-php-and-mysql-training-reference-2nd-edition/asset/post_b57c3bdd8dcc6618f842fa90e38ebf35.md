
## How to use a secure connection

To prevent others from reading data that is transmitted over the Internet, you can use a *secure connection*. Due to the time it takes to encrypt and decrypt the data that's sent across a secure connection, secure connections are noticeably slower than regular HTTP connections. As a result, you usually use secure connections only when your application passes sensitive data between the client and the server.

### An introduction to secure connections

Figure 21-1 shows a web page that transfers data between the server and the client over a secure connection. To determine if you're transmitting data over a secure connection, you can read the URL. If it starts with https rather than http, then you are using a secure connection. In addition, when you're using a secure connection, a small lock icon typically appears to the left of the URL.

With a regular HTTP connection, all data is sent as unencrypted plain text. As a result, if a hacker intercepts this data, it is easy to read. With a secure connection, though, all data is encrypted before it’s transferred between the client and server. Although hackers can still intercept this data, they won’t be able to read it unless they can break the encryption code.

The *Secure Sockets Layer (SSL)* protocol is an older Internet protocol that lets you transfer data between the server and the client over a secure connection. In contrast, *Transport Layer Security (TLS)* is a newer protocol that’s used for working with secure connections. As a user, it’s hard to tell whether you’re using an SSL connection or a TLS connection. Although TLS is supported by most modern browsers, any server that implements TLS also implements SSL. That way, most browsers can use TLS and older browsers can still use SSL.

When you’re working with secure connections, you’ll find that SSL is often used to describe the connection instead of TLS. That’s because SSL is the older, more established protocol for working with secure connections. In this chapter, the term SSL is used even though the connection is most likely a TLS connection.

### A request made with a secure connection

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_706_0.png)

### Description

- *Transport Layer Security (TLS)* and *Secure Sockets Layer (SSL)* are the two protocols used by the Internet that allow clients and servers to communicate over a *secure connection*.
- TLS is the successor to SSL. Although there are slight differences between SSL and TLS, the protocol remains substantially the same. As a result, they are sometimes referred to as the TLS/SSL protocol or these terms are used interchangeably.
- With SSL, the browser encrypts all data that’s sent to the server and decrypts all data that’s received from the server. Conversely, the server encrypts all data that’s sent to the browser and decrypts all data that’s received from the browser.
- SSL is able to determine if data has been tampered with during transit. It is also able to verify that a server or a client is who it claims to be.
- The URL for a secure connection starts with HTTPS instead of HTTP.
- A web browser that is using a secure connection typically displays a lock icon to the left of the URL for the web page.

## How to get a digital secure certificate

If you want to establish a secure connection with your clients, you must get a digital secure certificate from a trusted source such as those listed in Figure 21-3. These *certification authorities (CAs)* verify that the person or company requesting the certificate is a valid person or company by checking with a *registration authority (RA)*. To obtain a digital secure certificate, you’ll need to provide an RA with information about yourself or your company. Once the RA approves the request, the CA can issue the digital secure certificate.

A digital secure certificate from a trusted source isn’t free, and the cost of the certificate will depend on a variety of factors such as the level of security. As a result, when you purchase a digital certificate, you want one that fits the needs of your website. In particular, you’ll need to decide what *SSL strength* you want the connection to support. SSL strength refers to the level of encryption that the secure connection uses when it transmits data.

In the early days of web programming, many web servers used certificates with 40-bit or 56-bit SSL strength. At this strength, it’s possible for a determined hacker to break the encryption code.

Today, most web servers use 128-bit or higher SSL strength. Although these certificates are more expensive than 40-bit certificates, it’s extremely hard for a hacker to break the encryption code. Since most modern web browsers support 128-bit and 256-bit encryption, they are able to use this SSL strength. Meanwhile, older browsers that don’t support this strength can use whatever lesser strength they support.

Once you purchase a secure certificate, you typically send it to your web host who installs it for your site. Once the certificate is installed, you can use SSL to transmit data over a secure connection.

### Common certificate authorities that issue digital secure certificates

- www.symantec.com/ssl-sem-page
- www.godaddy.com/ssl
- www.globalsign.com
- www.startcom.org
- www.comodo.com

### SSL strengths

| Strength | Pros and Cons |
|---|---|
| 40-bit | Most browsers support it, but it’s relatively easy to break the encryption code. |
| 56-bit | It’s thousands of times stronger than 40-bit strength and most browsers support it, but it’s still possible to break the encryption code. |
| 128-bit | It’s over a trillion times a trillion times stronger than 40-bit strength, which makes it extremely difficult to break the encryption code, but it’s more expensive and not all browsers support it. |
| 256-bit | It’s virtually impossible to break the encryption code, but it’s more expensive and not all browsers support it. |

### Description

- To use SSL in your web applications, you must first purchase a digital secure certificate from a trusted *certification authority* (CA). Once you obtain the certificate, you send it to the people who host your website so they can install it on the server.
- A CA is a company that issues and manages security credentials. To verify information provided by the requestor of the secure certificate, a CA must check with a *registration authority* (RA). Once the RA verifies the requestor’s information, the CA can issue a digital secure certificate.
- Since SSL is built into all major browsers and web servers, installing a digital secure certificate enables SSL.
- *SSL strength* refers to the length of the generated key that is created during the encryption process. The longer the key, the more difficult to break the encryption code.
- The SSL strength that’s used depends on the strength provided by the certificate, the strength supported by the web server, and the strength supported by the browser. If a web server or browser isn’t able to support the strength provided by the certificate, a lesser strength is used.
- It’s considered a best practice to use 128-bit or better SSL strength if you process payments or collect personal information such as social security number, address, date of birth, and so on.

Figure 21-3 — How to get a digital secure certificate

### URLs for working with secure connections on a local system

**Test if secure connections are configured correctly**

```
https://localhost/
```

**Request a secure connection**

```
https://localhost/book_apps/ch21_ssl/
```

**Return to a regular connection**

```
http://localhost/book_apps/ch21_ssl/
```

### URLs for working with secure connections over the Internet

**Request a secure connection**

```
https://www.murach.com/
```

**Return to a regular connection**

```
http://www.murach.com/
```

### A warning page for the security certificate

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_712_0.png)

### Description

- To request a secure connection, use an absolute URL that starts with https.
- Once you establish a secure connection, you can use relative URLs to continue using the secure connection.
- To return to a regular HTTP connection after using a secure connection, use an absolute URL that starts with http.
