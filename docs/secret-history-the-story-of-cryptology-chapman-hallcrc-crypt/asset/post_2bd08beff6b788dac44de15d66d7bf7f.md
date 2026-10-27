
successes were only temporary, however. The Japanese would eventually switch over to a more secure machine, *Angooki Taipu B* (type B cipher machine).[^14]

## 8.4 Purple—How It Works

The American cryptanalysts continued their use of colors as code names for the various cipher machines, but by the time Japan introduced *Angooki Taipu B*, the seven colors of the rainbow (Red, Orange, Yellow, Green, Blue, Indigo, Violet)[^15] had all been used. The new machine cipher became known as Purple, which seemed the most appropriate choice at the time, but more colors would soon be needed. Japan’s Purple cipher was a machine, so in this sense it was similar to both Red and Enigma. However, the inner workings of Purple are completely different from both, as you will see. So, how exactly did Purple work? Figure 8.4 will help to clarify the description that follows.

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_294_0.png)

Figure 8.4 Purple schematics.

The characters typed are immediately permuted by a plugboard, which then separates them into two groups of unequal size—the sixes[^16] and the twenties. If a letter is among the sixes, it follows one of 25 paths through S, each of which is a permutation (among these six letters). The paths are cycled through in order (controlled by a telephone switch, *not a rotor*, as in Red and Enigma). The result is then fed through another plugboard to get the output.

If the letter typed does not become one of the sixes, it follows a path through R, M, and L before returning to the plugboard on the left side of the schematic. R, M, and L each contain 25 permutations of the alphabet, but these are not simply cycled through in order; rather, a stepping mechanism determines the rotation. The stepping mechanism takes its cue from S. The details follow, but we first note that R, M, and L will differ in that one will switch slowly, another quickly and the third at an intermediate (medium) value. This is in regards to how long it takes to cycle through all 25 permutations, not the speed of a single switch, which is the same for all. The speeds for the switches are part of the key.

If we label the permutations for S, R, M, and L as 0 through 24, we then have:

- If S is in position 23 and M is in position 24, the slow switch advances.
- If S is in position 24, the medium switch advances.
- In all other cases, the fast switch advances.

The period for Purple is a bit shorter than for the Enigma, which cycled through 16,900 permutations before returning to the first. Purple cycled through 25³ = 15,625. Of course, the sixes for Purple had a much shorter cycle of 25.

As with the Enigma, the plugboard settings were determined in advance and the same for all users on a particular day; however, the Japanese limited themselves to 1,000 different connections (out of a possible 26!; the connections needn’t be reciprocal, as with Enigma).[^17] Like Enigma, part of the Purple key for any given message was to be determined at random and sent as a header along with the ciphertext. This was a five-digit number, selected initially from a list of 120 (later on, the list offered 240 choices), which stood for the initial positions of each switch and the stepping switch. There was no mathematical relation between the five-digit number and the setting it stood for. It was simply a code number. For example, 13579 meant the sixes switch starts at position 3 and the twenties switches start at positions 24, 8, and 25, while the 20-switch motion (assignment of speeds slow, medium, and fast to particular switches) is 3-2-1.[^18] Of the 120 five-digit codes, half consisted only of odd digits and half only of even digits. It was a great mistake for the Japanese to artificially restrict themselves to this tiny fraction of the initial settings. With 25 possible settings for each of the twenties and the sixes, we have 25⁴ = 390,625 possibilities.

The Japanese did make some wise choices in how Purple was used. The first was enciphering the five-digit key using an additive. Thus, messages using the same key would not bear identical indicators. Another good decision was encoding messages, prior to running them through Purple, but they did this with the commercially available Phillips Code—not the best choice![^19]

Because a large keyspace is essential for security, we should address the overall keyspace for Purple. A variety of values may be given, depending on how we perform the calculation. Determining the keyspace of Purple requires that several subjective choices be made; for example, should one use all possible plugboard configurations as a factor, or limit it to the 1,000 that were actually used? Should all possible initial positions of the switches be considered or only the 120 (later 240) the Japanese allowed? Should we count all possible internal wirings? The cryptanalysts had to determine these, but the Japanese couldn’t change them once the machines were assembled, so one could say they weren’t part of the key. Thus, it’s not surprising that a range of values for the keyspace can be found in the literature. Stephen J. Kelley offers a figure of 1.8 × 10¹³⁸, which is much larger than for the three-rotor Enigma.[^20] Mark Stamp, more conservative in assigning values to various factors, came up with 2¹⁹⁸ ≈ 4 × 10⁵⁹ as the keyspace.[^21] Quite a difference! However, even this lower value was sufficiently large to avoid a brute force attack. So, the keyspace was definitely large enough. This was not why Purple ultimately proved insecure.

