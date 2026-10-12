
Imagine a teacher in a classroom full of six-year-olds. Each child demands the teacher's attention. At first, the teacher hears one child and gives the child attention. Then a second child calls, and the teacher focuses on that child while trying to remember what the first child needed. Seeing that calling out works, children three, four, and five cry out for the teacher, but this frustrates other children who also demand attention. Of course, each child who calls out does so more loudly than the previous ones, and soon the classroom is a cacophony of children's shouts, making it impossible for the teacher to do anything except tell them all to be quiet, wait their turn, and be patient (none of which comes naturally to six-year-olds). The teacher becomes so overloaded with demands that the only solution is to dismiss all current demands and start afresh.

An attacker can try for the same overloading effect by presenting commands more quickly than a server can handle them; servers often queue unmet commands during moments of overload for service when the peak subsides, but if the commands continue to come too quickly, the server eventually runs out of space to store the demand. Such an attack is called an **overload** or **flood**.

The target of a flooding attack can be an application, such as a database management system; an operating system or one of its components, for example, file or print server; or a network appliance like a router. Alternatively, the flooding attack can be directed against a resource, such as a memory allocation table or a web page. On the day Michael Jackson died, Google received so many queries about him that the Google engineers thought they were under attack and took evasive measures that, ironically, limited access to the Google news service. A denial-of-service flooding attack can be termed **volumetric**, meaning it simply seeks to saturate or exhaust the capacity of a critical telecommunications link.

***

**A flooding attack occurs from demand in excess of capacity, from malicious or natural causes.**

***

### Blocked Access

As another physical analogy, consider a traffic accident that stops traffic in both directions of a busy, two-lane road. As motorists begin to line up behind the accident, at some point one driver concludes the right approach is to slip into the oncoming traffic lane to get around all the stopped cars and, naturally, others immediately follow. They get as far as the accident and have to stop. What then happens is that two lanes of traffic build up at the point of the accident on both sides of the accident, meaning that police and other emergency vehicles cannot get past the two solid lines of cars in both directions to get to the accident. Even when the disabled cars are pushed off the road to clear the accident, all lanes are filled with cars that cannot move because there is no room either in front or behind.

In computer security, the attacker may simply prevent a service from functioning. The attacker could exploit a software vulnerability in an application and cause the application to crash. Or the attacker could interfere with the network routing mechanisms, preventing access requests from getting to the server. Yet another approach would be for the attacker to manipulate access control data, deleting access permissions for the resource, or to disable the access control mechanism so that nobody could be approved for access. In [Sidebar 6-16](#ch06.html#ch06sb16), the attacker alleged that he had deleted the original copy of an important database and encrypted a backup copy, which he was holding for ransom.

### Access Failure

Either maliciously or not, hardware and software fail from time to time; of course, it always seems that such nonmalicious failures occur only at critical times. Software stops working due to a flaw, or a hardware device wears out or inexplicably stops. The failure can be sporadic, meaning that it goes away or corrects itself spontaneously, or the failure can be permanent, as from a faulty component.

***

#### Sidebar 6-16 State of Virginia Database Held for Ransom

State officials in Virginia received a ransom note in May 2009 demanding $10 million for release of a state database of 8.3 million records of drug prescriptions for state residents. The database held copies of prescriptions for Federal controlled substances filled since 2003.

Ransom note:

> ATTENTION VIRGINIA
>
> I have your s\[censored\]! In \*my\* possession, right now, are 8,257,378 patient records and a total of 35,548,087 prescriptions. Also, I made an encrypted backup and deleted the original. Unfortunately for Virginia, their backups seem to have gone missing, too. Uhoh :(
>
> For $10 million, I will gladly send along the password. You have 7 days to decide. If by the end of 7 days, you decide not to pony up, I'll go ahead and put this baby out on the market and accept the highest bid. Now I don't know what all this \[censored\] is worth or who would pay for it, but I'm bettin' someone will. Hell, if I can't move the prescription data at the very least I can find a buyer for the personal data (name, age, address, social security #, driver's license #). (Brian Krebs, *Washington Post* Security Fix blog, 4 May 2009)

Although the attacker alleged that he had deleted the original, made one encrypted backup copy, and deleted all other backups, state officials were able to restore the database from backup copies and could access it with no difficulty. Sandra Whitley Ryals, director of the Virginia Department of Health Professions stated, "We are satisfied that all data was properly backed up and that these backup files have been secured." (WHSV TV, Richmond, VA, from WHSV.com, 6 May 2009) Thus, the ransom demand seems to have been a hoax. Nevertheless, removing sensitive data and holding it for ransom is a potentially effective means to block access.

***

These, then, are the three root threats to availability:

- insufficient capacity; overload
- blocked access
- unresponsive component

The attacker will try to actualize any of these threat types by exploiting vulnerabilities against them. In the next section we examine some of these potential vulnerabilities. In [Sidebar 6-17](#ch06.html#ch06sb17) we describe an incident that resulted from a combination of factors—none malicious—including age of components, antiquated network design, and faulty communications protocols.

***

#### Sidebar 6-17 Beth Israel-Deaconess Hospital Systems Down

In 2002, Boston's Beth Israel-Deaconess Medical Center was recognized by *Information Week* as 16th of the 500 top innovative IT groups in the United States. In the same year the hospital suffered a denial-of-service incident that sent the entire hospital back to using the paper forms they had abandoned years earlier [[BER03](#bib01.html#bib_60)].

On Wednesday, 13 November 2002, the first symptom noticed was that ordinarily instantaneous email was taking ten seconds to transmit. The network engineers observed that one core network switch was saturated by a sudden surge in traffic from an unknown source. To cope with this volume from an unknown cause, the engineers began disintegrating the network, closing connections to simplify traffic flow in the network and also to help identify the source of the problem. Later the engineers would learn that closing portions of the network actually exacerbated the problem.
