
to teller machines, often making multiple $20 withdrawals instead of cashing a $200 check weekly.

### 30.4.5 Proactive versus Reactive Threats

Some threats and hazards can be addressed proactively, whereas others are inherently reactive. When strategies and tactics are developed to protect a Web presence, the strategies and tactics themselves can induce availability problems.

As an example, consider the common strategy of having multiple name servers responsible for providing the translation of domain names to IP addresses. It is required before a domain name (properly referred to as a Domain Name System [DNS] zone) can be entered into the root-level name servers, that at least two name servers be identified to process name resolution requests. Name servers are a prime example of resources that should be geographically diverse.

Updating DNS zones requires care. If an update is performed improperly, then the resources referenced via the symbolic DNS names will become unresolvable, regardless of the actual state of the Web server(s) and related infrastructure. The risk calculus involving DNS names is further complicated by the common, efficient, and appropriate practice of designating ISP name servers as the primary mechanism for the resolution of domain names. In short, name translation provides a good example of the possible risks that can affect a Web presence.

### 30.4.6 Threat and Hazard Assessment

Some threats are universal. Others are specific to an individual environment. The most devastating and severe threats are those that simultaneously affect large areas or populations, where efforts to repair damage and correct the problem are hampered by the scale of the problem. Differences in perspective can impede effective response. What seems a minor outage to a carrier may be a business-threatening outage to a customer.

On a basic level, threats can be divided into several categories. The first is between deliberate acts and accidents. Deliberate acts comprise actions done with the intent to damage the Website or its infrastructure. Accidents include natural phenomena (acts of God) and clumsiness, carelessness, and unconsidered consequences (acts of clod).

Broadly put, a deliberate act is one whose goal is to impair the system. Deliberate acts come in a broad spectrum of skill and intent. For the purpose of risk analysis and planning, deliberate acts against infrastructure providers can often appear to be acts of God. To an organization running a Website, an employee attack against a telephone carrier appears simply as one more service interruption of unknown origin.

No enterprise or agency should consider itself an unlikely target. Past high-profile incidents have targeted the FBI (May 26 and 27, 1999), major political parties, and interest groups in the United States. On the consumer level, numerous digital subscriber line (DSL)-connected home systems have been targeted for subversion as preparation for the launching of DDoS attacks. In 2007, several investigations resulted in the arrest of several individuals for running so-called botnets (ensembles of compromised computers). These networks numbered hundreds of thousands of machines.²⁰ Recently, Aramco was victimized by a major attack²¹; as were major Korean financial institutions.²² The potential for such networks to be used for mischief cannot be underestimated.

## 30.5 OPERATIONAL REQUIREMENTS

Internet-visible systems are those with any connection to the worldwide Internet. It is tempting to consider protecting

or near Earth. The Space Shuttle had Internet access; as does the International Space Station. Under these circumstances, the possibilities for attack or inadvertent misuse are limitless.

Despite the vast increase in connectivity, some businesses and individuals do not need extensive access to the global Internet for their day-to-day activities, although they may resent being excluded. The case for universal access is therefore a question of business policy and political considerations.

### 30.5.5 Applications Design

Protecting a Website begins with the most basic steps. First, a site processing confidential information should always support the Secure Hypertext Transfer Protocol (HTTPS), typically using Transmission Control Protocol (TCP) port 443. Properly supporting HTTPS requires the presence of an appropriate digital certificate (see Chapter 37).

When the security requirements are uncertain, the site design should err on the side of using HTTPS for communications. Eavesdropping on the Internet is an ever-present hazard. There have been cases of routing database manipulation and state-sponsored surveillance. The Hannaford and TJ Maxx episodes described earlier in this chapter both involved the application of what can only be described as classic signals intelligence (SIGINT) techniques. Even though details on such attacks are often not made public, the voluminous historical literature on communications intelligence (COMINT) and SIGINT from the World War II period makes one point abundantly clear: Encryption of all potentially sensitive traffic is the only way to protect information.

