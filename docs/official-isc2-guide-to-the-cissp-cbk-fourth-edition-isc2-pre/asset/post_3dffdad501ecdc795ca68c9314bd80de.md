
client SSL certificate or an S/MIME certificate may be used for this purpose.

When a user clicks the Submit button on a Web-based form that supports form signing, a dialog box appears that displays the exact text to be signed. The form designer can either specify the certificate that should be used or allow the user to select a certificate from among the client SSL and S/MIME certificates that are installed in Communicator. When the user clicks OK, the text is signed, and both the text and the digital signature are submitted to the server. The server can then use a Red Hat utility called the Signature Verification Tool to validate the digital signature.

## Single Sign-On

Network users are frequently required to remember multiple passwords for the various services they use. For example, a user might have to type a different password to log into the network, collect email, use directory services, and access various servers. Multiple passwords are an ongoing headache for users, system administrators, and security professionals. Users have difficulty keeping track of different passwords, tend to choose poor ones, and tend to write them down in obvious places. Administrators and security professionals must keep track of a separate password database on each server and deal with potential security problems related to the fact that passwords are sent over the network routinely and frequently.

Solving this problem requires some way for a user to log in once, using a single password, and get authenticated access to all network resources that user is authorized to use, without sending any passwords over the network. This capability is known as single sign-on.

Both client SSL certificates and S/MIME certificates can play a significant role in a comprehensive single sign-on solution. A user can log in once, using a single password to the local client’s private-key database, and get authenticated access to all SSL-enabled servers that user is authorized to use without sending any passwords over the network. This approach simplifies access for users because they do not need to enter passwords for each new server. It also simplifies network management because administrators can control access by controlling lists of certificate authorities (CAs) rather than much longer lists of users and passwords.

In addition to using certificates, a complete single sign-on solution must address the need to interoperate with enterprise systems, such as the underlying operating system, that rely on passwords or other forms of authentication.

## Object Signing

Object signing uses standard techniques of public-key cryptography to let users get reliable information about code they download in much the same way they can get reliable information about shrink-wrapped software.

Most importantly, object signing helps users and network administrators implement decisions about software distributed over intranets or the Internet, for example, whether to allow Java applets signed by a given entity to use specific computer capabilities on specific users’ machines.

The "objects" signed with object signing technology can be applets or other Java code, JavaScript scripts, plug-ins, or any kind of file. The "signature" is a digital signature. Signed objects and their signatures are typically stored in a special file called a JAR file.

Software developers and others who wish to sign files using object-signing technology must first obtain an object-signing certificate.

## Contents of a Certificate

The contents of certificates are organized according to the X.509 v3 certificate specification, which has been recommended by the International Telecommunications Union (ITU), an international standards body, since 1988.

Users do not usually need to be concerned about the exact contents of a certificate. However, system administrators and security professionals working with certificates may need some familiarity with the information provided here.

## Distinguished Names

An X.509 v3 certificate binds a distinguished name (DN) to a public key. A distinguished name is a series of name-value pairs, such as uid=Sdog, that uniquely identify an entity, that is, the certificate subject.

For example, this might be a typical DN for an employee of (ISC)²:

```
uid=Sdog, e=Sdog@isc2.org,cn=Snoopy Dog,o=ISC2,c=US
```

The abbreviations before each equal sign in this example have these meanings:

- **Uid** — user ID
- **e** — email address
- **cn** — the user’s common name
- **o** — organization
- **c** — country

DNs may include a variety of other name-value pairs. They are used to identify both certificate subjects and entries in directories that support the Lightweight Directory Access Protocol (LDAP).

The rules governing the construction of DNs can be quite complex and are beyond the scope of this discussion. For comprehensive information about DNs, see "A String Representation of Distinguished Names" at the following URL:

http://www.ietf.org/rfc/rfc1485.txt

## A Typical Certificate

Every X.509 certificate consists of two sections:

The data section includes the following information:

