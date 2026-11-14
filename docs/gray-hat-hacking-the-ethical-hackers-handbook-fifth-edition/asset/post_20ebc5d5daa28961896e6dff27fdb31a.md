
trigger system stored in KeePass.config.xml and does not need malware to be abused.

Once credentials are gained, using a low-tech or human approach can also yield fruitful results for the red team. Simply looking through a company’s file shares can reveal a ton of information due to an overly permissive setting and a lack of data encryption. Although some red teams will be capable of creating their own sophisticated tools, the reality is that in a lot of cases the investment needed to make custom tools is not worth the reward. In fact, blending into the environment by using tools that will not set off red flags is called “living off the land.”10 Living off the land could include using wmic.exe, msbuild.exe, net.exe, nltest.exe, and the ever-useful Sysinternals and PowerShell.

Also consider targeting user groups that are likely to have local admin permissions on their desktops. An organization’s developers are often treated like VIPs and have fewer security controls on their systems. Same goes for an organization’s IT team. Many IT personnel still use their domain admin account for day-to-day use and don’t understand that it should be used sparingly. Also consider targeting groups that are likely to bypass user security awareness training. An organization’s executive leadership is frequently an attacker’s target, and ironically these people are the first to request an exemption from security training.

Privilege escalation methods used to focus on escalating privileges to local admin.

However, organizations are getting wise to this risk of allowing everyone to be a local administrator. Tools like PowerUp—a self-contained PowerShell tool that automates the exploitation of a number of common privilege escalation misconfigurations—is perfect for escalating privileges. Many privilege escalation options are available, including manually manipulating a service to modify binPath to trigger a malicious command, taking advantage of misconfigured permissions on the binary associated with a service, %PATH% hijacking, and taking advantage of DLL load order, to name a few.

Search for unprotected virtual machine backups. It’s amazing what you can find on a regular file server. Using default credentials is still a tried-and-true approach to gaining access in many organizations.

When exfiltrating data from an environment, first of all, be sure it is sanctioned via the assessment’s rules of engagement. Then find creative ways to remove the data from the environment. Some red team assessors have masqueraded their data as offsite backup data, for example.

## Lessons Learned

Postmortem exercises performed as a part of a red team engagement are often detailed and have a strong emphasis on knowledge transfer. Red team assessments need to have a heavy focus on “documenting as you go,” in order to capture all the information that will allow an organization to perform a detailed analysis of what is working and what needs to be redesigned. This postassessment analysis is often called an _after action report_ (AAR).

An AAR should include lessons learned from different perspectives. It’s also important to document what went right. A detailed understanding of which tools and processes were effective can help an organization mimic that success in future endeavors. Including different perspectives also means capturing information from different teams and sources. “Lessons” can come from unlikely sources, and the more input that goes into the AAR, the less likely an important observation will be lost.

The AAR should be used by the organization’s leadership to inform strategic plans and create remediation plans for specific control gaps that need to be addressed.

## Summary

Red team exercises are stealthy ethical hacking exercises that are unannounced to the blue team. They allow the blue team to defend a target and an organization to gauge how its controls and response processes perform in an emulation situation that closely mimics a real-world attack. Red team exercises limit communication and interaction between the red and blue teams. They are most beneficial to organizations that have mature security programs, those that have invested a significant amount of effort in establishing and testing their security controls. Organizations that are still in the process of building a security program and refining their security controls and processes may benefit more from the collaboration and communication inherent to purple team exercises, covered in the next chapter. Purple team exercises are ideal for getting an organization to the point where it is ready for the stealthy nature of a red team exercise.

## References

- 1. Carl von Clausewitz, On War, 1832. For more information, see https://en.wikipedia.org/wiki/On_War.
- 2. Department of Defense Directive (DoDD) 8570.1, August 15, 2004, https://static1.squarespace.com/static/5606c039e4b0392b97642a02/t/57375967ab48...
- 3. US Military Joint Publication 1-16: “Department of Defense Dictionary of Military and Associated Terms,” Joint Publication 1-02, January 31, 2011, www.people.mil/Portals/56/Documents/rtm/jp1_02.pdf; “Multinational Operations,” Joint Publication 3-16, July 16, 2013, www.jcs.mil/Portals/36/Documents/Doctrine/pubs/jp3_16.pdf.
- 4. Jason Kick, “Cyber Exercise Playbook,” The Mitre Corporation, November 2014, https://www.mitre.org/sites/default/files/publications/pr_14-3929-cyber-exercise-playbook.pdf.
- 5. Justin Warner, Common Ground blog, https://www.sixdub.net/?p=705.
- 6. “Threat Risk Modeling,” OWASP, https://www.owasp.org/index.php/Threat_Risk_Modeling.
- 7. Adversarial Tactics, Techniques & Common Knowledge, ATT&CK, Mitre, https://attack.mitre.org/wiki/Main_Page.
- 8. Category:Attack, OWASP, https://www.owasp.org/index.php/Category:Attack.
- 9. Raphael Mudge, “Infrastructure for Ongoing Red Team Operations,” Cobalt Strike, September 9, 2014, https://blog.cobaltstrike.com/2014/09/09/infrastructure-for-ongoing-red-team-operations/.
- 10. Christopher Campbell and Matthew Graeber, “Living Off the Land: A Minimalist Guide to Windows Post-Exploitation,” DerbyCon 2013, www.irongeek.com/i.php?page=videos/derbycon3/1209-living-off-the-land-a-minimalist-s-guide-to-windows-post-exploitation-christopher-campbell-matthew-graeber.

## CHAPTER 8

## Purple Teaming

> If you know the enemy and know yourself, you need not fear the result of a hundred battles. If you know yourself but not the enemy, for every victory gained you will also suffer a defeat. If you know neither the enemy nor yourself, you will succumb in every battle.
>
> Sun Tzu, _The Art of War_<sup>1</sup>

Purple teaming may be the absolute most valuable thing an organization can do to mature its security posture. It allows the defensive security team, your blue team, and your offensive security team, your red team, to collaborate and work together. This attack and defense collaboration creates a powerful cycle of continuous improvement. Purple teaming is like sparring with a partner instead of shadowboxing. The refinement of the skills and processes used during purple teaming can only be rivaled by the experience gained during actual high-severity events. Purple teaming combines your red team and blue team’s efforts into a single story with the end goal of maturing an organization’s security posture.

In this chapter we discuss purple teaming from different perspectives. First, we cover the basics of purple teaming. Next, we discuss blue team operations. Then we will explore purple team operations in more detail. Finally, we discuss how the blue team can optimize its efforts during purple team exercises.

In this chapter, we discuss the following topics:

- Introduction to purple teaming
- Blue team operations
- Purple team operations
- Purple team optimization and automation

### Introduction to Purple Teaming

Collaboration is at the heart of purple teaming. The goal of purple teaming is to improve the skills and processes of both the red and blue teams by allowing them to work closely together during an exercise to respectively attack and defend a particular target. This is vastly different from red teaming, where communication between the red and blue teams is restricted and prohibited during most of the exercise and where the red team typically has little knowledge of the target. During a purple teaming exercise, the red team will attack a specific target, device, application, business or operational process, security control, and so on, and will work with the blue team to understand and help refine security controls until the attack can be detected and prevented, or perhaps just detected and resolved with efficacy. It’s vital that you read Chapter 7 before reading this chapter because this chapter builds on Chapter 7’s content.

I’ve seen some confuse the concept of purple teaming with the role of a white cell or white team. As described in the previous chapter, the white team facilitates
