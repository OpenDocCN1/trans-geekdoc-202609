
- 6. Adam Grove. Two modellings for theory change. *Journal of Philosophical Logic*, 17(2):157–170.
- 7. Sanjay Jain, Daniel N. Osherson, James R. Royer, and Arun Sharma. *Systems That Learn: An Introduction to Learning Theory*.
- 8. Sanjay Jain and Arun Sharma. On a generalized notion of mistake bounds. *Information and Computation*, 166(2):156–166.
- 9. Sarit Kraus, Daniel Lehmann, and Menachem Magidor. Nonmonotonic reasoning, preferential models and cumulative logics. *Artificial Intelligence*, 44(1):167–207.

## 8 Counterfeits and Kill Switches
How Hardware Security can Impact You

Hammond Pearce
School of Computer Science and Engineering, UNSW Sydney
Kensington, Australia

### 8.1 COUNTERFEITS AND KILL SWITCHES: HOW HARDWARE SECURITY CAN IMPACT YOU

As the digital world expands, privacy and operational threats against computer systems are becoming ever more pervasive. Personal information is frequently stolen in breaches, and essential services face shutdowns due to cyberattacks. Recent high-profile incidents, such as the 2022 Medibank data breach of over 9 million Australians' medical data, and the 2023 disruption of Sydney’s port systems, highlight the growing danger. While most focus remains on software vulnerabilities, hardware-based attacks present even graver, often invisible threats. Here, a compromised circuit could shut down essential infrastructure or result in the failure of aircraft controls. This chapter introduces readers to the emerging field of hardware security, exploring how counterfeit electronics and hardware Trojans can infiltrate and compromise critical systems. It also discusses the countermeasures being developed to combat these insidious risks, making the case for why hardware security deserves broader attention in today’s world.

### 8.2 INTRODUCTION: WHAT IS HARDWARE SECURITY?

Consider this scenario. You have a large number of photos, videos, documents, and other files on your computer. You need to get these files to another computer. What’s the easiest way to move a large number of files? Why, an external USB hard drive, of course.

So, you go to your local shop, or even an e-shop online. You take a look at external hard drives. Wow! There are so many options. Walmart in the USA lists 282 results when searching ‘USB hard drive’. Some of them are made by Samsung, some by Seagate, some by Western Digital, and so many other brands besides. Target Australia has over 100 of these, too. When you ask Amazon, it refuses to list a count, but suffice to say there are so many results for this search it would take weeks to traverse them.

So, what should you do? I guess you could just buy any of them – they’re all as good as one another, right?

Well, unfortunately – probably not.

Never mind their listed specifications, never mind their purported brand names: unfortunately, computer electronics, like many other commodity products such as shoes and children’s products, have been overwhelmed with fake listings selling counterfeit products. These inferior goods can be both frustrating (when they underperform) or dangerous (when considering items meant for human use or consumption). Despite attention, such issues have come up again and again (e.g. [14, 25, 5]).

So why is this? Why is it so difficult to ensure that our products match their design? Well, part of the challenge – beyond simply the presence of unscrupulous actors in this world who are endlessly motivated to obtain money at minimum cost – is that it is fundamentally difficult to ensure that a given piece of the real-world is exactly what it claims to be. How can you, a consumer at home, validate that a bottle of shampoo is actually made by the company written on the bottle? How can you be sure that a shoe with Nike’s logo came from a Nike factory? So too, how could you be sure if the hard drive you want to purchase is actually genuine?

Counterfeits have always been a problem, but it’s only recently been that those same circumstances which allow us to buy a fake hard drive also might allow for even more harmful happenstances to occur. For a recent example, consider the story of the “pager attacks” as reported by the BBC [20]. Here, after the Hezbollah paramilitary group found they were unable to prevent the Israeli intelligence and military services from hacking and tracking their cellphones, in February 2024 their secretary-general Hassan Nasrallah issued instructions for the group’s members to use old-fashioned and low-tech pagers instead. These pagers were then nominally purchased from the global marketplace. Except – instead of receiving the intended Gold Apollo models, Hezbollah received shipments of devices secretly compromised by the Israeli Mossad to contain small explosive charges. Mossad then repeated this supply chain attack on a series of walkie-talkies also destined for the paramilitary group.

Putting aside the politics of the situation, this is a situation beyond mere counterfeiting. This is an escalation, a supply chain compromise taking the device from having fake branding and cost-saving cutouts to one where the device has been maliciously compromised to have the ability to perform an attack on the owner. These are called Hardware Trojans [6], so named for the apocryphal Trojan Horse. In the story, the Trojan Horse was a sculpture left as a gift for the defending city of Troy, which brought it inside their city only to later discover it was full of Greek soldiers (who then proceeded to attack the city from the inside, and opened the gates for the main army to enter). Hardware Trojans can be similarly destructive, as these compromised pagers and walkie-talkies cruelly demonstrated. In September 2024, Mossad activated both sets of explosives. They ultimately killed dozens of people including civilians and children, and injured thousands more.

Such physical tampering need not be so extreme as to physically include hidden explosives in order to have the desired effect, though. One of the scariest concepts for the modern world, powered as it is by a veritable sea of interconnected devices and computers, is that these devices might have hidden “Kill Switches” which would render them inoperable at the very moment of an attacker’s choosing. You could imagine such an ability to be considerably attractive to cyber-criminals: imagine a blackmailer who rings you while you are in a self-driving car, and threatens to disable the brakes on a highway unless you transfer them thousands of dollars!

Such a capability is also interesting to nation-states. Imagine how strategically beneficial it would be if your country could sneak a ‘Kill Switch’ into a foreign adversary’s military equipment. Here, though, we do not have to imagine hard – this is exactly what was reported by IEEE Spectrum [1] to have happened in September 2007, when Israeli fighter jets were able to stealthily enter Syrian airspace as part of Operation Outside the Box. At the time, it was a mystery to how exactly the jets had hidden themselves from state-of-the-art defensive radar installations. But, it was soon reported that a supply chain attack against commercial off-the-shelf microprocessor integrated circuits had been secretly completed, allowing the Israeli military to disrupt radar functions – having them report clear skies even as jets flew overhead.

So, what is hardware security?

Hardware security tries to protect the real-world chips, circuits, and devices that build up our real-world computing and communications infrastructure. It tries to prevent counterfeiting attacks, where low-cost poor-quality imitations impact both our bottom lines as producers but also our strength as a brand. So too it tries to prevent the possibility of hardware Trojan attacks, where adversaries aim to sneak malicious changes into our designs that might compromise their functionality or cause real-world harms.

The security of our computer systems impacts all of us. When our private data is stolen, attackers can impersonate us by opening credit cards in our names, attempt to swindle money from our personal relations, and can attempt to drain our savings accounts. These attacks can occur in many different ways, from leaked passwords to faulty websites. Sometimes they happen due to malicious employees – and sometimes they can be engineered to occur socially, from cold-emailing unsuspecting victims to strategic placement of scam advertisements.

Most people are familiar with the concept of software vulnerabilities – flaws or bugs in code that cybercriminals can exploit to gain unauthorized access, disrupt operations, or extract sensitive data. Unfortunately, as we have now introduced, the hardware that makes up our digital devices, from smartphones to critical infrastructure systems, is just as susceptible to being compromised. Worse, unlike software issues, which can often be patched remotely, hardware vulnerabilities – like the aforementioned ‘kill switches’ – can be embedded in the physical components. This can make them significantly harder to detect and mitigate, particularly if a fix requires changes to the underlying hardware.
