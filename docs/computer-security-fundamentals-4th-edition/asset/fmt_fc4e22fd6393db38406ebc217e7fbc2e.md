
The next phase of assessing a system’s security is to ensure that all reasonable protective software and devices are employed. This means, at a minimum, having a firewall between your network and the outside world (refer to [Chapter 2](#ch02.xhtml#ch02)). You should also consider using an intrusion detection system (IDS) on that firewall and any web servers. (We discussed Snort IDS in [Chapter 9](#ch09.xhtml#ch09)). Some security experts consider IDSs to be nonessential; you can certainly have a secure network without one. However, using an IDS is the only way to know of impending attacks, and there are free, open-source IDSs available, and I highly recommend using them. A firewall and an IDS will provide basic security to your network’s perimeter, but you also need virus scanning. Each and every machine, including servers, must have a virus scanner that is updated regularly. The point has already been made that a virus infection is the greatest threat to most networks. As also previously discussed, it is probably prudent to consider installing antispyware software on all of your systems to prevent users of your network from inadvertently running spyware on the network.

In Practice

Finding a Firewall

When selecting a firewall to use, you have a number of options: You can purchase a very inexpensive router-based firewall for your high-speed Internet connection, you can get a router that is separate from your DSL or cable router, or you can get a cable or DSL router that includes a firewall. The following websites can help you find more information on these options and determine which one would best suit your needs:

*   **Linksys:** [`http://www.linksys.com/us/`](http://www.linksys.com/us/) (Note: Linksys was purchased by Cisco.)

*   **Home PC Firewall Guide:** [`www.firewallguide.com`](http://www.firewallguide.com)

*   **Broadband Guide:** [`www.firewallguide.com/broadband.htm`](http://www.firewallguide.com/broadband.htm)

In addition to the information on the firewall options available, you can find many free or very inexpensive firewall packages on the Internet. Following is a list of two popular firewalls available via the Internet:

*   **Norton Personal Firewall:** This product is inexpensive and is available for multiple operating systems. A free trial download is available from [`www.symantec.com`](http://www.symantec.com).

*   **McAfee Personal Firewall:** This product is similar in price and basic function to Norton Personal Firewall. You can find out more about this product at [`http://us.mcafee.com`](http://us.mcafee.com).

For medium-sized or larger networks that have more flexible budgets, Citrix offers an application gateway specifically tailored for web servers. This solution is relatively inexpensive and can be ideal for companies whose primary function is to provide websites or web services. Information is available at [`https://www.citrix.com/products/netscaler-application-delivery-controller/tech-info.html`](https://www.citrix.com/products/netscaler-application-delivery-controller/tech-info.html)

Finally, Linux has a built-in firewall called iptables. It is an excellent solution for any system using Linux. The first firewall widely available for Linux was called ipchains. This product worked but had limitations. It was first introduced in version 2.2 of the Linux kernel and superseded ipfwadm. The iptables service, which is now the primary firewall for Linux, was first introduced in Linux kernel 2.4. On most Linux systems, iptables is installed as `/usr/sbin/iptables`; however, if it was not included in the installation, you can add it later.

#### Policies

While policies are discussed in detail in [Chapter 10](#ch10.xhtml#ch10), “[Security Policies](#ch10.xhtml#ch10),” we briefly review some aspects of policies here. It is absolutely essential that any organization have clearly written policies on computer security—and that those policies be strongly enforced by management. Those policies should cover acceptable use of organizational computers, the Internet, email, and any other aspect of the system. Policies should prohibit the installation of any software on the systems. Only IT personnel should install software—and only after they have verified its safety.

Policies should also advise users against opening unknown/unexpected attachments. I recommend that people within an organization or department use a code word. If that code word does not appear in the body of an email (or in the subject line), then they do not open the attachment. Most virus attacks spread via email attachments. The subject line and body of such email messages are generated automatically by the virus itself. All of your legitimate attachments can have a code word in the subject line; it is highly unlikely that this word would be in the subject line of an email sent by a virus. This alone could prevent your users from inadvertently opening a virus.

Policies should also clearly delineate who has access to what data, how backups are performed, and what to do to recover data in the case of a disaster (commonly called a *disaster recovery plan*). Data access must be limited to only those personnel with an actual need to access the data. For example, not everyone in the human resources department needs access to disciplinary files on all employees. Does your organization have a plan for what to do if a fire destroys your servers and all their data? Where do you get new machines? Who gets them? Is there an offsite copy of the data backup? Such questions must be addressed in a disaster recovery plan.

There should be a policy regarding passwords: acceptable minimum length, lifetime of a password, password history, and passwords to be avoided, such as any word that has a direct connection to the user. For example, a user who is a big fan of the Dallas Cowboys should not use a password that has any relationship to that sports team. Also, passwords that relate to personal data, such as spouse’s birthday, children’s names, or pet names, are poor choices. A password policy could also include recommendations or restrictions on a password.

FYI: Good Passwords

Many sources claim that a good password is at least 8 (preferably 15) characters long; contains letters, numbers, and characters; and combines upper- and lowercase letters. After learning about rainbow tables earlier in this book, you are probably aware that an even longer password might be needed. I usually recommend a passphrase. Start with something easy like “cheese burgers from Burger King.” Now put it all together in one word, use some capitalization, and change some letters to numbers, and you might end up with a password like this: `!l!k3ch33s3burg3rsfrombuRG3rk1ng`. You can memorize such a password with surprising ease, and it is very difficult to guess or even to crack with a rainbow table.
