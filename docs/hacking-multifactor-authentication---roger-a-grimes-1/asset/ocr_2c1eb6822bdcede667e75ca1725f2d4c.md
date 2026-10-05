# Chapter 22 Designing a Secure Solution

air-gapped from any network, stored in physically secure areas, and protected from EMI, optical, and other types of eavesdropping and manipulation. It should take two or more people to access and sign code, and documented, any entry to the code-signing area must be monitored, videorecorded. These later processes are fairly common at high-value public key infrastructure installations and are part of what is called the key-signing ceremony. These processes are not new; everything described is routine and normal. You can look up the steps and procedures for key-signing ceremonies on the web.

NOTE I cover one of the pitfalls of highly secure key-signing ceremonies here: www.linkedin.com/my-key-signing-ceremony-gone-wrong-roger-grimes.

Overall, the electronic remote voting MFA should invite review and scrutiny and actively promote and reward responsible disclosure. The HackerOne bounty program covers what disclosure measures fairly well in their definition: www.hackerone.com/disclosure-guidelines.

# Physical Design and Defenses

Since I do not fully trust for high-security applications, our MFA solution will be a separate physical device. Because of the highly required feature set, it will look something like a Bloomberg B-Unit (i.e., a thick credit card). Like B-Units and smartcards, it should be built to withstand use and abuse, and should operate in reasonable temperatures. This device contains its own power source (for, which likely means a lithium-ion battery), have a useful life of at least 10 years, and be resistant to physical tampering. Any attempts to open the physical package should render the device permanently, logically broken. It should be designed to prevent EMI, electron microscope, and wireless side-channel eavesdropping.

Our solution should have the most popular physical connections, such as micro-USB, and provide several popular physical connection types. It can include one or more wireless methods, such as Wi-Fi, Bluetooth, and cellular. Any wired or wireless connection points should be hardened against attack and operate at the secure implementation of their standards. Any wireless method should require the user to physical press or move a switch that is clearly indicated for such a purpose; otherwise, the connection methods remain off.

All connection points need to be protected by physical attacks, such as "Bad BIOS" or evil USB cable attacks like the one discussed here: blog.knowbe4.com/new-evil-usb-cable-shows-how-attacks-like-physical-hardware. All communications, physical or wireless, must be encrypted and protected to prevent interception, modification, or eavesdropping. Any memory, chip, or storage areas should not be susceptible to cold-boot attacks.

The device should have an organic light-emitting diode (OLED) display area large enough to show codes and voter answers (e.g., candidates' names and Y No Votes to ballot questions) along with detail that the voter is assured their vote was registered.