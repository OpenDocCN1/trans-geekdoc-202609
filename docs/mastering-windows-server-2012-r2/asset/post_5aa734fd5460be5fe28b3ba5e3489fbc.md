
# UNDERSTANDING FS KEY COMPONENTS AND TERMINOLOGY

metadata used to create a trust between the claims provider and the relying party. Federation trusts are required for user accounts to travel securely between organizations, applications, and services. We will create a trust together in the chapter.

**Federation Server** A federation server is a server that has been built and configured for the AD FS role. [Wait, checking text flow...]

**Federation Server Farm** When you cluster multiple federation servers to act as a single federation server on the same load-balanced network, the cluster of servers is referred to as a federation farm. The farm can contain of many devices as federation servers, proxies, and AD FS web agents.

**Federation Server Proxy** A federation server proxy is a server that is placed outside the corporate network to provide an intermediary proxy service between your publicly firewalled corporate network and clients on the Internet. In order to allow remote access to the cloud, from a smartphone, home computer, or internet kiosk, you need to deploy a federation server proxy to act as mediator between the Internet and the corporate network.

**Network Load Balancer** When you have multiple federation servers running together in federation server, it is an AD FS requirement to balance the load between servers using sort of load balancer (NLB). The NLB can be a piece of hardware or a switch of software such as the built-in NLB functionality with Windows Server. Adding this very point provides excellent advantages. In addition to balancing the AD environment, having multiple federation servers with an NLB will provide fault tolerance and high availability as added bonuses to the AD FS infrastructure.

**Relying Party** A relying party is any organization, application, or service that consumes the claims that are issued from an account provider. A partner organization or cloud service like Office 365 is an excellent example of a relying party.

**Relying Party Trust** A relying party trust is a trust that is created between two federation servers. Similar to an Active Directory forest, a relying party trust creates the secure tunnel that provides user accounts the ability to securely authenticate into applications and services between entities. Please note: Active Directory forest and trusts work independently from one another.

**Resource Partner** The resource partner is the other organization of the federation trust relationship with the account partner. The job of the resource partner is to host the applications and services that the account partner’s users wish to access via SSO. The resource partner inspects the security tokens sent by the account partner and decides whether to allow that user access to its applications and services.

Although there are many additional pieces that make up the entire spectrum of AD FS terminology, these terms and definitions provide a general understanding of the underlying framework.

Let’s also take a minute to examine the four different types of certificates that are used in AD FS infrastructure. These trusted certificates are required by AD FS and are listed in the next section.

# Understanding AD FS Certificates

Certificates are fundamental building blocks for allowing AD FS to work and function properly. Every client that has to SSO capabilities needs to have and be able to accept these secure certificates. Certificates are created and issued by both IIS (Internet Information Services) and AD FS to maintain trusted relationships. You use these certificates to communicate securely with all the different objects in an AD FS environment. You cannot implement AD FS as an SSO solution using these trusted certificates. We will create and add certificates using both IIS and AD FS later in this chapter; first let's see how they are used.

**Token-Signing Certificate** A token-signing certificate is a secure X509 certificate that is used by a federation server to digitally sign the security tokens that are created and dispersed throughout AD FS infrastructure. You are required to use a token-signing certificate on a federation server for AD FS to function. Of the four certificates discussed here, this is the one AD FS actually uses to sign tokens. You can have multiple token-signing certificates. In fact, it is best practice to keep a backup in a revolving cycle so that in case the active certificate expires or becomes compromised, you have a backup to roll over.

**Token-Decryption Certificate** The token-decryption certificate is used in hand with the token-signing certificate. When an account partner issues a security token for a user to access an application or service on the resource partner's side of the house, the federation server in the resource partner's house is able to decrypt the certificate and verify that it has not changed or tampered with.

**Secure Socks Layer Certificate** The SSL certificate is designed to be used with traffic between federation server proxies and clients on the Internet. For any web service or client to securely communicate with the federation server proxy, the client must be able to accept the SSL certificate issued by the proxy. Notices a trend here? Here AD FS is secured by encryption.

**Service Communication** The service certificate provides the same functionality as SSL but is used for communication between services within the environment. AD FS is secured by encryption. Now that you have general understanding of which certificates are required by AD FS, let's discuss how they are used.
