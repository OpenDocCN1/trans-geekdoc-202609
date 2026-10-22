# 35.3.1.2 Loss of Confidentiality.

There are many ways an organization may suffer a loss of confidentiality from P2P technology. One common mistake is a misconfigured P2P application. The case study in Section 35.3.4 describes one situation. However, the dangers of a misconfigured P2P application are real—it is quite easy for data to be shared inadvertently. When users are in a hurry or do not understand what they are doing, a P2P application may allow for unauthorized access to information because its restrictions are too lax or missing altogether. A common mistake in a Microsoft Windows environment may be to share the entire “My Documents” folder when a user intended to share only photos. A misconfigured or maliciously altered P2P application may also become a conduit or access point for an attacker to enter an otherwise secure network environment.

Another, less well-known and often overlooked threat involves the amount of data a P2P application can reveal to unauthorized persons. For example, a P2P application may offer detailed information about its host, including:

+   - Operating system, version, and configuration
+   - Corporate network address scheme, host naming convention, DNS information
+   - Detail about the P2P application version or build (useful for attackers to exploit known vulnerabilities in a “buggy” release or version)
+   - Network routes, privileged access from a certain PC to sensitive networks within the organization (behind a firewall, etc.)
+   - Open network ports in the organization’s firewall

Although many of these examples may seem rather benign by themselves, the P2P application may be revealing information that an attacker can use as part of a bigger attack. Chapter 19 of this Handbook details how small pieces of information can be gathered and used together in an information security breach. The nature and functionality of P2P applications leaks sensitive information that otherwise would not be revealed.

All P2P applications are not created equal; a P2P application may be different from the user’s expectations. Can the P2P application actually be a reliable, malware-free, secure application—especially when the application is a free download from the Internet? It is possible that a backdoor exploit, malware, spyware, or the like may be built into the P2P application, or introduced later. This was especially true in the days of Napster; many applications included unwanted malware that ranged from innocent to downright dangerous.7 Similar exploits are still possible.

Many users still do not completely understand the application’s functionality. What may start out as a user trying to download a single movie can turn into an application that never gets uninstalled and is always running, uploading, or “seeding” that single movie for weeks or months on end. Since many of these applications are built to silently operate in the background, the user may think that the movie is downloaded, and the application isn’t used any longer, when in reality, it is still running until it is removed. This is not only a waste of resources, but a likely way to expose the organization to a DMCA (Digital Millennium Copyright Act) complaint from the organization that owns the intellectual property.

# 35.3.1.3 Consequences.

Any organization that does not protect against data loss via P2P networking is at great risk of public disclosure and scrutiny, financial