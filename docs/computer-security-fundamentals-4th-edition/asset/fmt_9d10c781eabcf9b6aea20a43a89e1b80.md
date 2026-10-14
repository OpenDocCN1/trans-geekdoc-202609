
This brings up the issue of virus variants and how they occur. In the case of a biological virus, mutations in the genetic code cause new virus strains to appear, and the pressures of natural selection allow some of these strains to evolve into entirely new species of viruses. Obviously, the biological method is not what occurs with a computer virus. With a computer virus, some intrepid programmer with malicious intent gets a copy of a virus (perhaps her own machine becomes infected) and then reverse-engineers it. Since many virus attacks are in the form of a script attached to an email, unlike with traditionally compiled programs, the source code of these attacks is readily readable and alterable. The programmer in question then simply takes the original virus code, introduces some change, and rereleases the variant. Frequently, the people who are caught for virus creation are actually the developers of the variants who lacked the skill of the original virus writer and therefore were easily caught.

##### The Mimail Virus

Mimail is another older virus that is still worth studying. The Mimail virus did not receive as much media attention as Sobig, but it had some intriguing characteristics. This virus collected email addresses not only from your address book but also from other documents on your machine. Thus, if you had a Word document on your hard drive and an email address was in that document, Mimail would find it. This strategy meant that Mimail would spread further than many other viruses. Mimail had its own built-in email engine, so it did not have to “piggyback” off your email client. It could spread regardless of what email software you used.

These two differences from most viruses make Mimail interesting to people who study computer viruses. There are a variety of techniques that allow you to programmatically open and process files on your computer; however, most virus attacks do not employ them. The scanning of the document for email addresses indicates a certain level of skill and creativity on the part of the virus writer. In this author’s opinion, Mimail was not the work of an amateur but rather a person with professional-level programming skill.

##### The Bagle Virus

Bagle is another historical virus. It is not an issue today but is noteworthy in the history of malware because it combined email attachments with a fake virus warning. The Bagle virus began to spread rapidly in the fourth quarter of 2003. The email it sent claimed to be from your system administrator. It would tell you that your email account had been infected by a virus and that you should open the attached file to get instructions. Once you opened the attached file, your system was infected. This virus was particularly interesting for several reasons. To begin with, it spread both through email and by copying itself to shared folders. Second, it could scan files on your PC, looking for email addresses. Finally, it would disable processes used by antivirus scanners. In biological terms, this virus took out your computer’s “immune system.” The disabling of virus scanners was a new twist that indicated at least moderate programming skills on the part of the virus creator.

##### A Nonvirus Virus

Another new type of virus has been gaining popularity in the past few years, and that is the “nonvirus virus” or, put simply, a hoax. Rather than actually writing a virus, a hacker sends an email to every address he has. The email claims to be from some well-known antivirus center and warns of a new virus that is circulating. The email instructs people to delete some file from their computer to get rid of the virus. The file, however, is not really a virus but part of a computer’s system. The jdbgmgr.exe virus hoax used this scheme. It encouraged the reader to delete a file that was actually needed by the system. Surprisingly, a number of people followed this advice and not only deleted the file but promptly emailed their friends and colleagues to warn them to delete the file from their machines.

FYI: The Morris Internet Worm

The Morris worm was one of the first computer worms ever to be distributed over the Internet—and it was certainly the first to gain any significant media attention.

Robert Tappan Morris, Jr., then a student at Cornell University, wrote this worm and launched it from an MIT system on November 2, 1988. Morris did not actually intend to cause damage with the worm. Instead, he wanted the worm to reveal bugs in the programs it exploited in order to spread. However, bugs in the code allowed an individual computer to be infected multiple times, and the worm became a menace. Each additional “infection” spawned a new process on the infected computer. At a certain point, the large number of processes running on an infected machine slowed down the computer to the point of being unusable. At least 6000 UNIX machines were infected with this worm.

Morris was convicted of violating the 1986 Computer Fraud and Abuse Act and was sentenced to a $10,000 fine, 3 years’ probation, and 400 hours of community service. But perhaps the greatest impact of this worm was that it led to the creation of the Computer Emergency Response Team (CERT). CERT ([www.cert.org](http://www.cert.org)) is an organization hosted at Carnegie Mellon University that is a repository for security bulletins, information, and guidelines. CERT is a source that any security professional should be familiar with.

##### Flame

No modern discussion of viruses would be complete without a discussion of Flame. This virus, which first appeared in 2012, targeted Windows operating systems. The first item that makes this virus notable is that it was specifically designed by the U.S. government for espionage. It was discovered in May 2012 at several locations, including Iranian government sites. Flame is spyware that can monitor network traffic and take screenshots of the infected system.

##### The Earliest Viruses

It is instructive to consider the very first viruses every found. In 1971, Bob Thomas created what is widely believed to be the first computer virus, named Creeper. It spread through the ARPANET (the precursor to the Internet) and displayed a message “I’m the creeper, catch me if you can!” Another program, named Reaper, was created to delete Creeper.

Wabbit, which was found in 1974, made multiple copies of itself, thus adversely affecting the performance of the infected computer.

Apple Viruses 1, 2, and 3 are some of the first viruses “in the wild” or public domain. These viruses, which were found on the Apple II operating system in 1981, spread through Texas A&M via pirated computer games.

#### The Impact of Viruses

In early 2018, Taiwan Semiconductor Manufacturing Company, one of the largest chipmakers and a supplier for Apple, said it had been hit by a computer virus that had affected computer systems and fabrication tools. Estimates placed the damages over $170 million. The specific virus was not described in the news reports, but a single company being hit with a single virus causing so much havoc illustrates the dangers of computer viruses.

#### Rules for Avoiding Viruses

You should notice a common theme with all virus attacks (except the hoax): They want you to open some type of attachment. The most common way for a virus to spread is as an email attachment. Knowing this, you can follow a few simple rules to drastically reduce the odds of becoming infected with a virus:
