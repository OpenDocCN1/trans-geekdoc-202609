
discouraging, we can start over and assume the key length is 10. Splitting the ciphertext letters into ten groups and computing the IC for each will show if this assumption is better or not. The smaller groups of ciphertext letters, for which these computations are done, are referred to as *decimated alphabets*, even if there aren’t exactly ten of them.

A few examples will indicate how reliable the Kasiski and IC tests are. The first is presented below and others are left as exercises. *Caution:* Some books concoct examples where such tests work perfectly, creating the false impression that this is always the case.

The IC equation can be turned around to give the length (*L*) of the key, when the number of characters (*N*) in the ciphertext and the ciphertext index of coincidence (*IC*) are known:

$$L \approx \frac{0.028N}{(IC)(N-1)-0.038N+0.066}$$

Although you needn’t understand the derivation of the formula above in order to use it, it’s easy to demonstrate. Suppose we have a ciphertext consisting of *N* letters and that the enciphering key has length *L*. If we randomly pick two letters, what is the probability that they are the same (As *ciphertext*—the plaintext letters they represent needn’t match)? The probability that the two letters match is much higher if they were both enciphered with the same alphabet, so we consider two separate cases and combine them for our final answer.

## Case 1: The Two Letters Arose from the Same Cipher Alphabet

It doesn’t matter which letter we pick first, but the second letter has to come from the same alphabet, so it must be one of the remaining (*N/L*) − 1 letters of this type (The *L* alphabets will roughly divide the *N* letters of the text into groups of size *N/L*, each enciphered differently). Thus, there are (*N/L*) − 1 choices left out of the total remaining *N* − 1 letters. So the probability is

$$\frac{\left(\frac{N}{L}\right)-1}{N-1}.$$

But we also want the two letters to be the same. Because we are already within the same alphabet, this probability is simply 0.066, the value of the IC for one alphabet. We multiply these two values together to get

$$\frac{\left(\frac{N}{L}-1\right)(0.066)}{N-1}.$$

## Case 2: The Two Letters Arose from Different Cipher Alphabets

As with case 1, it doesn’t matter which letter we pick first, but now the second letter must come from a different alphabet. Because we already found the probability the second letter came from the same alphabet, we can take the complement to get the probability it came from a different alphabet. We have

$1-\left(\frac{\frac{N}{L}-1}{N-1}\right).$

Now that we have two letters from different alphabets, we need to multiply by the probability that they match. This is simply the IC value for random text (or, equivalently, a large number of alphabets), namely 0.038. So, our probability for case 2 is

$\left(1-\frac{\frac{N}{L}-1}{N-1}\right)(0.038).$

Combining the two cases, we have

$IC \approx \frac{\left(\frac{N}{L}-1\right)(0.066)}{N-1}+\left(1-\frac{\frac{N}{L}-1}{N-1}\right)(0.038).$

It’s now just a matter of doing the algebra to solve for $L$ (see Exercise 23) and obtain the result.

$L \approx \frac{0.028N}{(IC)(N-1)-0.038N+0.066}$

Using this equation, you don’t need a table of values like the one given above; however, this version of the equation is only intended for ciphers having English plaintexts. For other languages, the constants may vary.

The Kasiski test and the index of coincidence may sound complicated at first, but they are very easy to use. Take a look at the following example to see how simple they make the task of Vigenère cipher cryptanalysis.

## Example

```
IZPHY XLZZP SCULA TLNQV FEDEP QYOEB SMMOA AVTSZ VQATL LTZSZ
AKXHO OIZPS MBLLV PZCNE EDBTQ DLMFZ ZFTVZ LHLVP MBUMA VMMXG
FHFEP QFFVX OQTUR SRGDP IFMBU EIGMR AFVOE CBTQF VYOCM FTSCH
ROOAP GVGTS QYRCI MHQZA YHY XG LZPQB FYEOM ZFCKB LWB TQ UIHUY
LRDCD PHPVO QVVPA DBMWS ELOSM PDCMX OFBFT SDTNL VPTSG EANMP
MHKAE PIEFC WMHPO MDRVG OMPQ BTAEC CNUAJ TNOIR XODBN RAIAF
UPHTK TFIIG EOMHQ FPPAJ BAWSV ITSMI MMFYT SMFDS VHF WQ RQ
```

Several character groups repeat. We need to note their positions to make use of the Kasiski test.

| Character Grouping | Starting Positions | Difference Between Starting Positions |
|---------------------|---------------------|----------------------------------------|
| IZP | 1 and 57 | 56 |
| HYX | 4 and 172 | 168 |
| EPQ | 24 and 104 | 80 |
| MBU | 91 and 123 | 32 |
| TSM | 327 and 335 | 8 |

Consider the last column of the table above. All of the values are multiples of 8. This suggests that the key is of length 8. It's possible that the key length is 4 (or 2), but if this were the case, it's likely that one of the numbers in the difference column would be a multiple of 4 (or 2) but not a multiple of 8.

Calculating the index of coincidence requires more work. We begin by constructing a frequency table (Table 2.1) for the ciphertext letters.

The numerator of the index of coincidence for this example is then given by

## Table 2.1 Frequency Table Used to Calculate Index of Coincidence

