
## Figure 5-23 Kerberos Ticket Granting Service

![](img/073342643701cc54eb7875c41ab92ef2_276_0.png)

When the Kerberos server sends the service ticket to S, it also sends the session key with V encrypted with a key that only the supplicant and the Kerberos server share. S uses this shared key to decrypt the symmetric session key with V.

Now that both hosts have the same symmetric session key, they can begin communicating back and forth, encrypting their transmission for confidentiality with the session key.

If you have been following this closely, you undoubtedly ask, “Hey, how does V know that S is not an impostor?” The answer is that if another host, say X, intercepts the service ticket and sends it to V, X will not know the symmetric session key. It will not be able to communicate with V using this key. Consequently, there is no need to inform V explicitly that S is authenticated and has permissions for the conversation. V simply acts as if this was the case, and if it is not, the communication will break down. In other words, the system fails safely.

## Test Your Understanding

- 26. a. In Kerberos, distinguish between the ticket granting ticket and the service ticket.
- b. What information does the service ticket give the verifier?
- c. How does the supplicant get the symmetric session key?
- d. Is the verifier notified explicitly that the supplicant has been authenticated? Explain.

## 5.10 Directory Servers

## 5.10 Describe how directory servers work.

RADIUS, Kerberos, and other central authentication servers improve centralization, but two problems remain in most large firms.

- First, most large firms find themselves with multiple RADIUS, Kerberos, and other central authentication servers.
- In addition, most large companies have made a strategic decision to use directory servers as their place to store data centrally in the firm.

## What Are Directory Servers?

**Directory servers** are central repositories for information about people, equipment, software, and databases. Directory servers store authentication, authorization, and auditing information required for security. However, directory servers are not limited to security information. They store information about host configurations, employee contact information such as telephone numbers, and a great deal of general information.

> Security information is only one aspect of directory server information.

## Hierarchical Data Organization

Database courses usually focus on relational databases. Relational databases are good when there are about an equal number of accesses and updates. However, when there are many more accesses than updates, as there are with directory servers, a **hierarchical database organization** may be better. As Figure 5-24 illustrates, directory servers use a hierarchical database organization. The directory server database schema is a hierarchical collection of **objects (nodes)**.

- The top-level object is the *organization* (O). This is the name of the organization. In the figure, this is the University of Waikiki. The *common name* (CN) is a shortcut way of referring to this node.
- Below the organizational level are several *organizational unit* (OU) objects. In the figure, the three organizational units are Astronomy, Business, and Computer Science. There probably are several more OUs not shown in the figure. Usually, the management of the OU’s data is at least partially delegated to the organizational unit.
- There may be several levels of organizational units in the hierarchical structure, but this directory server only has one level of OU.
- The next level consists of more nodes. In this case, the nodes are applications, faculty members, and routers. This emphasizes that directory servers are not limited to information about people.
- Under faculty, there are many people objects. One of those is for Brown. Brown has sub-nodes for common name (Charlene Brown), e-mail address, and digital certificate.

## Figure 5-24 Directory Server Organization

![](img/073342643701cc54eb7875c41ab92ef2_277_0.png)

## Test Your Understanding

- 27. a. How is information in directory servers organized?
- b. What are the top two levels of the organization?
- c. Do directory servers only hold information about people?

## Lightweight Data Access Protocol

Authentication servers communicate with directory servers using the Lightweight Directory Access Protocol (LDAP). Mostly, LDAP is used to retrieve data from the directory server. However, it can also be used to update information in the directory server. Nearly all directory servers support LDAP. Note that LDAP does not govern the internal operations of the directory server—only communication between directory servers and other devices, including authentication servers.

## Test Your Understanding

- 28. What is LDAP’s purpose?

## Use by Authentication Servers

In security, directory servers are important because they are used by central authentication servers such as RADIUS servers and Kerberos servers. Figure 5-25 shows that a directory server can provide authentication information to many authentication servers. Just as authentication servers are valuable because they centralize authentication information, directories provide a higher level of centralization for firms that have many central authentication servers.

## Test Your Understanding

- 29. a. How do central authentication servers often get their authentication information?
- b. What is the advantage of this?

## Active Directory

Microsoft’s directory server product is called Active Directory (AD). Given the widespread use of Microsoft products in corporations, security professionals should understand AD. Figure 5-26 shows a firm with several active directory servers.

## Figure 5-25 Using a Directory Server to Centralize Authentication Information

![](img/073342643701cc54eb7875c41ab92ef2_279_0.png)

## ACTIVE DIRECTORY DOMAINS

As Figure 5-26 shows, companies usually divide their resources into multiple active directory domains. AD domains usually are organizational units. For instance, in a university, an individual school or college may be a domain. The resources of the domain typically are managed by the organizational unit. AD domains may correspond to DNS domains, but they do not have to.

## Domain Controllers

In Figure 5-26, Domain X has a single domain controller server, which controls the resources in the domain. The domain controller has both an active directory database and a Kerberos authentication server program. Consequently, it handles authentication and AD searches within the domain.

## Figure 5-26 Active Directory Domains and Tree

![](img/073342643701cc54eb7875c41ab92ef2_279_1.png)

Domains with Multiple Controllers
Domain Y has *two* domain controllers. The two servers have their AD databases synchronized, so either of them can handle an active directory LDAP request. Having two (or more) domain controllers gives reliability in the event one crashes or is successfully attacked.

Trees
AD domains can be organized into hierarchies called **trees**. The hierarchy in Figure 5-26 has three domains. However, trees can have *many* domains.

Forests
Figure 5-26 shows a simple tree with multiple domains. Some corporations also have multiple trees. They can connect their *multiple trees* together into a **forest**.

Replication
Within a domain, there is total replication between domain controllers. What about replication in trees? The answer is that domain controllers often replicate some of their AD database to domain controllers at the next higher level, but they usually do not replicate all data. Replication across domains at the same level and between forests usually is even more selective.

Fortunately, AD is rich in tools for specifying replication across specific domains. Of course, this same richness requires strong policy control to avoid chaos and Swiss-cheese security.

## Test Your Understanding

- 30.
- a. What is Microsoft’s directory server product?
- b. What is the smallest organizational unit in active directory?
- c. What two things does a domain controller contain?
- d. Can a domain have multiple domain controllers?
- e. What is the advantage of having multiple domain controllers?
- f. Into what larger structures are domains organized?
- g. Into what larger structure can trees be organized?
- h. Describe replication among domain controllers within a single AD domain.
- i. Describe replication between a domain controller in one domain and the domain controller in the parent domain.

## Trust

**Trust** means that one directory server will accept information from another. Several types of trust are possible.

> Trust means that one directory server will accept information from another.

- Trust may be **mutual** (bidirectional). However, **one-way** trust is also possible, in which one directory server trusts another, but this trust is not reciprocated.
- Sometimes, trust is **transitive**. This means that if Directory Server X trusts Directory Server Y, and if Directory Server Y trusts Server Z, then Directory Server X will *automatically* trust Directory Server Z.
- By contrast, if Directory Server X trusts Directory Server Y, and Directory Server Y trusts Directory Server Z, but Directory Server X does *not* automatically trust Directory Server Z, then trust is **intransitive**.
