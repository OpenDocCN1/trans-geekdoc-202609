
# Security Measures against Cloning

When considering one tag and one reader as a system, which has been done in the previous sections, the risk of cloning (duplication of the tag ID in a new tag) has been identified. Only in the broad view of the complete architecture, such a risk could be handled: in the database where all the different tag IDs (with respect to a specific application) are collected, a duplicate ID could be detected and in some cases even the clone could be recognized (i.e., be distinguished from the original tag).

# Conclusion

This document presented an overview of some of the technical facets of RFID. The most striking lesson here is that even though RFID is a conceptually simple technology, it engenders technological questions and problems of formidable complexity. For this reason, it is unwise to view RFID privacy and security as a technological issue alone. Policymaking will also have a vital role to play in the realm of RFID. They must not only supplement the protections that technology affords, but must prove sensitive to its novelties and nuances. To be most effective, RFID security controls should be incorporated throughout the entire life cycle of RFID systems’from policy development and design to operations and retirement. A delicate balance between privacy and utility is needed to bring RFID to its high pitch of promise.

# Chapter 4

# Privileged User Management

# Georges J. Jahchan

# Introduction

On June 22, 2008, Terry Childs made national headlines when he locked access to the city of San Francisco’s Fiber Wide Area Network (WAN) by resetting administrative passwords to its switches and routers and then declining to hand over those passwords.[^(\*)](#9781466508507_epub_c04_r1.htm#ch4-ftn1)

On October 24, 2008, an employee at Fanny Mae’s Urbana, MD, data center was let go from his contract, almost two weeks after erroneously creating a computer script that changed the settings on the Unix servers without the proper authority of his supervisor.[^†](#9781466508507_epub_c04_r1.htm#ch4-ftn2) Within 90 minutes of being told his contract was terminated, and several hours before his access to the Fannie Mae network was disabled later that evening, he embedded a malicious script inside a legitimate script that ran on Fannie Mae’s network every morning. The malicious script was to trigger on January 31, but was discovered by chance by another engineer on October 29. The malicious script was planted after a page of blank lines intended to conceal it. Had that script run, it would have disabled monitoring alerts and all log-ins, deleted the root passwords to the approximately 4000 Fannie Mae servers, then erased all data and backup data on those servers by overwriting with zeros. It would have caused millions of dollars in damage and reduced or shut down operations for at least a week.

March 17, 2009: An IT contract employee was indicted on charges of sabotaging a computer system he helped set up, because the company did not offer him a permanent job.[^‡](#9781466508507_epub_c04_r1.htm#ch4-ftn3) He was charged with affecting the integrity and availability of an offshore platform monitoring computer system designed to detect oil leaks. While working as a contract employee, he had set up multiple accounts that he used to illegally gain access to the system after he stopped working for the company.

In the three cases, had appropriate privileged user controls been implemented, the incidents could have been prevented, or at least detected in a timely manner so as to minimize damage. In the second and third case, dame luck averted disaster, but organizations should not count on their lucky star to safeguard their information assets.

With the job cuts and corporate belt tightening, resulting from the faltering economy, companies are advised to be especially vigilant with disgruntled employees.[^(\*)](#9781466508507_epub_c04_r1.htm#ch4-ftn4)

A disgruntled administrator is not the only threat to an organization. Outsiders who manage to steal legitimate privileged users’ credentials and then use them to gain access to high-value targets pose an even greater threat. Hackers who band together in across-the-globe virtual communities and share knowledge are the most dangerous as they combine their diverse skills to mount innovative and highly sophisticated targeted attacks. They will typically carefully plan their attacks and break into a system outside working hours, when they are most likely to go unnoticed, plant a back door that subsequently grants them root access, and leave as quickly as possible, erasing their tracks.

Computer Emergency Response Team (CERT’s) published analysis of 150 insider attack incidents[^†](#9781466508507_epub_c04_r1.htm#ch4-ftn5) classified the attacks into three categories: fraud, theft of information, and IT sabotage, and identified the typical perpetrators’ profiles. Following is a summary table of the results.

![](OEBPS/images/table_38.1.jpg)

![](OEBPS/images/table_39.1.jpg)

CERT recommends that management must recognize the technical precursors and have the “ability to disable access on demand in the absolute, particularly for administrators and privileged users” when demoting or firing. In practice, that requires an understanding of the access paths available to insiders, which “depends on rigorous access management practices.” Access management must be proactive and ongoing, as “practices tend to degrade over time without regular enforcement” and “it takes time to recover from poor access management practices.”

Effective privileged user controls need to combine policies, procedures, and technologies that address the particular environment and needs of organizations. Though there may be similarities, no two organizations’ environments are alike. Consequently, what works very well for one organization may not for another in the same line of business. In security, there is no such thing as “one solution fits all.” While the administrative and operational controls are particular to a company, the technology controls are licensed for a variety of tools available from specialty security vendors.

At a high level, organizations use technology solutions to come as close as possible to the goal of consistently granting and controlling rights based on the principle of least privilege (or access on a need-to-know and/or need-to-do basis). Furthermore, auditors come to expect organizations to prove it. Regulations further complicate matters with regulation-specific control/audit/reporting requirements.

The technical controls to manage privileged users fall in three main categories: privileged password management, privileged user access controls, and identity and access management suites. Some vendors have products that fall into more than one category, others are platform specific (Windows-only or \*nix-only), while others are cross-platform. This paper explores some of the products that help automate and enforce rigorous privileged account management practices. The content of this article is based on published information from vendors and independent sources. The information is reported “as is”; no attempt was made to validate vendor claims, as product evaluations are beyond the scope of this article.

Full management of privileged accounts requires organizations to not only control who has access to privileged credentials, but also, once access is granted, restrict use exclusively to perform specific tasks, and maintain an audit trail of user actions. As we will see, none of the solutions reviewed meet all of the goals.

The solutions are categorized, but they are not sorted in any particular order.

# Privileged User Audit Solutions

# Centrify DirectAudit
