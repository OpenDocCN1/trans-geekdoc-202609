XOR is the basic binary math operation, exclusive or. Some viruses will XOR their binary file with some random number. That renders the virus temporarily unusable, but also makes it no longer match known virus signatures. When ready to unleash the virus, it is simply XORs again and the original is returned. Obviously, this requires a secondary module that performs the XOR operation. However, since that is all that module will be tasked with, it is unlikely that it will trigger antivirus software.

Related to the XOR are cryptor viruses that use a secondary module to encrypt the virus, then decrypt it when ready for use.

The Trojan horse is an excellent way to hide a virus. By tying it to a legitimate program, it not only will trick the user into installing it, but it may also evade antivirus software.

A polymorphic virus literally changes its form from time to time to avoid detection by antivirus software. A more advanced form of this is called the metamorphic virus; it can completely change itself. This also requires a secondary module to perform the rewriting.

A sparse infector virus attempts to elude detection by performing its malicious activities only sporadically. With a sparse infector virus, the user will see symptoms for a short period, then no symptoms for a time. In some cases the sparse infector targets a specific program but the virus only executes every 10th time or 20th time that target program executes. Or a sparse infector may have a burst of activity and then lie dormant for a period of time. There are a number of variations on the theme, but the basic principle is the same: to reduce the frequency of attack and thus reduce the chances for detection.

Fragmented payload is a rather sophisticated method of hiding a virus. The virus is split into modules. The loader module is rather innocuous and unlikely to trigger any antivirus software. It will then download, separately, the other fragments. When all fragments are present, the loader will assemble them and unleash the virus.

# Ransomware

It is impossible in modern times to discuss malware and not discuss ransomware. In fact, as I am writing this, in the past 48 hours the world has been hit with a massive ransomware attack. It began by attacking healthcare systems in England and Scotland, and spread far beyond those. While many people first began discussing ransomware with the advent of CryptoLocker in 2013, ransomware has been around a lot longer than that. The first known ransomware was the 1989 PC Cyborg Trojan, which only encrypted filenames with a weak symmetric cipher.

In general, ransomware works as a worm, then either disables system services or encrypts user files. It then demands a ransom to release those files/service. The term worm used to have a different meaning than virus, though the terms are often used interchangeably today. A worm is essentially a virus that propagates much more readily.

There are two general categories of ransomware, as shown in Figure 5-3.