- The version number of the X.509 standard supported by the certificate.
- The certificate’s serial number. Every certificate issued by a CA has a serial number that is unique among the certificates issued by that CA.
- Information about the user’s public key, including the algorithm used and a representation of the key itself.
- The DN of the CA that issued the certificate.
- The period during which the certificate is valid (for example, between 10:00 p.m. on September 3, 2014 and 10:00 p.m. September 3, 2016)
- The DN of the certificate subject (for example, in a client SSL certificate this would be the user’s DN), also called the subject name.
- Optional certificate extensions, which may provide additional data used by the client or server. For example, the certificate type extension indicates the type of certificate (whether it is a client SSL certificate, a server SSL certificate, a certificate for signing email, and so on). Certificate extensions can also be used for a variety of other purposes.

The **signature** section includes the following information:

- The cryptographic algorithm, or cipher, used by the issuing CA to create its own digital signature.
- The CA’s digital signature, obtained by hashing all of the data in the certificate together and encrypting it with the CA’s private key.

Here are the data and signature sections of a certificate in human-readable format:

Certificate:
Data:
Version: v3 (0x2)
Serial Number: 3 (0x3)
Signature Algorithm: PKCS #1 MD5 With RSA Encryption
Issuer: OU=ABC123 Certificate Authority, O=ABC123, C=US
Validity:
Not Before: Friday Aug 18 18:36:25 2000
Not After: Sun Aug 18 18:36:25 2002
Subject: CN=Snoopy Dog, OU=Dog House, O=ABC123, C=US
Subject Public Key Info:
Algorithm: PKCS #1 RSA Encryption
Public Key:
Modulus:
00:ca:fa:79:98:8f:19:f8:d7:de:e4:49:80:48:e6:2a:2a:86:
ed:27:40:4d:86:b3:05:c0:01:bb:50:15:c9:de:dc:85:19:22:
43:7d:45:6d:71:4e:17:3d:f0:36:4b:5b:7f:a8:51:a3:a1:00:
98:ce:7f:47:50:2c:93:36:7c:01:6e:cb:89:06:41:72:b5:e9:
73:49:38:76:ef:b6:8f:ac:49:bb:63:0f:9b:ff:16:2a:e3:0e:
9d:3b:af:ce:9a:3e:48:65:de:96:61:d5:0a:11:2a:a2:80:b0:
7d:d8:99:cb:0c:99:34:c9:ab:25:06:a8:31:ad:8c:4b:aa:54:91:f4:15
Public Exponent: 65537 (0x10001)
Extensions:
Identifier: Certificate Type
Critical: no
Certified Usage:
SSL Client
Identifier: Authority Key Identifier
Critical: no
Key Identifier:
f2:f2:06:59:90:18:47:51:f5:89:33:5a:31:7a:e6:5c:fb:36:26:c9
Signature:
Algorithm: PKCS #1 MD5 With RSA Encryption
Signature:
6d:23:af:f3:d3:b6:7a:df:90:df:cd:7e:18:6c:01:69:8e:54:65:fc:06:
30:43:34:d1:63:1f:06:7d:c3:40:a8:2a:82:c1:a4:83:2a:fb:2e:8f:fb:
f0:6d:ff:75:a3:78:f7:52:47:46:62:97:1d:d9:c6:11:0a:02:a2:e0:cc:
2a:75:6c:8b:b6:9b:87:00:7d:7c:84:76:79:ba:f8:b4:d2:62:58:c3:c5:
b6:c1:43:ac:63:44:42:fd:af:c8:0f:2f:38:85:6d:d6:59:e8:41:42:a5:
4a:e5:26:38:ff:32:78:a1:38:f1:ed:dc:0d:31:d1:b0:6d:67:e9:46:a8:d:c4
Here is the same certificate displayed in the 64-byte-encoded form interpreted by software:
-----BEGIN CERTIFICATE-----
MIICKzCCAZSGaWIBAgIBAzANBgkqhkiG9w0BAQQFADA3MQswCQYDVQQGEwJVUzER
MA8GA1UEChMITmV0c2NhcGUxFTATBgNVBAsTDFN1cHJpeWEncyBDQTAeFw05NzEw
MTgwMTM2MjVaFw05OTE...
-----END CERTIFICATE-----
