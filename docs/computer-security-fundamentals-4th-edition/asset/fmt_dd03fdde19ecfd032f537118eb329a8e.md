
Use a virus scanner. McAfee and Norton (explored in the exercises at the end of this chapter) are the two most widely accepted and used virus scanners. However, Kaspersky and AVG are also good, reputable choices. Each costs about $30 per year to keep your virus scanner updated. Do it. Each antivirus product has proponents and detractors, and I won’t delve into the opinions on which is better. For most users, any of the four major antivirus programs would be effective. I rotate which one I use periodically just so I can stay familiar with all of them.

If you are not sure about an attachment, do not open it.

You might even exchange a code word with friends and colleagues. Tell them that if they wish to send you an attachment, they should put the code word in the title of the message. Without seeing the code word, you will not open any attachment.

Do not believe “security alerts” that are sent to you. Microsoft does not send out alerts in this manner. Check the Microsoft website regularly, as well as one of the antivirus websites previously mentioned.

These rules will not make your system 100% virus proof, but they will go a long way toward protecting your system.

### Trojan Horses

Recall from earlier chapters that `Trojan horse` is a term for a program that looks benign but actually has a malicious purpose. We have already seen viruses that are delivered via a Trojan horse. You might receive or download a program that appears to be a harmless business utility or game. More likely, the Trojan horse is just a script attached to a benign-looking email. When you run the program or open the attachment, it does something else other than or in addition to what you thought it would. It might do any of the following:

*   Download harmful software from a website.

*   Install a key logger or other spyware on your machine.

*   Delete files.

*   Open a backdoor for a hacker to use.

It is common to find combination virus/Trojan horse attacks. In those scenarios, the Trojan horse spreads like a virus. The MyDoom virus opened a port on your machine that a later virus, doomjuice, would exploit, thus making MyDoom a combination of a virus and a Trojan horse.

A Trojan horse can also be crafted especially for an individual. If a hacker wished to spy on a certain individual, such as the company accountant, he could craft a program specifically to attract that person’s attention. For example, if he knew the accountant was an avid golfer, he could write a program that computed handicap and listed best golf courses. He would post that program on a free web server. He would then email a number of people, including the accountant, telling them about the free software. The software, once installed, could check the name of the currently logged-on person. If the logged-on name matched the accountant’s name, the software could then go out, unknown to the user, and download a key logger or other monitoring application. If the software did not damage files or replicate itself, then it would probably go undetected for quite a long time. There have been a number of Trojan horses through the years. One of the earliest and most widely known was Back Orifice.

FYI: Virus or Worm?

As noted in [Chapter 4](#ch04.xhtml#ch04), there is disagreement among the experts about the distinction between a virus and a worm. Some experts would call MyDoom (as well as Sasser, which will be discussed later) a worm because it spread without human intervention. However, I would define a virus as any file that can self-replicate and a worm as any program that can propagate without human interference. This is also the most common definition you will find among security experts.

Such a program could be within the skill set of virtually any moderately competent programmer. This is one reason that many organizations have rules against downloading *any* software onto company machines. I am unaware of any actual incident of a Trojan horse being custom tailored in this fashion. However, it is important to remember that those creating virus attacks tend to be innovative people.

It is also important to note that creating a Trojan horse does not require programming skill. There are free tools on the Internet, such as `EliteWrapper`, that allow someone to combine two programs—one hidden and one not. So one could easily take a virus and combine it with, for example, a poker game. The end user would see only the poker game, but when it was run, it would launch the virus.

Another scenario to consider is one that would be quite devastating. Without divulging programming details, the basic premise will be outlined here to illustrate the grave dangers of Trojan horses. Imagine a small application that displays a series of unflattering pictures of Osama Bin Laden. This application would probably be popular with many people in the United States, particularly people in the military, intelligence community, or defense-related industries. Now assume that this application simply sits dormant on the machine for a period of time. It need not replicate like a virus because the computer user will probably send it to many of his associates. On a certain date and time, the software connects to any drive it can, including network drives, and begins deleting all files. If such a Trojan horse were released “in the wild,” within 30 days it would probably be shipped to thousands, perhaps millions, of people. Those thousands or millions of computers would then begin deleting files and folders. Imagine the devastation.

This scenario is mentioned precisely to frighten you a little. Computer users, including professionals who should know better, routinely download all sorts of things from the Internet, such as amusing flash videos and cute games. Every time an employee downloads something of this nature, there is a chance of downloading a Trojan horse. One need not be a statistician to realize that if employees continue that practice long enough, they will eventually download a Trojan horse onto a company machine. If they do, hopefully the virus will not be as vicious as the theoretical one just outlined here.

Because Trojan horses are usually installed by users themselves, the security countermeasure for this attack is to prevent downloads and installations by end users. From a law enforcement perspective, the investigation of a crime involving a Trojan horse would involve a forensic scan of the computer hard drive, looking for the Trojan horse itself.

There are a number of tools, some free for download, that will help a person create a Trojan horse. One that I use in my penetration testing classes is `eLiTeWrap`. It is easy to use. Essentially, it can bind any two programs together. Using a tool such as this one, anyone can bind a virus or spyware to an innocuous program such as a shareware poker game. This would lead to a large number of people downloading what they believe is a free game and unknowingly installing malware on their own system.

The `eLiTeWrap` tool is a command line tool, but it is very easy to use. Just follow these steps:

1.  Enter the file you want to run that is visible.

2.  Enter the operation:

    *   1—Pack only

    *   2—Pack and execute, visible, asynchronously

    *   3—Pack and execute, hidden, asynchronously

    *   4—Pack and execute, visible, synchronously

    *   5—Pack and execute, hidden, synchronously

    *   6—Execute only, visible, asynchronously

    *   7—Execute only, hidden, asynchronously

    *   8—Execute only, visible, synchronously

    *   9—Execute only, hidden, synchronously

3.  Enter the command line.

4.  Enter the second file (the item you are surreptitiously installing).

5.  Enter the operation.

6.  When done with files, press Enter.