## 8.5 Purple Cryptanalysis

As with many classical ciphers, a frequency analysis of Purple ciphertexts provides useful information to get the cryptanalysis started. The six letters that are separated from the rest will each have a frequency about equal to the average of that group, because, over the course of the 25 substitutions, each letter is about equally likely to be replaced by any letter in the sixes. In the same manner, every letter in the group of twenty will be substituted for, on average, equally often by each letter in the twenties. Thus, every letter in this group will also have about the same frequency in the ciphertext.

As an experiment, I placed one Scrabble tile for each letter in a container, shook it, and then selected six. The six, in alphabetical order were A, E, J, L, V, and Z; thus, the set happened to contain both the most frequent and the rarest English letters. According to the frequency table from Section 1.9, the average frequency of the letters in this group is 4.3666. For the remaining 20 letters, the average frequency is 3.7, for a difference of 0.666.

This is how we distinguish the sixes from the twenties. After calculating the frequencies, we either split off the six most frequent or the six least frequent letters to be the sixes (whichever set seems to stand out most strongly from the other frequencies) and assume these are, in fact, the sixes. The remaining letters should be the twenties.

Rowlett’s team had the advantage of having broken Red prior to attacking Purple, so the 6-20 split was familiar. The sixes being easier, with a period of only 25, were recovered first. The twenties were more difficult, but a number of factors worked to the cryptanalysts’ advantage.

Switching from Red to Purple was a good move for the Japanese, but they made the move in the worst possible way—slowly! Ideally, there would be an abrupt change, with everyone shifting to the new cipher at, for example, the stroke of midnight on a particular date. The slow change made by the Japanese over many months meant that many messages sent out in Purple were also sent out in Red to locations that hadn’t yet made the transition. Because Red was already broken, this allowed the cryptanalysts to compare those plaintexts with the corresponding ciphertexts in the Purple system. In other words, they had cribs in abundance! Messages that weren’t also sent in Red were cribbed with stereotyped phrases and the numbering of messages used by the Japanese. Finally, the Japanese sometimes sent enciphered copies of U.S. State Department communiqués for which the cryptanalysts had no trouble obtaining plaintexts.[^22]

Leo Rosen, an electrical engineering major from the Massachusetts Institute of Technology (MIT) and part of the cryptanalytic team, made an important discovery in September 1939. While looking at an electrical supply catalog, he recognized that telephone stepping switches could have been used to accomplish the substitutions. There was no commercially available cipher machine that worked in this manner, so it was not an obvious solution!

Even with Rosen’s insight and the help inadvertently supplied by the Japanese, recovering the twenties with their large period of 25³ = 15,625 would have been difficult; however, Genevieve Grotjan recognized that there was a relationship to be found at shorter intervals of just 25 letters. Some illustrations of reconstructed substitution alphabets make her finding clearer.

[^14]: Also known as 97-*shiki-obun In-ji-ki*, which translates to “alphabetical typewriter 97.” The 97 refers to the year it was first developed, 2597 by the Japanese reckoning, 1937 for the Americans.

[^15]: Of course, this division of the rainbow into seven colors is arbitrary. That particular value was chosen by Isaac Newton to create a nice symmetry with the seven-note musical scale (A, B, C, D, E, F, G).

[^16]: Unlike Red, the sixes in Purple weren’t necessarily vowels; they could be any six letters and they changed daily. Actually, this innovation was one of the changes made in Red usage before its demise.

[^17]: Smith, Michael, The Emperor's Codes: The Breaking of Japan's Secret Ciphers, Penguin Books, New York, 2002, p. 68.

[^18]: Freeman, Wes, Geoff Sullivan, and Frode Weierud, “Purple Revealed: Simulation and Computer-Aided Cryptanalysis of Angooki Taipu B,” Cryptologia, Vol. 27, No. 1, January 2003, pp. 1–43, p. 38 cited here.

[^19]: Smith, Michael, The Emperor's Codes: The Breaking of Japan's Secret Ciphers, Penguin Books, New York, 2002, p. 68.

[^20]: Kelley, Stephen J., Big Machines, Aegean Park Press, Laguna Hills, California, 2001, p. 178.

[^21]: Stamp, Mark and Richard M. Low, Applied Cryptanalysis: Breaking Ciphers in the Real World, John Wiley & Sons, Hoboken, New Jersey, 2007, pp. 44–45.

[^22]: Smith, Michael, *The Emperor’s Codes: The Breaking of Japan’s Secret Ciphers*, Penguin Books, New York, 2002, pp. 70–71.
