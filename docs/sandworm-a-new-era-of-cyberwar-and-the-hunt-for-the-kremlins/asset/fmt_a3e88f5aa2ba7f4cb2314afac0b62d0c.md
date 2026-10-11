
When he saw Huss’s tweet, Hutchins’s heart started racing. Could it be true? He needed to try his own test for confirmation. He ran a simulation on his server of a WannaCry infection and allowed it to reach out to his domain. Sure enough, it ceased its evil behavior the instant it connected. Then he ran the test again, this time blocking the malware’s connection to his sinkhole. In that second test, the computer’s files were immediately encrypted, and WannaCry’s menacing ransom message popped up on his screen. The test had confirmed that his kill switch worked.

Hutchins reacted in a way that perhaps no one ever before in history has reacted to seeing his computer paralyzed with ransomware: He leaped up from his chair and jumped around his bedroom, overtaken with joy.

***

■

The goal of WannaCry’s creators remains a mystery. Were they seeking to make as much money as possible from their supercharged ransomware scheme? Or merely to inflict maximal global chaos? Either way, building a kill switch into their malware seemed like a strangely sloppy act of self-sabotage.^([^(10)](#fn10))

The WannaCry programmers had been careless in other ways, too. The payment mechanism built into their code was, effectively, useless: Unlike better-designed ransomware, WannaCry had no automated system for distributing decryption keys to victims who had paid, or even keeping track of who had paid and who hadn’t. When that became clear to victims, they stopped paying. The entire scheme generated a total of less than $200,000, a smaller sum than the annual salary of many of the individual malware analysts tracking it.

Some researchers came to the conclusion that WannaCry must have been released prematurely: Perhaps its creators had been testing their worm, and then, as worms tend to do—as Stuxnet had done seven years earlier—it spread beyond its creators’ control, before it was truly ready.

Finally, in another critical act of carelessness, WannaCry’s coders had left clues about their identity, too. Within days, security researchers at Google and the Russian cybersecurity firm Kaspersky had noticed that code used in WannaCry overlapped with a favorite backdoor program of a group of North Korean government hackers known as Lazarus. By December 2017, the Trump White House would announce that it had determined North Korea was behind the attack. The same group of hackers who had devastated Sony three years earlier had now unleashed that same destruction on every network in the world, and only an accidental kill switch had prevented utter disaster.^([^(11)](#fn11))

***

■

By the end of 2017, theories of how the Shadow Brokers had pulled off their shocking theft of NSA secrets would begin to come to light, too. In December of that year, a sixty-seven-year-old former NSA staffer and developer for the agency’s Tailored Access Operations hacking team named Nghia Hoang Pho pleaded guilty to violating his security clearances. He’d taken home enormous troves of classified materials. He’d later tell a Maryland court that after bad performance reviews he’d merely sought to study the materials as a way to get ahead in his work. Pho was sentenced to sixty-six months in prison.

That case connected with another piece of the narrative reported by *The Wall Street Journal* from months earlier, claiming that Russian government hackers had used their access to the antivirus software of Moscow-based Kaspersky Labs to steal a vast collection of NSA files from the home computer of a contract employee of the agency. The contractor, the report stated, had been foolish enough to not only violate his clearances and bring the top secret material home but also to run Kaspersky’s software, which—like most antivirus programs—included a capability that allowed the program to upload files to the company’s remote servers for analysis.

Kaspersky responded in a statement, denying that it had any “inappropriate ties” to the Russian government that might have let Kremlin hackers exploit its antivirus code. A few weeks later, the company followed up with the results of an internal investigation: It had, the company admitted, uploaded a collection of NSA hacking tools in 2014. But it claimed to have immediately deleted them upon discovering what the files represented.^([^(12)](#fn12))

Even as those clues added to the circumstantial evidence of Russia’s responsibility for the leak of the NSA’s secret armory, nothing suggested that either the Shadow Brokers or WannaCry was connected to Sandworm. But just as artists inspire one another, Sandworm was no doubt watching and learning from its hacker peers. The Shadow Brokers had made available a powerful hacking tool that a team of hyper-bellicose cyberwarriors could hardly ignore.

The WannaCry worm that followed offered Sandworm a chance to observe a weapon of mass disruption in action—and, it would turn out, a few ideas about how to build an even more explosive one.

## 23

## MIMIKATZ

In May 2012, Benjamin Delpy walked into his room at the President Hotel in Moscow and found a man dressed in a dark suit with his hands on Delpy’s laptop.

Just a few minutes earlier, the twenty-five-year-old French programmer had made a quick trip to the front desk to complain about the room’s internet connection. He had arrived two days ahead of a talk he was scheduled to give at the nearby security conference Positive Hack Days, only to discover that his room had no Wi-Fi connection. Nor was the ethernet jack working. Downstairs, one of the hotel’s staff insisted he sit in the lobby while a technician was sent up to fix it. Delpy refused and went back to wait in the room instead.

When he returned, as Delpy tells it, he was shocked to find the stranger standing at the room’s desk, a small black roller-board suitcase by his side, his fingers hurriedly retracting from Delpy’s keyboard. The laptop still showed a locked Windows log-in screen.

The man mumbled an apology about his key card working on the wrong room, brushed past Delpy, and was out the door before Delpy could even react. “It was all very strange for me,” Delpy said. “Like being in a spy film.”

It didn’t take Delpy long to guess why his laptop had been the target of a literal black-bag job. That computer contained the subject of his presentation at the Moscow conference, an early version of a program he’d written called `Mimikatz`.

`Mimikatz` had been a kind of hobby for Delpy. He worked as an IT manager at a French government institution—which one he declined to tell me—and had observed that Windows had a subtle flaw: Microsoft had created a feature called `WDigest`, designed to allow corporate and government Windows users to more conveniently prove their identity to different applications on their networks or on the web. `WDigest` would hold users’ authentication credentials like usernames and passwords in a computer’s memory so they would only have to be entered once and could then be effortlessly reused to unlock other sensitive programs.

Delpy noticed that while Windows encrypted that copy of the user’s password in the computer’s memory, it kept a copy of the secret key to decrypt it handy in memory, too. “It’s like storing a password-protected secret in an email with the password in the same email,” Delpy explained to me.
