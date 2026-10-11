
If Trump sensed the news could be used against him politically, he was right. In late June 2017, eighteen Democratic senators and Independent Bernie Sanders signed a letter to the president, citing Dragos’s work and demanding Trump direct the Department of Energy to conduct a new analysis of the Russian government’s capabilities to disrupt America’s power grid. They also asked for an exploration of any attempts the Kremlin had already made to compromise America’s electric utilities, pipelines, or other energy infrastructure.

“We are deeply concerned that your administration has not backed up a verbal commitment prioritizing cybersecurity of energy networks and fighting cyber aggression with any meaningful action,” the legislators wrote. The White House never responded.

Lee quickly regretted that the Crash Override news had become a partisan football. But he was far more frustrated still that history was replaying itself from a year before: Another White House seemed to be pushing another Ukrainian blackout under the rug. “When a cyberattack takes down electric power for the first time with a capability that’s scalable and impactful to people around the world, it doesn’t even get a sound bite,” Lee said. “And that’s ridiculous.”

***

■

In the Dragos researchers’ mad seventy-two-hour rush to dissect Crash Override, a.k.a. Industroyer, they had missed something. In fact, Rob Lee would tell me that one element of the code that ESET described in its report was lacking from the version of the malware Dragos found. It hadn’t, apparently, been used in the Ukrenergo attack. It’s not clear if it even worked. But it was, in some ways, the most foreboding clue of all.

At one point as he was combing the Industroyer code, Cherepanov had spotted that it was programmed to send out a strange eighteen-byte string of numbers. When he googled that string, he found an advisory about a known vulnerability in Siemens Siprotec devices—protective relays designed to function as safety kill switches for electrical equipment. Send that one packet of eighteen bytes to a Siemens Siprotec box, and it would become unresponsive. Only manually rebooting it would wake it up again.

When Mike Assante read ESET’s report on Industroyer at his home in Wyoming, that Siprotec trick immediately stuck out to him. Protective relays were, after all, the devices he’d always worried might be hacked to not simply disrupt but *destroy* physical equipment. It had been just over ten years since he’d led the Aurora demonstration, showcasing exactly the scale of disaster that might be possible when protective relays are maliciously altered.

The vulnerability exploited by Sandworm’s malware, unlike his Aurora attack, didn’t actually change the logic of a protective relay to cause dangerous effects. It simply put the relay to sleep. But if that technique had been combined with other kinds of transmission station sabotage, it could still have caused far more permanent damage: Disable protective relays while messing with the electric load on certain components, and hackers might melt lines or burn transformers, outcomes that would make a one-hour blackout look like an innocent game of tag by comparison. “If you ever see a transformer fire, they’re massive,” Assante says. “Big black smoke that all of a sudden turns into a fireball.”

In 2007, he had first warned the world about hackers unleashing physical destruction on power systems. Now someone seemed to be taking the first steps toward a very literal Aurora-style attack. As he looked out the windows of his second-story home office at the distant Teton mountain range, Assante felt a strange mix of pride and bitter dread. “There was the satisfaction of not having had a failure of imagination,” he says. “But also the fear: They’re developing these capabilities now.”

His Aurora nightmare was now on the verge of coming true. “This is real,” he thought to himself. “It’s happening.” The future he’d glimpsed a full decade earlier had arrived.

# PART IV

# APOTHEOSIS

> Out of the sand haze came an orderly mass of flashing shapes—great rising curves with crystal spokes that resolved into the gaping mouths of sandworms, a massed wall of them, each with troops of Fremen riding to the attack. They came in a hissing wedge, robes whipping in the wind as they cut through the melee on the plain.

# 20

# MAERSK

It was a perfect, sunny summer afternoon in Copenhagen when the world’s largest shipping conglomerate began to lose its mind.

The headquarters of A.P. Møller-Maersk sit beside the breezy, cobblestoned esplanade of Copenhagen’s harbor. A ship’s mast carrying the Danish flag is planted by the building’s northeastern corner, and six stories of blue-tinted windows look out over the water, facing a dock where the Danish royal family parks its yacht. In the building’s basement, employees can browse a corporate gift shop, stocked with Maersk-branded bags and ties, and even a rare Lego model of the company’s gargantuan Triple-E container ship, a vessel roughly as large as the Empire State Building laid on its side, capable of carrying another Empire State Building–sized load of cargo stacked on top of it.

That gift shop also houses a technology help center, a single desk manned by IT troubleshooters next to the shop’s cashier. And on the afternoon of June 27, 2017, confused Maersk staffers began to gather at that help desk in twos and threes, almost all of them carrying laptops. On some of the machines’ screens were messages that read “repairing file system on C:” with a stark warning not to turn off the computer. Others, more surreally, read “oops, your important files are encrypted” and demanded a payment of $300 worth of bitcoin to decrypt them.

Across the street, an IT administrator named Henrik Jensen was working in another part of the Maersk compound, an ornate white stone building that in previous centuries had served as the royal archive of maritime maps and charts.⁹

He quietly swore under his breath. Jensen assumed the unplanned reboot was a typically brusque move by Maersk’s central IT department, a little-loved entity in England that oversaw most of the corporate empire, whose eight business units ranged from ports to logistics to oil drilling, in 574 offices in 130 countries around the globe.

Jensen looked up to ask if anyone else in his open-plan office of IT staffers had been so rudely interrupted. And as he craned his neck, he watched every other computer screen around the room blink out in rapid succession.

“I saw a wave of screens turning black. Black, black, black. *Black black black black black,*” he says. The PCs, Jensen and his neighbors quickly discovered, were irreversibly locked. Restarting them only caused them to display the Bitcoin ransom message other Maersk staffers had been seeing.

All across Maersk headquarters, the full scale of the crisis was starting to become clear. Within half an hour, Maersk employees were running down hallways, yelling to their colleagues to turn off computers or disconnect them from Maersk’s network before the malicious software could infect them as it dawned on them that every minute could mean dozens or hundreds more corrupted PCs. Tech workers ran into conference rooms and unplugged machines in the middle of meetings. Soon staffers were hurdling over locked key-card gates, which had been paralyzed by the still-mysterious malware, to spread the warning to other sections of the building.

Disconnecting Maersk’s entire global network took the company’s IT staff more than two panicky hours. By the end of that process, all employees had been ordered to turn off their computers and leave them at their desks. The digital phones at every cubicle, too, had been rendered useless in the emergency network shutdown.
