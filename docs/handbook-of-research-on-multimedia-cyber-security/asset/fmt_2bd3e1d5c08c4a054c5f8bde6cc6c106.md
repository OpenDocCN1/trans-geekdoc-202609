
# Pseudonyms in the Scheme of Authentication (HSK-AKA) for the Achievement of IMSI

Pseudonyms in the scheme of authentication (HSK-AKA) for the achievement of IMSI were proposed by Hamandi et. al. (2013). The scheme consumes network bandwidth, given that the proposed scheme of authentication must reach the HSS. In addition, the network entities—mobility and management entities and the user equipment—do not have the capability for checking the pseudonyms’ accuracy. Hence, the malicious attacker remains a problem.

The user equipment’s permanent ID proposes a scheme of pseudonym-based authentication for the preservation of IMSI privacy. On the other hand, the anticipated scheme of authentication must reach the HSS, which needs the consumption of more bandwidth. In addition, the proposed scheme depended on a novel function’s set, which might be or might not be appropriate for the LTE network infrastructure.

Also, a pseudonym for the preservation of IMSI privacy in the LTE authentication scheme was utilized by Parne et al. (2019). The traceable attack remains a challenge provided that attackers have the capability to associate amongst two permanent pseudonyms as proved by Haddad (2017).

## Vulnerabilities in Existing Authentication Schemes

Above authentication schemes are vulnerable to many threats such as:

*   Shoulder surfing
*   Replay attacks (internal or external recording)

In the next section, researchers propose an authentication scheme that is immune to the above-mentioned threats. The proposed authentication scheme, which we call the **Implicit Password Authentication System (IPAS)**, belongs to the graphical-based techniques. IPAS is lightweight, easy to remember, and hard to break by common attack methods. Also, IPAS is suitable for mobile and non-mobile devices in a friendly and flexible manner.

# IMPLICIT PASSWORD AUTHENTICATION SYSTEM (IPAS)

Authentication is the first line of defence against compromising confidentiality and integrity. Though traditional login/password-based schemes are easy to implement, they have been subjected to several attacks. As an alternative, the token- and biometric-based authentication systems were introduced. However, they have not improved substantially enough to justify the investment. Thus, a variation to the login/password scheme, viz. a graphical scheme was introduced, but it also suffered due to shoulder surfing and screen dump attacks. In this section, researchers introduce a framework called the **Implicit Password Authentication System (IPAS)** initiated by Almuairfi et al. (2011), which is immune to the common attacks suffered by other authentication schemes.

## Overview

IPAS is similar to a graphical scheme with some fine differences. In every “what you know to type” authentication scheme of which we are aware, the server requests the user to reproduce the fact given to the server at the time of registration. This is also true in graphical passwords such as PassPoint.

In IPAS, we consider the password as a piece of information known to the server at the time of registration. At the time of authentication, the user gives this information in an implicit form that can be understood only by the server. IPAS may also be implemented in any client-server environment, where we need to authenticate a human as a client (IPAS will not work in machine-to-machine authentication). The authors also assume that the server has enough hardware resources, such as RAM and CPU. This is not unrealistic as high-end servers are becoming cheaper day by day.

## IPAS Implementation

The authentication system usually has both a client and server component. Each component facilitates the implementation of a standard interface function and an initialization function that registers the module with the system. In fact, the client-server model is a more scalable approach to client authentication than other models.

Thus, the design model of IPAS is a client-server model where both ends must be trusted. Any client is authenticated when connected to the server (cloud) and trusted afterward. The authenticated user actions are checked against a specific access control policy that controls allowed or denied access.

## IPAS Design Stage

A client device could be any portable device, such as a laptop or mobile phone. Mobile phones have become increasingly important in our daily lives. One main reason for this is that an increasing number of functions have been integrated within mobile phones, such as Internet browsing, mobile banking, and shopping. Some of the latest smartphones are similar in performance to the high-end desktop PCs of a decade ago.

People are now paying much more attention to their mobile phones than they did before, which makes mobile phones relatively hard to lose, compared with devices that users do not care very much about, such as USB flash drives. However, having such an advantage in relation to security is not enough to prove that mobile phones are more suitable for online banking authentication than USB drives. Therefore, an in-depth inspection of mobile phones, malware and applications is desirable.

IPAS has considered this issue by allowing users to access their accounts on the move, with a high level of security and usability. Our system does not require any high-end specialized software. The presence of a standard web browser with an Internet connection is enough to launch our application. Thus, our system may very well scale from a smartphone to desktop PCs.

On the other side, the server (at cloud) is the other entity of our design model in IPAS. However, we assume that the communication between client and server is secure and trusted through protocols like **SSL (Secure Socket Layer)** and **IPSec** against malicious intermediate nodes caching and making offline guesses. This only adds an extra layer of protection. However, the IPAS authentication process may still work without this assumption.

The server(s) which is located at the cloud side, should be equipped with appropriate safety measures such as firewalls, intrusion detection systems and rapid recovery mechanisms to guarantee information security. The authentication server, which is one of the most important servers in our design model, should contain an **Intelligent Graphical (IG) module** to covert user information/answers into an image.

This image, which implicitly represents the user’s password, will be pushed to the client’s device during the authentication process. The user will be authenticated only if he/she clicks on the right objects in the image that match the stored information. Moreover, a trusted link between the authentication server and the main image database server should take place for access control purposes of such an authentication level.

## IPAS Development Model

In this stage, researchers provide the system requirements which are needed to reform IPAS. Client-server interactions start by defining the needs of each party. Therefore, we need to define the properties of the system which may be used by any organization or in any payment environment.

### Image Database

The image database at the server-side is the heart of our authentication scheme. Depending upon the number of users, the image database may contain tens of thousands to millions of images. The system administrator and/or the user may add more images on a regular basis.

Each image may have more than one “clickable” object. With each clickable-object, one or more text keywords are associated with it. Some objects within the image will be used as a decoy object to increase the security level of IPAS. The relation between the image objects and associated texts play a significant role in our authentication scheme, which is described later in this chapter.

### Registration Phase
