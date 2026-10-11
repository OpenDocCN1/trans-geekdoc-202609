
# DARPA Plum Island Grid Cyberattack Simulation

This disaster situation was not, thankfully, what it sounds like. McHann and his fellow engineers weren't fighting off the first-ever cyberattack to trigger a blackout on American soil. Instead, they were in the midst of a disturbingly realistic simulation of that dreaded scenario, defending a custom-built and isolated grid from a "red team" of skilled Department of Defense contract hackers, designed to let his "blue team" feel the pain of a utility-targeted cyberattack without inflicting that pain on American civilian victims.

The Plum Island test grid had been constructed by the Defense Advanced Research Projects Agency, or DARPA, the experimental arm of the Pentagon designed to develop technologies to fight future wars. DARPA is famously credited with inventing the internet and in recent decades helping to develop other world-changing technologies like GPS and unmanned aerial vehicles. On Plum Island, the agency had set out to find the tools that would allow electric utilities to fight off highly sophisticated hackers. And to test them, it had dropped those utilities' engineers into a worst-case scenario: one where they were tasked not with merely keeping the power on but with turning it *back* on after digital adversaries had already blacked out a grid for days.

As the red team hackers dragged his utility back to that blackout state, McHann was discovering just how painful that recovery could be. "Your heart sinks and your stomach falls through the ground," he said, describing the feeling of starting over yet again. "Then you suck it up and get back to work."

---

## Exercise Setup

A few days before McHann had heard those seven shots ring out across Plum Island, DARPA had kicked off its cyberattack war game with an elaborate setup: Two utilities had been assembled on the island with a remote dispatch center and sixteen transmission substations housed in shipping containers dotting the landscape. One utility started the exercise fully dark; in the game's panic-inducing scenario, hackers have turned off the power for long enough—weeks or even months—that all its generators are down and even backup batteries are entirely depleted.

The second utility started the week with one diesel generator connected only to a "critical asset," which the blue team was told it must keep powered at all times. That asset, a crumbling building near the south of Plum Island that was once used by the Pentagon as a laboratory for germ warfare, represented in the world of DARPA's simulation something like a hospital or a defense command center—an imaginary, nonnegotiable consumer of power that's required to save lives or win a war. To allow the participants to see from a distance whether the critical asset was powered or not, a series of inflatable dancing wind-sock figures had been plugged in just outside the building, giving it the look more of a used-car dealership than an imperiled hospital.

The participants, engineers drawn from utilities around the country and cybersecurity researchers who submitted proposals to DARPA, were told they must perform a so-called black start. That meant bootstrapping one blacked-out utility's grid from scratch by spinning up its diesel generator, then building out a path of electrical distribution from both utilities' generators to their substations, and finally syncing the island's two utilities to create a redundant power source for the critical asset.

---

## The Challenge: Untrustworthy Systems

On the first day of the exercise, the utility engineers quickly discovered just how comprehensively they'd have to rethink their approach to running a power grid after it had been fully hijacked by digital saboteurs. Some senior utility operators had begun by telling their teammates that they would restart the grid "by the numbers," McHann said. These engineers believed they could use their remote readings from networked, digital equipment to power up the grid just as they would after any natural disaster. "They were pretty sure it was going to be another hurricane-training scenario," he said drily.

Within twenty-four hours, according to McHann, those naive operators had learned that straightforward approach didn't work when every computer lied to you. The industrial control system software that the utility operators were accustomed to drew its readings of current and voltage from power equipment, displaying them on the dispatch centers' computers known as human-machine interfaces. But that software had now been fully penetrated by the hackers and offered only wildly inaccurate or even deceptive answers.

Worse, the operators soon discovered that not only those remote readings but even the panels on the equipment couldn't be trusted. "They knocked out routers, mucked with the data on screens, tripped breakers, routed power wrong," said McHann of the phantom hackers tormenting them. "You name it, it was coming at us."

The utility defenders tried to push the hackers out of their systems and rebuild them, only to find that the attackers would tenaciously dig their way back in again. "While we were cleaning things up, the adversary was countering our moves," one cybersecurity researcher, Stan Pietrowicz, told my *Wired* colleague Lily Hay Newman, who visited the island during the exercise, in the midst of one of its punishing rainstorms. On the third day, just as the defenders had almost restarted the entire grid, the attackers took down a key substation, throwing them back into chaos. "Even that small victory got taken away from us," Pietrowicz lamented.

---

## Adaptation: Bypassing the Compromised Network

Once the utility engineers conceded to their cybersecurity researcher teammates that their traditional computers were hopeless, they resorted to experimental tools designed to bypass the hacked network. Engineers eventually walked into each substation and connected sensors with clamps directly to power equipment. They connected those sensors with a "mesh" network built from portable computers—black boxes the size of a desktop PC—that talked to one another over encrypted channels protected from the rest of the utility's infections.

Communicating via that encrypted network and with voice commands by phone, the utility operators were finally able to make some progress toward stability. In the very last hours of the weeklong exercise, they finally, briefly synced the two utilities, though there was no guarantee the hackers wouldn't have taken it down again had the game continued.

Meanwhile, the red team had scored a different sort of victory: Twice, they had managed to take down the power to the "critical asset" the blue team had been ordered to protect. On both occasions, the inflatable sock-men had fallen limp on a concrete ramp outside the building, casualties of a conflict against an insidious, highly persistent enemy.

---

## Implications: US vs. Ukraine Grid Resilience

Hearing the experience of DARPA's guinea pigs, I was reminded of something Rob Lee had said to me a year and a half earlier, not long after the second Ukrainian blackout. We'd just met for the first time at the bare-bones Baltimore headquarters of his newly formed start-up, Dragos. Outside the window of his office, appropriately, loomed a series of pylons holding up transmission lines that carried power eighteen miles south to Washington, D.C.

"Taking down the American grid would be harder than Ukraine," Lee had told me at the time. "*Keeping* it down might be easier."

The DARPA exercise seemed to bear out that idea: American utility operators, more than Ukrainians, have learned to manage the generation and flow of power primarily through their computers and automated systems. Without those modern tools, they're blinded. Ukrainian operators, by contrast, are far more accustomed to those tools' failures, and thus ready to fall back on an analog option.
