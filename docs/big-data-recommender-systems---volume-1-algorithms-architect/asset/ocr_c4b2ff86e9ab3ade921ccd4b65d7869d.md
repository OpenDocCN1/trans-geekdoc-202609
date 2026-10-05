# Private entity resolution for big data on Apache Spark 289

at the beginning of a name will result in a different Soundex code. To overcome this problem, a common solution would be to reverse the words and use Soundex on the resulting strings.

# 13.3.4 The NYSIIS algorithm

As described in [8], NYSIIS, the New York State Identification and Intelligence System phonetic encoding algorithm [4], follows another approach for phonetic encodings. In particular, it maintains information regarding the phonetic of vowels in the encoded word by converting all of them to the letter A.

It provides an encoding consisting exclusively of letters, as a result of a series of transformations:

+   1. The following name prefix conversions take place:
i. "mac" → "mec"
ii. "kn" → "n"
iii. "k" → "c"
iv. { "ph" | "pf"} → "ff"
v. "sch" → "sss"
2. The following name suffix conversions take place:
i. "ce" | "ie" → "y"
ii. "dt" | "rt" | "rd" | "nt" | "nd" → "d"
3. The first character of the resulting string is the first letter of the encoding.
4. The rest of the letters are transformed as follows:
i. "ev" → "af"
ii. "e" | "i" | "o" | "u" → "a"
iii. "q" → "g"
iv. "z" → "s"
v. "m" → "n"
vi. "kn" → "n"
vii. "k" → "c"
viii. "sch" → "sss"
ix. "ph" → "ff"
x. Letter before or after an "h" not a vowel → "h" replaced by letter before
xi. Letter before "u" is a vowel → "w" replaced by "a"
xl. A letter is added to the NYSIIS encoding only if it is different from the previous letter in the encoding
5. If the last letter of the resulting code is "a" or "s," it is removed
6. If the encoding ends with "ay," it is replaced by "y"
7. The final transformation dictates truncating the encoding so as be limited to six characters only.

# 13.3.5 Apache Spark

Apache Spark [5] is an open source, memory-based data-processing framework, suit- for big data. It is considered the next generation big data processing engine,