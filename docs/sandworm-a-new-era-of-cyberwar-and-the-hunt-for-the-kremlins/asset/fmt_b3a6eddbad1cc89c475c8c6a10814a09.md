
The fifty-six-second clip showed a cursor moving around the screen of one of the computers in the company's control room. The pointer glides to the icon for one of the breakers and clicks a command to open it. The video pans from the computer's Samsung monitor to its mouse, which hasn't budged. Then it shows the cursor moving again, seemingly of its own accord, hovering over a breaker and attempting again to cut its flow of power as the engineers in the room ask one another who's controlling it.

The hackers hadn't sent their blackout commands from automated malware, or even a cloned machine, as they'd done at Kyivoblenergo. Instead, they'd exploited the company's IT help-desk tool to take direct control of the mouse movements of the stations' operators. They'd locked the operators out of their own user interface. And before their eyes, phantom hands had clicked through dozens of breakers—each serving power to a different swath of the region—and one by one by one, turned them cold.

# PART II: ORIGINS

> Once men turned their thinking over to machines in the hope that this would set them free. But that only permitted other men with machines to enslave them.

# Chapter 10: FLASHBACK: AURORA

Nine years before his Ukraine trip, on a piercingly cold and windy morning in March 2007, Mike Assante arrived at an Idaho National Laboratory facility thirty-two miles west of Idaho Falls, a building in the middle of a vast, high desert landscape covered with snow and sagebrush. He walked into an auditorium inside the visitors' center, where a small crowd was gathering. The group included officials from the Department of Homeland Security, the Department of Energy, and the North American Electric Reliability Corporation (NERC), executives from a handful of electric utilities across the country, and other researchers and engineers who, like Assante, were tasked by the national lab to spend their days imagining catastrophic threats to American critical infrastructure.

At the front of the room was an array of video monitors and data feeds, set up to face the room's stadium seating, like mission control at a rocket launch. The screens showed live footage from several angles of a massive diesel generator. The machine was the size of a school bus, a mint green, gargantuan mass of steel weighing twenty-seven tons, about as much as an M3 Bradley tank. It sat a mile away from its audience in an electrical substation, producing enough electricity to power a hospital or a navy ship and emitting a steady roar. Waves of heat coming off its surface rippled the horizon in the video feed's image.

Assante and his fellow INL researchers had bought the generator for $300,000 from an oil field in Alaska. They'd shipped it thousands of miles to the Idaho test site, an 890-square-mile piece of land where the national lab maintained a sizable power grid for testing purposes, complete with sixty-one miles of transmission lines and seven electrical substations.

Now, if Assante had done his job properly, they were going to destroy it. And the assembled researchers planned to kill that very expensive and resilient piece of machinery not with any physical tool or weapon but with about 140 kilobytes of data, a file smaller than the average cat GIF shared today on Twitter.

***

Three years earlier, Assante had been the chief security officer at American Electric Power, a utility with millions of customers in eleven states from Texas to Kentucky. A former navy officer turned cybersecurity engineer, Assante had long been keenly aware of the potential for hackers to attack the power grid. But he was dismayed to see that most of his peers in the electric utility industry had a relatively simplistic view of that still-theoretical and distant threat. If hackers did somehow get deep enough into a utility's network to start opening circuit breakers, the industry's common wisdom at the time was that staff could simply kick the intruders out of the network and flip the power back on. "We could manage it like a storm," Assante remembers his colleagues saying. "The way it was imagined, it would be like an outage and we'd recover from the outage, and that was the limit of thinking around the risk model."

But Assante, who had a rare level of crossover expertise between the architecture of power grids and computer security, was nagged by a more devious thought. What if attackers didn't merely hijack the control systems of grid operators to flip switches and cause short-term blackouts, but instead reprogrammed the automated elements of the grid, components that made their own decisions about grid operations without checking with any human?

In particular, Assante had been thinking about a piece of equipment called a protective relay. Protective relays are designed to function as a safety mechanism to guard against dangerous physical conditions in electric systems. If lines overheat or a generator goes out of sync, it's those protective relays that detect the anomaly and open a circuit breaker, disconnecting the trouble spot, saving precious hardware, even preventing fires. A protective relay functions as a kind of lifeguard for the grid.

But what if that protective relay could be paralyzed—or worse, corrupted so that it became the vehicle for an attacker's payload?

That disturbing question was one Assante had carried over to Idaho National Laboratory from his time at the electric utility. Now, in the visitor center of the lab's test range, he and his fellow engineers were about to put his most malicious idea into practice. The secret experiment was given a code name that would come to be synonymous with the potential for digital attacks to inflict physical consequences: Aurora.

***

The test director read out the time: 11:33 a.m. He checked with a safety engineer that the area around the lab's diesel generator was clear of bystanders. Then he sent a go-ahead to one of the cybersecurity researchers at the national lab's office in Idaho Falls to begin the attack. Like any real digital sabotage, this one would be performed from miles away, over the internet. The test's simulated hacker responded by pushing roughly thirty lines of code from his machine to the protective relay connected to the bus-sized diesel generator.

The inside of that generator, until that exact moment of its sabotage, had been performing a kind of invisible, perfectly harmonized dance with the electric grid to which it was connected. Diesel fuel in its chambers was aerosolized and detonated with inhuman timing to move pistons that rotated a steel rod inside the generator's engine—the full assembly was known as the "prime mover"—roughly 600 times a minute. That rotation was carried through a rubber grommet, designed to reduce any vibration, and then into the electricity-generating components: a rod with arms wrapped in copper wiring, housed between two massive magnets so that each rotation induced electrical current in the wires. Spin that mass of wound copper fast enough, and it produced 60 hertz of alternating current, feeding its power into the vastly larger grid to which it was connected.

A protective relay attached to that generator was designed to prevent it from connecting to the rest of the power system without first syncing to that exact rhythm: 60 hertz. But Assante's hacker in Idaho Falls had just reprogrammed that safeguard device, flipping its logic on its head.

At 11:33 a.m. and 23 seconds, the protective relay observed that the generator was perfectly synced. But then its corrupted brain did the opposite of what it was meant to do: It opened a circuit breaker to disconnect the machine.
