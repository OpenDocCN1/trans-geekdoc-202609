
# Exploiting Maintenance Difficulties

Maintaining computer systems is no trivial matter. Software vendors often release updates, many of which may impact other programs running on a machine. Yet, some patches are absolutely critical to be installed in a timely fashion because they fix bugs in software — bugs that may introduce exploitable security vulnerabilities. The conflict between security and following proper maintenance procedures is a never-ending battle — and security doesn’t often win.

As a result, the vast majority of computers aren’t kept up to date. Even people who do enable automatic updates on their devices may not be up to date — both because checks for updates are done periodically, not every second of every day, and because not all software offers automatic updating. Furthermore, sometimes updates to one piece of software introduce vulnerabilities into another piece of software running on the same device.

# Advanced Attacks

If you listen to the news during a report of a major cyberbreach, you’ll frequently hear commentators referring to advanced attacks. While some cyberattacks are clearly more complex than others and require greater technical prowess to launch, no specific, objective definition of an advanced attack exists. That said, from a subjective perspective, you may consider any attack that requires a significant investment in research and development to be successfully executed to be advanced. Of course, the definition of significant investment is also subjective. In some cases, R&D expenditures are so high and attacks are so sophisticated that there is near universal agreement that an attack was advanced. Some experts consider any zero-day attack to be advanced, but others disagree.

Advanced attacks may be opportunistic, targeted, or a combination of both.

**Opportunistic** attacks are attacks aimed at as many possible targets as possible in order to find some that are susceptible to the attack that was launched. The attacker doesn’t have a list of predefined targets — the attacker’s targets are effectively any and all reachable systems that are vulnerable to the launched attack. These attacks are similar to someone firing a massive shotgun in an area with many targets in the hope that one or more pellets will hit a target that it can penetrate.

**Targeted attacks** are attacks that target a specific party and typically involve utilizing a series of attack techniques until one eventually succeeds in penetrating into the target. Additional attacks may be launched subsequently in order to move around within the target’s systems.

## Opportunistic attacks

The goal of most opportunistic attacks is usually to make money — which is why the attackers don’t care whose systems they breach; money is the same regardless of whose systems are breached in order to make it.

Furthermore, in many cases, opportunistic attackers may not care about hiding the fact that a breach occurred — especially after they’ve had time to monetize the breach, for example, by selling lists of passwords or credit card numbers that they stole.

While not all opportunistic attacks are advanced, some certainly are. Opportunistic attacks are quite different than targeted attacks.

## Targeted attacks

When it comes to targeted attacks, successfully breaching any systems not on the target list isn’t considered even a minor success.

For example, if a Russian operative is assigned the mission to hack into the Democratic and Republican parties’ email systems and steal copies of all the email on the parties’ email servers, the mission is going to be deemed a success only if the operative achieves those exact aims. If the operative manages to steal $1 million from an online bank using the same hacking techniques that were directed at the targets, it will not change a failure to breach the intended targets into even a small success. Likewise, if the goal of an attacker launching a targeted attack is to take down the website of a former employer the attacker had issues with, taking down other websites doesn’t accomplish anything in the attacker’s mind.

Because such attackers need to breach their targets no matter how well defended those parties may be, targeted attacks often utilize advanced attack methods — for example, exploiting vulnerabilities not known to the public or to the vendors who would need to fix them.

As you may surmise, advanced targeted attacks are typically carried out by parties with much greater technical prowess than those who carry out opportunistic attacks. Often, but not always, the goal of targeted attacks is to steal data undetected or to inflict serious damage — not to make money. After all, if one’s goal is to make money, why expend resources targeting a well-defended site? Take an opportunistic approach and go after the most poorly defended, relevant sites.

Some advanced threats that are used in targeted attacks are described as **advanced persistent threats** (APTs):

*   **Advanced:** Uses advanced hacking techniques, likely with a major budget to support R&D
*   **Persistent:** Keeps trying different techniques to breach a targeted system and won’t move on to target some other system just because the initial target is well protected
*   **Threat:** Has the potential to inflict serious damage

## Blended (opportunistic and targeted) attacks

Another type of advanced attack is the opportunistic, semi-targeted attack. If criminals want to steal credit card numbers, for example, they may not care whether they successfully steal an equivalent number of active numbers from Best Buy, Walmart, or Barnes & Noble. All that the criminals likely care about is obtaining credit card numbers — from whom the numbers are pilfered isn’t relevant.

At the same time, launching attacks against sites that don’t have credit card data is a waste of the attacker’s time and resources.

# Some Technical Attack Techniques

While it is not necessary for most people to understand the details of how technical cyberattacks exploit system vulnerabilities, it is often interesting for people to understand the basic ideas behind popular methods utilized by hackers. The following sections outline some common ways of breaching and exploiting technical systems.

## Rootkits

Rootkits are software toolsets that allow attackers to perform unauthorized activities at a privileged level on a compromised computer. (“Root” refers to the administrator account on UNIX systems.) Rootkits typically also contain features that seek to ensure that the attacker maintains access while that access remains secret from the authorized user or users of the compromised device.

## Brute-force attacks

Brute-force attacks are simply attacks in which an attacker tries many possible values until the tools the attacker is using guess the correct value. A brute-force attack, for example, might consist of an attacker trying to log in to a user’s account by trying every possible password combination until the attacker (or the attacker’s brute-force attack tool, as the case may be) submits the correct one. Or the attacker may try different decryption keys until successfully decrypting an encrypted message.

## Injection attacks
