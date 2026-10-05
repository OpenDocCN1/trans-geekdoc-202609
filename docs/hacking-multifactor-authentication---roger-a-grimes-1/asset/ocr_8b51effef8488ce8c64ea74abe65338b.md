# 248 Hacking Multifactor Authentication

![](bbox=[0.093, 0.107, 0.802, 0.532])

**Figure 11.2:** Example of UAC prompt screen

But as much as UAC was hated, in a year or two it had the same desired effect as sudo did in the Linux world: most users and programs were no longer running as full administrators. Over time Microsoft tweaked UAC to be more user friendly and less bothersome (although the behind-the-scenes complexity stayed). Today, users barely notice UAC other than they have to click OK to install a program or enter their password to change a system setting. UAC (and sudo) are success stories if you ignore the early warts and frustrations of the first few years.

I related this long narrative for two reasons. First, sometimes usability issues cannot be avoided and the vendors just have to take a risk that users will understand the new, constant interruptions over the long term.

NOTE Keep in mind that far too many security vendors think this is always the case for everyone they do, and in reality, forced instances of major changes should be used rarely. As covered in Chapter 4, “Usability as Security,” users will more often work around security blockers, turn them off, or use something else when faced with too high of a security obstacle—even when it is in the user’s own best self-interest.