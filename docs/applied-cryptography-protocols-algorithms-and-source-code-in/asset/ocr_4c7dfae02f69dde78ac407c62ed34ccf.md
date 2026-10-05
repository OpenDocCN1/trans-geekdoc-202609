# 1.4 Simple XOR

substitute "F" for "A," "U" for "B," "L" for "C" and so on. The output pins of one rotor are connected to the input pins of the next.

For example, in a 4-rotor machine the first rotor might substitute "F" for "A," the second might substitute "Y" for "F," the third might substitute "E" for "Y," and the fourth might substitute "C" for "E," would be the output ciphertext. Some of the rotors shift, next time the substitutions will be different.

It is the combination of several rotors and the gears moving them that make the machine secure. Because the rotors move at different rates, the period for an n-rotor machine is 26, furthering cryptanalysis.

The best-known rotor device is the Enigma. The Enigma was used by the Germans during World War II. The idea was invented by Arthur Scherbius and Arvid Gerhard D in Europe. It was patented in the United States by Arthur Scherbius [1383]. The Germans upped the basic design considerably for wartime use, a plugboard that slightly perturbed the plaintext, and a reflecting rotor that caused each rotor to operate on each plaintext twice. First, a team of Polish cryptographers broke the German Enigma and explained their attack to the British. The Germans modified their Enigma as the war progressed. For explanations of how rotor ciphers work and how they were broken, see [794,868,498,446,880,1315,1587,690]. Two fascinating accounts of how the Enigma was broken are [735,796].

# Further Reading

This is not a book about classical cryptography, so I will not dwell further on these subjects. Two excellent precomputer cryptography books are [587,1475]; [448] presents some modern cryptanalysis of cipher machines. Dorothy Denny discusses many of the same ciphers in [456] and [880] has some fairly complex mathematical analysis of the ciphers. Another older cryptography text, which discusses another cryptography, is [99]. An article that presents a good overview of the subject is [579]. David Kahn's historical cryptography books are also excellent [794,795,796].

# 1.4 Simple XOR

XOR is exclusive-or operation: '^' in C or @ in mathematical notation. It’s a standard operation on:

```
0 ⊕ 0 = 0
0 ⊕ 1 = 1
1 ⊕ 0 = 1
1 ⊕ 1 = 0
```

Also note that:

```
a ⊕ a = 0
a ⊕ b ⊕ b = a
```