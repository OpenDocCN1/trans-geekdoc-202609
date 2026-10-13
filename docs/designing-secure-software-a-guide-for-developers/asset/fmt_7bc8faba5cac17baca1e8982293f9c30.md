
# HTTPS：从可选到必选

Nobody ever disputed the need for HTTPS to secure financial transactions on the web, but major sites delayed going fully HTTPS for far too long. (For example, Facebook only did so in 2013.) When first implemented, the protocol had subtle flaws, and the necessary computations were too heavyweight for the hardware at the time to justify widespread adoption. The good news is that, over time, developers fixed the bugs and optimized the protocol. Thanks to protocol optimizations, more efficient crypto algorithms, and faster processors, HTTPS is fast, robust, and rapidly approaching ubiquity today. It’s widely used to protect private data communications, but even for a website only serving public information, HTTPS is important to ensure authenticity and strong integrity. In other words, it provides assurance that the client is communicating with the bona fide server named in the request URL, and that data transmitted between them has not been snooped on or tampered with. Today, it’s difficult to think of any good reason *not* to configure a website to use HTTPS exclusively. That said, there are still plenty of non-secure HTTP websites out there. If you use them, keep in mind that the nice security properties of HTTPS do not apply, and take appropriate precautions.

## 理解 HTTPS 的安全边界

Understanding precisely what HTTPS does (and does not do) to secure the client/server interaction is critical in order to grasp its value, how it helps, and what it can and cannot change. In addition to assuring server authenticity and the confidentiality and integrity of web requests and response content, the secure channel protects the URL path (in the first line of the request headers—for example, `GET /path/page.html?query=secret#fragment`), preventing anyone who’s snooping from seeing what page of the website the client requested. (HTTPS can optionally also authenticate the client to the server.) However, the HTTPS traffic itself is still observable over the network, and because the IP addresses of the endpoints are unprotected, eavesdroppers can often deduce the identity of the server.

[Table 11-1](#c11.xhtml#table11-1) compares of the security attributes of HTTP and HTTPS, in terms of the capabilities of an attacker lurking between the two endpoints of a client/server communication.

### 表 11-1：HTTP 与 HTTPS 安全属性对比

| **Can an attacker. . .** | **HTTP** | **HTTPS** |
| --- | --- | --- |
| See web traffic between client/server endpoints? | Yes | Yes |
| Identify the IP addresses of both client and server? | Yes | Yes |
| Deduce the web server’s identity? | Yes | Sometimes (see note below) |
| See what page within the site is requested? | Yes | No (in encrypted headers) |
| See the web page content and the body of POSTs? | Yes | No (encrypted) |
| See the headers (including cookies) and URL (including the query portion)? | Yes | No |
| Tamper with the URL, headers, or content? | Yes | No |

## Let’s Encrypt：消除证书获取障碍

As HTTPS and the technology environment matured, the last obstacle to broad adoption was the overhead of getting server certificates. Whereas larger companies could afford the fees that trusted certificate authorities charged and had staff to manage the renewal process, the owners of smaller websites balked at the extra cost and administrative overhead. By 2015, HTTPS was mature and most internet-connected hardware operated fast enough to handle it, and with awareness of the importance of web privacy growing quickly, the internet community was approaching a consensus that it needed to secure the majority of web traffic. The lack of free and simple server certificate availability proved the biggest remaining obstacle.

Thanks to strong promotion by the wonderful Electronic Frontier Foundation and sponsorship from a wide range of industry companies, Let’s Encrypt, a product of the nonprofit Internet Security Research Group, offers the world a free, automated, and open certificate authority. It provides Domain Validation (DV) certificates, free of charge, to any website owner. Here’s a simplified explanation of how Let’s Encrypt works. Keep in mind that the following process is automated in practice:

1.  Identify yourself to Let’s Encrypt by generating a key pair and sending the public key.
2.  Query Let’s Encrypt, asking what you need to do to prove that you control the domain.
3.  Let’s Encrypt issues a challenge, such as provisioning a specified DNS record for the domain.
4.  You satisfy the challenge by creating the requested DNS record and ask Let’s Encrypt to verify what you did.
5.  Once verified, the private key belonging to the generated key pair is authorized for the domain by Let’s Encrypt.
6.  Now you can request a new certificate by sending Let’s Encrypt a request signed by the authorized private key.

Let’s Encrypt issues 90-day DV certificates and provides a “certbot” to handle automatic renewals. With automatically renewable certificates available as a free service, secure web serving today has widely become a turnkey solution at no additional cost. HTTPS comprised more than 85 percent of web traffic in 2020, more than double the 40 percent level of 2016, when Let’s Encrypt launched.

## 证书类型：DV、OV 与 EV

A DV certificate is usually all you need to prove the identity of your website. DV certificates simply assert the authenticated web server’s domain name, and nothing more. That is, the `example.com` certificate is only ever issued to the owner of the `example.com` web server. By contrast, certificates offering higher levels of trust, such as Organization Validation (OV) and Extended Validation (EV) certificates, authenticate not only the identity of the website but also, to some extent, the owner’s identity and reputation. However, with the proliferation of free DV certificates, it’s increasingly unclear if the other kinds will remain viable. Few users care about such distinctions of trust, and the technical as well as legal nuances of OV and EV certificates are subtle. Their precise benefits are challenging to grasp unless (and even if) you are a lawyer.

## 强制 HTTPS 与防范降级攻击

Once you’ve set up your web server to use the HTTPS protocol with a certificate, you must make sure it *always* uses HTTPS. To ensure this, you must reject *downgrade attacks*, which attempt to force the communication to occur with weak encryption or without encryption. These attacks work in two ways. In the simplest case, the attacker tries changing an HTTPS request to HTTP (which can be snooped and tampered with), and a poorly configured web server might be tricked into complying. The other method exploits the HTTPS protocol options that let the two parties negotiate *cipher suites* for the encrypted channel. For example, the server may be able to “speak” one set of crypto “dialects,” and the client might “speak” a different set, so up front, they need to agree on one that’s in both their repertoires. This process opens the door to an attacker, who could trick both parties into selecting an insecure choice that compromises security.

The best defense is to ensure your HTTPS configuration only operates with secure modern cryptographic algorithms. Judging exactly which cipher suites are secure is highly technical and best left to cryptographers. You must also strike a balance to avoid excluding, or degrading the experience of, older and less powerful clients. If you don’t have access to reliable expert advice, you can look at what major trustworthy websites do and follow that. Simply assuming that the default configuration will be secure forever is a recipe for failure.
