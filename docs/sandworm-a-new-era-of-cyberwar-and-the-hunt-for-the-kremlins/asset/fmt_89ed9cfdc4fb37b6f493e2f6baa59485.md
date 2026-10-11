
# 8

# BLACKOUT

“The question is not for whom the bell tolls,” Yushchenko warned. “The bell tolls for us all. This is a threat to every country in the world.”

***

In late November 2015, as the pace of the digital blitzkrieg against Ukraine was accelerating, John Hultquist was invited to give a briefing at the Pentagon, a rare chance to win contracts and bend the ear of the world’s most powerful military. He sat down among intelligence officials at a conference table in the most senior officer’s medal-adorned office, deep in the gargantuan building.

When it came to his turn to speak, Hultquist wasted no time introducing his favorite subject. He gave the elevator-pitch version of Sandworm’s history: Russian fingerprints, dangerous sophistication, targets stretching from Poland to the United States but clustering in Ukraine, with a disturbing focus on critical infrastructure. He noted that Russia’s actual, ongoing war with Ukraine was heating up and that it had increasingly metastasized from physical invasion to disruptive digital attacks on everything from media firms to government agencies. Pro-Ukrainian activists had retaliated against Russia with a lower-tech form of sabotage, tearing down pylons that supplied electricity to the Crimean peninsula, throwing the territory Russia had seized into a mass blackout. Putin, of course, blamed the Ukrainian government for the sabotage.

With all those elements aligning, Hultquist went on to predict that Russia’s hackers were about to carry out a form of attack that had never before occurred in the history of cybersecurity. “I think there’s a good chance,” he told the Pentagon officials, “that they’re going to try to turn out the lights.”

The military audience seemed to acknowledge his warning, Hultquist remembers. But there were myriad other trouble spots across an internet crawling with potential threats, and so the meeting moved on. “To be honest,” Hultquist says, “I don’t think it really sunk in at all.”

At first, Robert Lee blamed the squirrels.

It was Christmas Eve 2015—and also, as it happened, the day before Lee was set to be married in his hometown of Cullman, Alabama. A barrel-chested, bearded, and redheaded twenty-seven-year-old, Lee had recently left a high-level job at the NSA, where he’d led a team of analysts focused on a unique mission: tracking hackers who threatened critical infrastructure. Now he was settling down to launch his own security start-up and marry the Dutch girlfriend he’d met while stationed abroad.

As Lee busied himself with wedding preparations, he saw news reports that immediately distracted him from his matrimonial duties. Hackers had just taken down a power grid in western Ukraine, the headlines on his phone’s screen read. A significant swath of the country had apparently gone dark for six hours. After the initial wave of adrenaline passed, Lee’s natural skepticism kicked in. He remembered this was probably just more media hype; he had other things on his mind, and he’d heard spurious claims of hacked grids plenty of times before. The cause was usually a rodent or a bird; the notion that squirrels represented a greater threat to the power grid than hackers had become a running joke in the industry.

The next day, however, just before the wedding itself, Lee received a text message that dragged the incident back into his awareness. It came from Mike Assante, the director of industrial control systems security at the SANS Institute, an elite cybersecurity training center where Lee also taught courses. A message from Assante, for Lee, held far more weight than any news outlet: When it comes to digital threats affecting power grids, Assante was one of the most respected experts in the world. And he was telling Lee that the Ukraine blackout hack looked like the real thing.

Lee cleared the messages from his phone and tried to focus on his wedding. But moments after he had said his vows and kissed his bride, a contact in Ukraine pinged him: The blackout hack was real, the man said, and he needed Lee’s help.

Lee had spent his career preparing for this moment. At the NSA, he’d devoted years to tracking the rare, sophisticated hacker teams that targeted power grids, pipelines, and water systems, priding himself on protecting the most fundamental underpinnings of civilization. He’d briefed the government’s most senior officials on those threats. He’d gone so far as to build mock-ups of industrial control systems for testing in his own basement. Now, with absurdly bad timing, the historic milestone he’d anticipated for years seemed to have finally arrived: the first-known case of an actual hacker-induced blackout.

There was hardly a choice to be made. He skipped out on not only Christmas with his family but also his own wedding reception, found a quiet corner of the room, and began to text with Assante about the details of the Ukrainian power grid attack.

Still in his wedding suit, Lee eventually retreated to his mother’s desktop computer in his parents’ nearby home. Working in tandem with Assante, who had pulled out his laptop and hidden in the corner of a friend’s Christmas party in rural Idaho, they examined maps of Ukraine and a chart of its power grid. The three power companies’ substations that had been hit were in different regions of the country, hundreds of miles from one another, and unconnected. “This was not a squirrel,” Lee concluded with a dark thrill.

By that night, Lee was busy dissecting the `KillDisk` malware his Ukrainian contact had sent him from the hacked power companies, much as Yasinsky had done after the StarLightMedia hack months before. “I have a very patient wife,” Lee says of his decision to spend his wedding night in front of a computer.

Over the next few days, he received from his Ukrainian contact another sample of code and forensic data from the attacks. Pulling it apart, Lee saw how the intrusion had started. It began with a phishing email impersonating a message from the Ukrainian parliament. A malicious Word attachment had silently run a script known as a macro, a little program hidden inside the document, on the victims’ machines.

The effect was the same as the zero-day technique iSight had first found Sandworm using in its infected Microsoft PowerPoint documents in 2014, but with a new trade-off: Without the zero day, the victims had to be tricked into clicking a button to allow the script to run. Until they clicked, the document would appear to be missing content or broken, so most users unthinkingly clicked to load it. But by using a simpler replacement for their zero-day technique, the hackers had been able to operate much less conspicuously, and their attack didn’t depend on keeping a rare vulnerability secret from Microsoft.

The Word script had planted an infection of `BlackEnergy`, the piece of malware that had by now become practically the official national disease of Ukrainian IT networks. From that foothold, it appeared, the hackers had spread through the power companies’ systems and eventually compromised a virtual private network, a tool the companies had used for remote access to their systems—including the highly specialized industrial control software that gives operators command over equipment like circuit breakers.

Looking at the attackers’ methods and their use of `BlackEnergy`, Lee began to make connections to iSight’s earlier findings and others from his time at NSA. This was the work of Sandworm, he was sure of it. After years of lurking, spying, building their capabilities, and performing reconnaissance work, Sandworm had taken the step that no other hackers had ever dared to: They’d caused an actual blackout, indiscriminately disrupting the physical infrastructure of hundreds of thousands of civilians.
