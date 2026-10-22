compliance. Data protection laws have been enacted in many countries that require data subjects to give their agreement to their information being processed and for defined purposes; therefore, monitoring of communications may need to be included in customer contracts and other data protection declarations.

Despite all of these hurdles, for most countries, it is possible to roll out a DLP system. As part of the project planning stage, the organization needs to commission a legal investigation for each country to understand whether it is lawful to actively monitor corporate email, but more importantly, the preconditions for any monitoring to lawfully take place. For countries that forbid email monitoring or any form of workplace surveillance, it is usually possible to implement blocking controls on writing to removable storage along with uploads to external Websites, provided no log files are kept.

# 13.3.2.5 Remote Access Solution.

A commonly implemented remote access solution is the provision of Webmail from home computers. With Webmail you need to configure the system to prevent staff opening attachments within local applications on the home computer. If this is not blocked, staff can copy corporate information by saving the open attachment to their local hard drive. In addition, any use of the Remote Desktop Protocol (RDP) also needs to be properly configured to prevent local USB resources being mapped to the remote computer.

# 13.3.3 Internal Honeypots.

Honeypots are attractive systems or nodes that appear to have valuable confidential data. Roger Grimes, author of a textbook about honeypots,²² writes:

> One of the best things you can do to get early warning of internal attackers is to implement honeypots.... because they’re low cost and low noise—and they work!

Because the internal attackers you seek could be trusted IT employees, the entire project must be kept secret. It should be known only to the sponsor, management, and the implementers. Often, we give the project a boring code name like Marketing Business Development, which is used in all documents and e-mails, avoiding terms having anything to do with honeypots. Don’t even tell the network security people about it, in so far as you can and still have an operational project. Then take a few computers that are destined for de-provisioning or the scrap heap and turn them into your honeypots.²³

The point of such a honeypot is that there should be zero access to it: It serves no function and there is never a reference to it in any internal or external documentation. Thus, anyone who accesses it is either doing so by pure accident or is violating policies governing unauthorized access to internal data (there is no one authorized to access the honeypot). Detailed logging should be in place at all times to provide forensic information immediately; however, administrators should ensure that they can actually visualize exactly what is being done in real time, not simply rely on the detailed log files for after-the-fact analysis. An early-warning system should immediately alert system administrators to the problem (preferably as the access is in progress) via screen messages, voice messages, and text messages.

# 13.4 CONCLUDING REMARKS.

Fighting the insider threat need not be solely reactive. In addition to the entire spectrum of information assurance measures covered throughout this Handbook, maintaining an environment of security awareness and of encouragement, trust, fair-dealing, and long-term commitment to the welfare of employees must remain among the very best approaches to reducing the risk of insider crime.