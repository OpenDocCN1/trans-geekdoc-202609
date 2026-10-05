
# CHAPTER 1 Foundations

A running-key cipher—sometimes called a book cipher—in which one text is used to encrypt another text, another example of this sort of cipher. Even though this cipher has a period of the text, it can also be broken easily [576,794].

# Transposition Ciphers

In a transposition cipher the plaintext remains the same, but the order of characters is shuffled around. In a simple columnar transposition cipher, the plaintext is written horizontally onto a piece of paper of fixed width and the ciphertext is read off vertically (see Figure 1.4). Decryption is a matter of writing the ciphertext vertically onto a piece of paper of identical width and reading the plaintext horizontally.

The German ADFGVX, used during World War I, is a transposition cipher combined with a simple substitution. It was a very complex algorithm for its day but was broken by Georges Painvin, a French cryptanalyst [794].

Many modern algorithms use transposition, it is troublesome because it requires a lot of memory and sometimes requires messages to be only certain lengths. Substitution is far more common.

# Rotor Machines

In the 1920s, various mechanical encryption devices were invented to automate the process of encryption. Most were based on the concept of a rotor, a mechanical wheel wired to perform a general substitution.

A rotor machine has a keyboard and series of rotors, and implements a version of the Vigenère cipher. Each rotor is an arbitrary permutation of the alphabet, has 26 positions, and performs a simple substitution. For example, a rotor might be wired

```
Plaintext: COMPUTERICS MAY BE SLOW AT LEAST EXPENSIVE

COMPUTERGR
APHCISMAYB
ESLOWBUTAT
LEASTITSEX
PENSIVE

Ciphertext: CAELP OPSEE MHLAN PIOSSUCWTI SBIVEMUTE RATSY YAERB TX
```

Figure 1.4 Columnar transposition cipher.

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

# 14 CHAPTER Foundations

The simple-XOR algorithm is really an embarrassment, it's nothing more than a Vigenère polyalphabetic cipher. It's here only because of its prevalence in commercial software packages, at least in the MS-DOS and Macintosh worlds [1502,1387]. Unfortunately, if a software security program claims that it has a "proprietary" encryption algorithm—significantly faster than DES—the odds that it is some variant of it.

```
* Usage: crypto key input_file output_file */
void main( int argc, char *argv[]) {
    FILE *fi, *fo;
    char *cp;
    int c;
    if ((cp = argv[1]) && *cp!='\0') {
        if ((fi = fopen(argv[2], "rb")) != NULL) {
            if ((fo = fopen(argv[3], "wb")) != NULL) {
                while ((c = getc(fi)) != EOF) {
                    c ^= *cp;
                    cp++;
                }
                putc(c,fo);
                fclose(fo);
            }
            fclose(fi);
        }
    }
}
```

This is a symmetric algorithm. The plaintext is XOREd with a keyword to generate the ciphertext. Since XORing the same value restores the original, encryption and decryption use exactly the same program:

P @ K = C
C @ K = P

There's no real security here. This kind of encryption is trivial to break, without computers [587,1475]. It will take a few seconds with a computer. Assume the plaintext is English. Furthermore, assume the key length is any small number of bytes. Here's how to break it:

+   1. Discover the length of the key by a procedure known as counting coincidences [577]. XOR the ciphertext against it-shifted various numbers of bytes, and count those bytes that are equal. If the displacement is a multiple of the key length, then something over 6 percent of the bytes will be equal. If it is not, then less than 0.4 percent will be equal (assuming a random key encrypting normal ASCII text; other plaintext will have different numbers). This is the index of coincidence. The smallest displacement that indicates a multiple of the key length is the length of the key.

2. Shift the ciphertext by that length and XOR it with itself. This removes the key and leaves you with plaintext XORed with the plaintext. Since English has 1 bits of real information per byte [see Section 11.1], there is plenty of redundancy for determining a unique decryption.

Despite this, the long list of software vendors that tout this algorithm as "almost as secure as DES" is staggering [1387]. It is the algorithm (with a 160-bit repeated "key") that NASA finally allowed the U.S. digital phones to use for voice.

# 1.5 One-Time PADS

Believe it or not, there is a perfect encryption scheme. It's called a one-time pad, and was invented in 1917 by Major Mauborg and AT&T's Gilbert Vernam [794]. (Actually, a one-time pad is a special case of a threshold scheme; see Section 3.7) A one-time pad is nothing more than a large nonrepeating set of random key letters, written on sheets of paper and glued together in a pad. In its original form, it was a one-time tape for telewriters. The sender uses each key letter on the pad to encrypt exactly one plaintext character. Encryption is the addition modulo 26 of the plaintext character and the one-time pad key character.

Each letter is used exactly once, for only one message. The sender encrypts the message and destroys the used pages of the pad or used section of the tape. The receiver has an identical pad and uses each key on the pad, in turn, to decrypt each letter of the ciphertext. The receiver destroys the same pad pages or tape section after decrypting the message. New message—new key letters. For example, if the message is:

```
ONETEPAD
```

and the key sequence from the pad is

```
TBFRGFARM
```

then the ciphertext is

because

```
O + T mod 26 = I
N + B mod 26 = P
E + F mod 26 = K
```

etc.