| Letter | Frequency | Letter | Frequency |
|---|---|---|---|
| A | 18 | N | 7 |
| B | 14 | O | 18 |
| C | 12 | P | 22 |
| D | 12 | Q | 17 |
| E | 15 | R | 10 |
| F | 22 | S | 16 |
| G | 9 | T | 20 |
| H | 14 | U | 8 |
| I | 13 | V | 18 |
| J | 2 | W | 5 |
| K | 4 | X | 7 |
| L | 15 | Y | 9 |
| M | 26 | Z | 14 |

∑_{i=A}^{Z} F_i(F_i - 1) = (18)(17) + (14)(13) + (12)(11) + (12)(11) + (15)(14) + (22)(21) + (9)(8) + (14)(13) + (13)(12) + (2)(1) + (4)(3) + (15)(14) + (26)(25) + (7)(6) + (18)(17) + (22)(21) + (17)(16) + (10)(9) + (16)(15) + (20)(19) + (8)(7) + (18)(17) + (5)(4) + (7)(6) + (9)(8) + (14)(13) = 5178

The index of coincidence is then

IC = Σ_{i=A}^{Z} F_i(F_i − 1) / N(N − 1) = 5178 / (347)(346) ≈ 0.0431.

This value, although not matching an expected value perfectly, suggests that five or six alphabets were used. We can assume the key is of length 5, split the ciphertext letters into groups that would have been enciphered with the same alphabet, and perform the IC calculation for each group. We get the values 0.046, 0.050, 0.041, 0.038, and 0.046. These values are far below 0.066, so it's very unlikely that they are really from the same alphabet. Our assumption that the key is of length 5 must be wrong. Repeating these calculations based on a key of length 6 gives the values 0.050, 0.041, 0.035, 0.048, 0.038, and 0.037. Again, it seems that the key cannot be of this length.

We could try again with four alphabets and then with seven, before moving on to values further from the ones suggested by the IC, but the Kasiski test suggested eight, so let's skip ahead to this value. Splitting the ciphertext into eight separate groups and calculating the IC for each gives 0.105, 0.087, 0.075, 0.087, 0.056, 0.069, 0.065, and 0.046. These values are by far the largest, so we have another test backing up the results of the Kasiski test. Another way in which an IC calculation can be used to support the result of the Kasiski test is described in Exercise 22.

We now rewrite the ciphertext in blocks of length 8, so that characters in the same column represent letters enciphered by the same alphabet. We may construct a frequency table for each column (Table 2.2). This had to be done to get the values for the IC given in the paragraph above, but I left out showing the work until it could be seen to lead to a positive conclusion. Take a moment to examine Table 2.2 and the accompanying text before returning here.

For each column, there are 26 possible choices for which letter represents E. In column 1, the maximum value for the sum of the frequencies of E, A, and T is 21 and is obtained when M represents E. Now for column 2, assuming that P represents E yields a sum of only 9. The greatest sum is 11, which is obtained when Q represents E. For column 3, the maximum sum is also obtained when Q represents E. This time the sum is 17. For columns 4 through 8, this technique suggests E is represented by S, V, X, E, and P, respectively. We see that, if these substitutions are correct, E is only the most frequent character in columns 1, 3, 4, and 5, while it is tied for first place in column 7. You are encouraged to investigate other techniques for determining the shift of each alphabet in Exercise 14. The substitutions above imply the keyword (the letters representing A in each alphabet strung together in order) is IMMORTAL. Since this is a real word, we gain some confidence in our solution. Applying this keyword to the ciphertext by subtracting modulo 26 gives:

```
IZPHY XLZZP SCULA TLNQV FEDEP QYOEB SMMOA AVTSZ VQATL LTZSZ
IMMOR TALIM MORTA LIMMO RTALI MMORT ALIMM ORTAL IMMOR TALIM
ANDTH ELORD GODSA IDBEH OLDTH EMANI SBECO NEASO NEOFU STOKN
AKXHO OIZPS MBLLV PZCNE EDBTQ DLMFZ ZFTVZ LHLVP MBUMA VMMXG
MORTA LIMMO RTALI MMORT ALIMM ORTAL IMMOR TALIM MORTA LIMMO
OWGOO DANDE VILAN DNOWL ESTHE PUTFO RTHHI SHAND ANDTA KEALS
FHFEP QFFVX OQTUR SRGDP IFMBU EIGMR AFVOE CBTQF VYOCM FTSCH
RTALI MMORT ALIMM ORTAL IMMOR TALIM MORTA LIMMO RTALI MMORT
OOFTH ETREE OFLIF EANDE ATAND LIVEF OREVE RTHER EFORE THELO
ROOAP GVGTS QYRCI MHQZA YHY XG LZPQB FYEOM ZFCKB LWB TQ UIHUY
ALIMM ORTAL IMMOR TALIM MORTA LIMMO RTALI MMORT ALIMM ORTAL
RDGOD SENTH IMF OR THFRO M THEG ARDEN OFEDE NTOTI LLTHE GROUN
LRDCD PHPVO QVVPA DBMWS ELOSM PDCMX OFBFT SDTNL VPTSG EANMP
```
