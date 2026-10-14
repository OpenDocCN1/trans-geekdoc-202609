
# Figure 11.13 OWASP ZAP results.

OWASP ZAP is a very easy-to-use tool. The basics can be mastered in a few minutes. And given that OWASP is the organization that tracks web application vulnerabilities, it is a very good source for testing the vulnerabilities of a website.

## Shodan

This tool is widely used by black hat hackers and security professionals alike. The website [https://www.shodan.io](https://www.shodan.io) is essentially a search engine for vulnerabilities. You need to sign up for a free account to use it, but then it can be invaluable to a pen tester trying to identify vulnerabilities. Of course, the site can also be invaluable to attackers. You can see the website in [Figure 11.14](#ch11.xhtml#ch11fig14).

![Figure 11.14 Shodan.io.](Images/11fig14.jpg)

# Figure 11.14 Shodan.io.

Shodan allows you to search using a number of options, including the following:

*   Search for default passwords, using search terms such as the following:

    *   default password country:US

    *   default password hostname:chuckeasttom.com

    *   default password city:Chicago

*   Find Apache servers, using search terms such as the following:

    *   apache city: “San Francisco”

*   Find webcams, using search terms such as the following:

    *   webcamxp city:Chicago

*   OLD IIS, using search terms such as the following:

    *   “iis/5.0”

With Shodan you can use a number of filters, including these:

*   **city:** Find devices in a specific city.

*   **country:** Find devices in a specific country.

*   **geo:** Specify coordinates (such as latitude and longitude).

*   **hostname:** Find values that match a specific hostname.

*   **net:** Search based on an IP address or an /x CIDR address.

*   **os:** Search based on operating system.

*   **port:** Find particular ports that are open.

*   **before/after:** Find results within a specified time frame.

For example, [Figure 11.15](#ch11.xhtml#ch11fig15) shows the results of a search for **default password city:Miami**.

![Figure 11.15 Shodan search results.](Images/11fig15.jpg)

# Figure 11.15 Shodan search results.

When you are performing a penetration test, it is a good idea to search Shodan for your company domain to find information that can guide your penetration testing efforts. Of course, would-be attackers can also use Shodan to find the same information. You can restrict your search to the hostname or domain name of a client who has hired you to conduct a penetration test. You can use Shodan to seek out default passwords, old web servers, unsecured web cameras, and other vulnerabilities in the target network.

The search shown in [Figure 11.15](#ch11.xhtml#ch11fig15) was conducted using the free version of Shodan. Recently, Shodan began offering a paid version that costs $49 and provides additional tools. There are also corporate memberships available at a higher price.

### Getting Professional Help

You may decide that you need outside help to set up and test your system’s security. This option is one that most security professionals would highly recommend if at all possible, particularly if you are new to security. It can be extremely helpful to get a professional consultant to assist you in setting up your initial security strategy and policies and perhaps do a periodic audit of your security. As mentioned in [Chapter 1](#ch01.xhtml#ch01), “[Introduction to Computer Security](#ch01.xhtml#ch01),” there are a number of people who claim to be hackers who are not. Frankly, there are also a number of self-proclaimed security experts who simply do not have the requisite skills. The question here is: How do you determine whether an individual is qualified? Following are some guidelines to consider in making this decision.

Experience is the most important factor when looking for a security professional. You want someone with a minimum of 5 years of IT experience, with 2 years related to security. Often, this will be a network administrator or programmer who has moved into security. Note that this is a minimum level of experience. More experience is always better. It is certainly possible that someone with less experience might have the requisite skill, but it is unlikely. Everyone needs a place to start, but you do not want your systems to be the place where someone is learning.

The quality of the person’s experience is as important as the length of experience. Ask details about the person’s experience. For example, exactly what role did she play in computer security? Did she simply set up policies, or did she actually do hands-on security work? What was the result? Was her system free from virus infections and hacker breaches or not? Can you contact her references? In short, simply because a person states that she was responsible for information security on her resume is not enough. You need to find out exactly what she did and what the results were.

Another important aspect of a security professional is education. Remember that computer security is a very broad subject. One needs an understanding of networks, protocols, programming, and more. It is entirely possible for a person with no formal education to have these skills, but it is less likely than if they had a formal education. Generally, these skills will most likely be found in a person with experience and a degree in a computer- or math-related field. That may sound somewhat intellectually snobbish, but it is a fact. There are many people in IT who are self-taught, such as people with history degrees who are network administrators or psychology majors who are now programmers. However, the more areas a person focuses in, the harder it is to obtain mastery. This is not to say that a person cannot be a security professional without a computer science, math, or engineering degree. The point is simply that this is one factor you should consider. If someone has an unrelated degree but meets or exceeds all other qualifications, you might still consider him. Some colleges are beginning to offer security-specific curriculum, and a few even offer security degrees. Clearly, specific training in computer security would be the most preferable security background.

Certifications have become very controversial in the IT profession. Some people swear by them. You can easily find many job advertisements that demand certain certifications, such as the CNE (Certified Novell Engineer) or MCITP (Microsoft Certified Information Technology Professional). Cisco certifications are also common (Cisco Certified Network Associate through Cisco Certified Internetworking Engineer). On the other hand, you would have no problem finding some IT professionals who denigrate certifications and consider them utterly worthless. That second position stems from the fact that there are some people who hold certifications who don’t have the skills one would expect. But that is true of any credential. There are medical doctors who are incompetent. But if you need medical help, your odds are much better if you consult someone who has a medical degree. Employers often take this approach to hiring. If they only interview those with certain degrees or certifications, then they have a higher chance of interviewing qualified candidates.
