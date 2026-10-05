# Hacking Multifactor Authentication

# Migration and Deprovisioning

As with any MFA solution, inventories, policies, and processes need to be developed for lost, stolen, or replacement MFA devices. Any username changes due to marriage, divorce, or legal name changes can be handled outside the MFA device and application. The MFA device should stay linked to the person's voter ID. If a new device is provisioned, the old one is always deprovisioned first and disabled from being used (at least by that user). Users and anyone else should be able to easily initiate a device “hard reset” to wipe the device.

# API

Any APIs used by the voting system should be locked by IP address and require special trusted digital certificates for initial authentication. The API should not be “open” and available to use anyone. API connections should happen over private phone lines or data connections and not over the Internet.

# Operational Training

All users, tech support, and trainers need to be trained on device use and troubleshooting. Users should be provided with a written booklet, which shows them what to do, step-by-step, in pictures and text. No matter how easy you think to use any MFA device, there will be a large percentage of people missing up. Remember earlier in this chapter when I discussed how a large percentage of people could not be trained to use a device whose only instruction was to plug it into the USB port and push a button. Our MFA vote-protecting device is orders of magnitude harder. Bloomberg’s B-Unit is used by “masses” and is more difficult to use, but the average B-Unit user is college-educated or at least of average intelligence.

An MFA device for remote voting going out people who never graduated from high school, who have never driven cars, or who have a driver’s license. They may have little to no experience on a computer, much less MFA devices. Any public-wide MFA rollout is going to take a lot of training and support. I suggest that in the real world, when you’re planning your MFA training, consult experts whose job it is to help you design user-friendly and easy-to-understand documentation. It’s harder than most people think.

# Security Awareness Training

Every MFA solution needs to come with its security awareness training campaign. Users must be taught about potential threats and attackers and the ways they might abuse the MFA solution. Online remote voting is no different. Users should be warned about attackers sending their fraudulent emails trying to infect their host machines or encouraging them to enable and use their MFA device against their bogus website. Hackers will always find ways to hack MFA solutions, and users need to be taught what those methods are, what to look out, and how to defend against them.