Encryption also should be used within an organization, possibly with a different digital certificate, for sensitive internal communications and transactions. Earlier, it was noted that organizations are not monolithic security domains. This is nowhere more accurate than when dealing with human resources, employee evaluations, compensation, benefits, and other sensitive employee information. There are positive requirements that this information be safeguarded, but few organizations have truly secured their internal networks against internal monitoring. It is far safer to route all such communications through securely encrypted channels. Such measures also demonstrate a good faith effort to ensure the privacy and confidentiality of sensitive information. Such efforts are an important element of an organization’s defense when an incident occurs. Upfront care can significantly reduce legal liability.

Failure to heed these hazards has been at the root of several incidents, including the TJ Maxx and Hannaford affairs.

It is also important to avoid providing all of the authentication information on a single page or, for that matter, in a sequence of pages. When parts of information are suppressed, as, for example, portions of a credit card or account number, the division between suppressed and displayed portions should be maintained. Displaying all of the information, even if it is on different screens, is an invitation to a security breach.

### 30.5.6 Provisioning

Although today’s hardware has unprecedented reliability, any failure of hardware between the customer and the data center will impair an enterprise’s Web presence. For a highly available, front-line Website, the effective requirement is a minimum of two diversely located facilities, each with a minimum of two servers. This is not necessarily an expensive proposition. Fairly powerful Web servers can be purchased for less than $5,000, so the total hardware expenditure for four servers is reasonable, substantially less than the annual cost of a single technician. Cloud-computing, the availability of data center-housed virtual servers as a service (e.g.,

a Website penetration. This breach escalated into a security breach of corporate data systems. It is reported on the TJX Website that at least 45.7 million credit cards were compromised (original reports in USA Today and other publications cite 94 million credit card numbers as being compromised). On November 30, 2007, it was reported that TJX, the parent organization of stores including TJ Maxx and Marshall’s, had agreed to settle bank claims related to VISA cards for US$ 40.9M.²⁶ Also, as of March 2008, a class action suit on behalf of customers was in process of being settled. It called for fees to be paid for each of the plaintiffs for credit monitoring and identity theft, and for new driver’s licenses, as well as $6.5 million to plaintiffs’ counsel. In spite of several such high-profile attacks, the lessons appear not to have been learned. As recently as March 2008, Hannaford Bros. Co. reported that 4.2 million credit card numbers had been exposed, with about 1,800 cases of fraudulent usage reported as of that date. An incident involving the network supporting Sony’s PlayStation 3²⁷ disclosed personal information relating to an estimated 70 million subscribers. Clearly, more stringent controls, care, and safeguards are called for.

### 30.5.8 Multiple Security Domains

The front-line Web servers, and the database servers supporting their activities, comprise two different security domains.

The Web servers, as noted previously, need to be globally accessible via HTTP, HTTPS, and ICMP (while not needed for actual operations, ICMP is often needed for troubleshooting connectivity problems by both customers and providers). In turn, they need to access the application or database servers, and only those servers. In a production environment, it is preferable that application or database servers interact with the Web servers using a dedicated, restricted-use protocol. Properly implemented, such a restriction prevents a hijacked Web server from exploiting its access to the application or database server.

These second-tier servers should be in a security domain separated by restrictive firewalls from the externally accessible front-line Web servers. This seems like a significant expenditure, but it is often less expensive and lower risk than the costs associated with correcting a single significant incident.

### 30.5.9 What Needs to Be Exposed?

Publicly accessible Websites need publicly accessible Web servers to perform their functions. The challenge is to provide the desired services to the public without simultaneously providing access that can be leveraged in unauthorized ways to subvert the site. A penetration incident may lead to significant financial losses, embarrassment, and financial and (in some cases) criminal liability.

Generally speaking, Web servers should not be connected to the public Internet (unless it is possible to verify that all other ports are closed to traffic). All connections to the public network should be made through a firewall system, with the firewall configured to pass only Web-related traffic to those hosts. A DMZ guarded by a firewall often creates a more easily controlled security gateway.

Many sites will opt to place externally visible Web servers in a security compartment of their own, on a separate port of the firewall (if not a totally separate firewall), using a separate DMZ from other publicly accessible resources. These precautions may seem excessive, but having improperly secured systems can lead to security breaches that are extremely difficult to correct and can lead to extended downtime while the problems are analyzed and remedied. In this case, an ounce of prevention is worth substantially more than a pound of cure.
