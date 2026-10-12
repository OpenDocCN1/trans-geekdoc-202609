
APIs and C&C centers manage daily IoT operations effectively. Because they are centralized in nature, they have several exploitable weak spots such as:

- Unpatched vulnerabilities: devices, in most cases, run on outdated software because end-users are required to download updates manually and connectivity issues. This leaves them vulnerable to newly discovered threats.
- Weak authentication: IoT devices such as home routers usually have easily decipherable passwords. This makes them an easy target for automated scripts from hackers.
- Vulnerable APIs: some of the major threats that target APIs include distributed denial of service (DDoS), code injections, and Man in the Middle (MITM).

These dangers can be divided into two categories: threats to users and threats to others.

- Data theft: an IoT device has so much data which, in most cases, is unique to the individual user. The data may be credit card details, personal health information, etc.
- Physical harm: IoT devices are becoming more common in the medical space. Some of them include defibrillators and pacemakers. When these devices are interfered with, the medical care of a patient can be negatively affected.

A vulnerable IoT device can be infiltrated and used in a botnet. Unprotected devices are not hard to discover for perpetrators. The threats posed to IoT devices have become more sophisticated and this has led to a multitude of cyberattacks. There are billions of IoT devices and, therefore, their security should be highly prioritized. Device users should adhere to security practices such as blocking remote access (if it not necessary) and changing default passwords.

Device manufacturers and vendors should be more vigilant and invest in IoT management tools. They should take the following steps:

- Notify users about outdated software.
- Emphasize on smart password management.
- Disable unnecessary remote access.
- Make sure APIs have strict access control policy.
- Reinforce the security of C&C centers.

---

# Chapter 19: Domain Name Server (DNS) Hijacking

DNS hijacking (or DNS redirection) is a DNS attack where DNS queries are resolved incorrectly so that users can be unexpectedly redirected to malicious sites. For them to carry out the attack, the bad actor can install malware on the victim’s PC, hack/intercept DNS communication, or take over routers. Attackers use DNS hijacking for phishing or pharming. DNS hijacking is also used by many ISPs (Internet Service Providers) to take over the DNS requests of a user and gather statistics. DNS hijacking is also used by governments for censorship—users are redirected to government sites that are authorized.

There are four main forms of DNS redirection:

- **Local DNS hijack**: the perpetrator installs Trojan malware on the computer of the victim. He then tweaks the local DNS settings, so the victim is redirected to malicious sites.
- **Router DNS hijack**: most routers have firmware vulnerabilities or default passwords. When an attacker takes over a router, he can overwrite the DNS settings which affects all the users that are connected to the router.
- **Man in the middle DNS attacks**: a perpetrator intercepts communication between a DNS server and a user then gives another destination IP address that points to a malicious site.
- **Rogue DNS Server**: the perpetrator hacks a DNS server and tweaks DNS records. Consequently, DNS requests are redirected to malicious sites.

A DNS spoofing attack occurs when an attacker redirects traffic from a legitimate site to a malicious site. DNS spoofing can be carried out using DNS redirection. For instance, by compromising a DNS server, attackers can spoof legitimate websites then redirect the users to other malicious sites. Cache poisoning can also be used to execute DNS spoofing without the need to rely on DNS hijacking. A bad actor can put in an illegitimate DNS entry and poison the DNS cache. This entry contains an alternative IP destination. Until the cache is refreshed, the domain is resolved to the spoofed website.

Strong security measures are required for a DNS name server since it is a very sensitive infrastructure. Hackers can hijack it and use it to execute DDoS attacks.

- Resolvers on the network: shut down any DNS resolvers that are not needed. As for the legitimate resolvers, ensure that they are behind a firewall and inaccessible from outside.
- Access to name servers should be restricted: use network security measures, firewall, physical security, and multi-factor access.
- Take caution against cache poisoning: lower/upper case in domain names and query ID should be randomized and try to use a random port source.
- Take care of known vulnerabilities: attackers are always looking for susceptible DNS servers.
- Resolver should be separated from authoritative name server: the two should not be run on the same server.
- Ensure that zone transfers are restricted.

For end users, actions such as installing antivirus, changing router passwords, and use an encrypted VPN channel will protect them from DNS hijacking.

## Mitigation for Site Owners

Steps to take:

- DNSSEC
- Client lock
- Secure access

---

# Chapter 20: Cross Site Request Forgery (CSRF) Attack

CSRF (otherwise known as Session Riding, Sea Surf or XSRF) is a kind of an attack that manipulates a web browser into carrying out an undesired action in the application that a user is logged on to. When a CSRF attack is successful, both the user and the business are affected. It can lead to unauthorized transfer of funds, data theft (including session cookies), changed passwords, or damaged relationships with clients. CSRFs are usually executed using social engineering attacks such as links or emails that manipulate the user into sending a counterfeit request to the server. The application authenticates the unsuspecting user during the attack—this makes it difficult to tell the difference between a forged request and a legitimate one.

## Example of a CSRF Attack

A perpetrator takes some time to study an application so that the request can look just like a legitimate one. Take the example of a `GET` request for say, a $200 bank transfer. It will typically look like this:

```
GET http://netbank.com/transfer.do?acct=PersonB&amount=$200 HTTP/1.1
```

A perpetrator may tweak this script and transfer $200 to his account. The malicious request may be something like this:

```
GET http://netbank.com/transfer.do?acct=AttackerA&amount=$200 HTTP/1.1
```

The attacker may then embed this request into a link that seems very innocent:

```html
<a href="http://netbank.com/transfer.do?acct=AttackerA&amount=$200">Read more!</a>
```

The next step for the bad actor is to send out this link to as many bank customers as possible via email. Anyone who clicks through while signed into their bank account may end up unintentionally transferring $200 to the hacker. A malicious request carried out using the `<a>` href tag cannot be successful if the bank only uses `POST` requests. Nonetheless, the attacker can still use a `<form>` tag together with automatic execution of an embedded JavaScript.

For example:

```html
<body onload="document.forms[0].submit()">
<form action="http://netbank.com/transfer.do" method="POST">
<input type="hidden" name="acct" value="AttackerA"/>
<input type="hidden" name="amount" value="$100"/>
<input type="submit" value="View my pictures!"/>
</form>
</body>
```
