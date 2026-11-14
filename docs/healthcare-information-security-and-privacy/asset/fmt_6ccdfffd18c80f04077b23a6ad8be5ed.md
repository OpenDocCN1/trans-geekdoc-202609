
## References

9. Executive Order 13636, “Improving Critical Infrastructure Cybersecurity.” *Federal Register* 78, no. 33. (February 19, 2013). Accessed October 24, 2014, at <http://www.whitehouse.gov/the-press-office/2013/02/12/executive-order-improving-critical-infrastructure-cybersecurity>

10. National Initiative for Cybersecurity Education (NICE). “DRAFT National Cybersecurity Workforce Framework.” Accessed October 24, 2014, at <http://niccs.us-cert.gov/sites/default/files/documents/files/DraftNationalCybersecurityWorkforceFrameworkV2.xlsx>

11. Big Brother Watch. “NHS Breaches of Data Protection Law: How Patient Confidentiality Was Compromised Five Times Every Week.” October, 2011. p. 2. Accessed October 24, 2014, at <http://www.bigbrotherwatch.org.uk/files/NHS_Breaches_Data_Protection.pdf>

12. Sparkes, Matthew. “Poorly Trained IT Workers Are ‘Gateway for Hackers’.” *The Telegraph*. August 6, 2014. Accessed September 28, 2014, at <http://www.telegraph.co.uk/technology/internet-security/11011249/Poorly-trained-IT-workers-are-gateway-for-hackers.html>

13. The National Health Information Sharing & Analysis Center (NH-ISAC). “Membership Services.” Accessed September 20, 2014, at <http://www.nhisac.org/membershipservices>

14. National Institute of Standards and Technology. “An Introductory Resource Guide for Implementing the Health Insurance Portability and Accountability Act (HIPAA) Security Rule.” By Matthew Scholl, Kevin Stine, Joan Hash, Pauline Bowen, Arnold Johnson, Carla Dancy Smith, and Daniel I. Steinberg. Special Publication 800-66, Revision 1. Section 4.3, p. 21. October, 2008. Accessed September 24, 2014, at <http://csrc.nist.gov/publications/nistpubs/800-66-Rev1/SP-800-66-Revision1.pdf>

---

# Chapter 11: Administering Risk Management and Cybersecurity

**Rob Davis**

In this chapter, you will learn to:

- Understand the anatomy of an external cybersecurity attack using an organized approach
- Appreciate the cyber operations application of risk management frameworks
- Comprehend what a detection capability can provide for risk mitigation
- Understand incident response and recovery for the entire organization
- Apply tailored risk assessment consideration and balance to compensating controls in healthcare

---

Healthcare has seen a tremendous explosion of technology become integrated into the everyday care of patients. Traditional computing of desktops, laptops, and servers centrally managed by the information technology (IT) department is rapidly evaporating. Smartphones, medical devices, and so on, are blurring the lines of computing and communications capabilities, spreading information from countless sources all over the network. The result is that professionals outside of traditional IT are involved in security at all levels. Most healthcare organizations are delivering care 24 hours a day, which means that the network is humming all the time. Personal health information (PHI) is also being stored, accessed, and transmitted continuously. So we have the ingredients of a critical mission, many different perspectives, a large network footprint, and personal information coming from everywhere to make a recipe for the perfect storm for cybersecurity.

In this chapter, we tackle this difficult challenge in a practical manner given the resources and tools available. The anatomy of a cyberattack will be laid out to better understand the problem. For many healthcare privacy and security professionals, this may be their first up-close look at cybersecurity attacks in action. Finally, a practitioner’s view of applying risk management frameworks for protecting a network will be provided.

### The Attack

In cybersecurity we tend to focus on ourselves because the attackers seem almost like mythical creatures that come to pillage and plunder while we are not looking. The immediate reaction is to fortify our defenses and stop this injustice. However, this is only one side of the equation, and we must give an equal amount of consideration to the adversary. The anatomy of a cyberattack is illustrated in [Figure 11-1](#ch11.html#ch11fig1) and referenced throughout the rest of the chapter.

![image](f0284-01.jpg)

**Figure 11-1** Overview of the anatomy of a cyberattack

#### The Anatomy of a Cyberattack

The procedure outlined in [Figure 11-1](#ch11.html#ch11fig1) is the result of incorporating several best-practice framework descriptions of cyber events, such as Lockheed Martin’s “Cyber Kill Chain,” a term that is actually borrowed from commonly used jargon in the United States Air Force when it references a mission such as an air strike that will be launched from far away.^([1](#ch11.html#ch11en1)) In cybersecurity, the term has long been applied to the surface area of attack by external threats. The way the Air Force describes the kill chain process is similar to how cyberattacks happen, as most of the adversaries against healthcare networks originate in other networks that are far away. The term “kill chain” as a descriptor sounds cool and really gets attention, and the latter is probably the reason it is sometimes used. Another example to which the anatomy of a cyberattack is related is Carnegie Mellon University’s cyber situation awareness (cyberSA). CyberSA means having recognition of the computing environment and events over time, and what their impact is. Situation recognition consists of the following elements: the perception of the type of cyberattack, the source (who, what) of the attack, and the target of the attack; situation comprehension, which is the understanding of why and how the current situation occurred, and its impact; and situation projection, which involves determining the expectations of a future attack, its location, and its impact.^([2](#ch11.html#ch11en2)) Also included in the framework presented here are personal experiences by the author and others. In sum, the attack sequence outlined in this chapter is intended to include several industry best practices.

![image](note.jpg) **NOTE** This is a general, high-level depiction of how cyberattacks take place. Please refer to other kill chain or cyberattack models, as desired, for a full introduction to the processes.

A general misconception exists about the duration and steps needed to successfully execute an attack, because details of attacks get glossed over in our current 140-character media and 24-hour news cycle. To keep stories simple, too much focus is placed on the end of the attack. Usually, many steps precede the headline-grabbing action.

#### External Delivery

If absolute protection from all the malicious actions on the World Wide Web is the goal, then simply disconnect from the Internet, but we all know that is impossible in today’s ever-connected world. We all rely on e-mail, third-party providers, bank transfers, and so on, to get business done every day, and it is almost inevitable that some level of malware will get into a network from this connectivity to the outside world.
