but this is really only an estimate, as the effects over groups of letters have not been accounted for yet. Rules such as Q being (almost always) followed by U and “I before E, except after C” show there is order in English on the scale of two- and three-character groupings. Entropy approximations based on single letter frequencies are often denoted as $H_1$. Better estimates are given by $H_2$ and $H_3$ where the probabilities used in these are for digraphs and trigraphs. As $N$ grows, $H_N/N$ converges monotonically to a limit (see Table 11.1).

**Table 11.1  First-, Second-, and Third-Order Entropy for Various Languages**

| Language | $H_1$ | $H_2$ | $H_3$ |
|---|---:|---:|---:|
| English |  |  |  |
| &nbsp;&nbsp;&nbsp;Contemporary | 4.03 | 3.32 | 3.1 |
| &nbsp;&nbsp;&nbsp;Poe | 4.100 | 3.337 | 2.62 |
| &nbsp;&nbsp;&nbsp;Shakespeare | 4.106 | 3.308 | 2.55 |
| &nbsp;&nbsp;&nbsp;Chaucer | 4.00 | 3.07 | 2.12 |
| German | 4.08 | 3.18 | – |
| French | 4.00 | 3.14 | – |
| Italian | 3.98 | 3.03 | – |
| Spanish | 3.98 | 3.01 | – |
| Portuguese | 3.91 | 3.11 | – |
| Latin | 4.05 | 3.27 | 2.38 |
| Greek | 4.00 | 3.05 | 2.19 |
| Japanese | 4.809 | 3.633 | – |
| Hawaiian | 3.20 | 2.454 | 1.98 |
| Voynich ms. | 3.66 | 2.22 | 1.86 |

*Source:* Bennett, Jr., William Ralph, *Scientific and Engineering Problem-solving with the Computer*, Prentice Hall, Englewood Cliffs, New Jersey, 1976, p. 140.

As von Neumann indicated, the idea of entropy existed in physics before Claude Shannon applied it to text. To make sense of entropy in physics, one must first understand that imbalances in systems offer usable energy. As an example, consider a hot cup of coffee in a room. It has energy that can be used—one could warm one’s hands over it or use it to melt an ice cube. If left alone, its energy will slowly dissipate with no effect other than slightly warming the room. When the coffee and the room settle to an equilibrium temperature, the room will contain the same amount of total energy, but there will no longer be any useable energy. The amount of entropy or “unusable energy” can be said to have increased.

One of the few theories that scientists have enough confidence in to label a “law” is the second law of thermodynamics. This states that entropy must increase in a closed system; that is, if no energy is being added to a system (i.e., the system is closed), then the amount of energy in the system that cannot be used must increase over time. In other words, the amount of usable energy