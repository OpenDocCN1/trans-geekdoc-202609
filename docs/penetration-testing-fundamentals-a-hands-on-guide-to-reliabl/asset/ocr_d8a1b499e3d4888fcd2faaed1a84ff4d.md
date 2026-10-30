# Industrial Viruses

Industrial viruses target systems such as supervisory control and data acquisition (SCADA) systems, which are used in manufacturing, water purification, power plants, and other industrial systems. NIST 800-82 is a good place to start studying SCADA security. Special Publication 800-82, Revision 2, “Guide to Industrial Control System (ICS) Security,” is specific to industrial control systems. Industrial systems include SCADA systems and PLCs (primary logic controllers). This document begins by examining the threats to these systems, in detail. The standard then discusses how to develop a comprehensive security plan for such systems.

In 2010, the Stuxnet virus was discovered. It was designed to attack programmable logic controllers, particularly those in systems used by Iran to refine uranium. It was widely speculated that the U.S. government and/or Israel were behind the attack.

# Hardware Trojans

Hardware Trojans are alterations to firmware in an integrated circuit. Given the widespread outsourcing of chip manufacturing, such Trojans could be in any integrated circuit. Instances of such Trojans found in the wild have, thus far, been rare. But that merely means they have not been detected. And that is logical, as it is both harder to create a hardware Trojan and harder to detect it. Since it is in a chip, traditional anti-malware approaches will not work.

Detecting hardware Trojans is quite difficult. There exist established methodologies for testing individual chips. For example, destructive measures such as reverse engineering the chip can be used to detect Trojans; however, these methods are very expensive and require sophisticated equipment such as electron microscopes. The more common methodologies involve comparing timing delays and power fluctuations; however, such methods depend on a “golden chip” reference to compare the test chip to. It is not always possible to have a verified chip to test.

As already stated, while hardware Trojans are quite rare and some sources claim there have been none found “in the wild,” this is not completely accurate. Some have been found, but confirmation of the finding is difficult. The systems infected tend to be confidential systems, and limited information is available.

From a penetration testing or security auditing perspective, hardware Trojans are a separate issue and should be given their own audit. Most penetration testers do not have the skill set to perform tests for hardware Trojans, and most networks don’t need testing for hardware Trojans. Therefore, these should be excluded from the scope.

# Virus Examples

The threat from virus attacks cannot be overstated. While there are many web pages that give virus information, in my opinion there are only a handful of web pages that consistently give the latest, most reliable, most detailed information on virus outbreaks. Any security professional will want to consult