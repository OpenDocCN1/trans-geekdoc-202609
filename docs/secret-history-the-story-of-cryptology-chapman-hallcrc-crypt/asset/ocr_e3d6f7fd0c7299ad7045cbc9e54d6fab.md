# 1.14 Cryptanalysis of a MASC

Now that we’re seeing ciphers everywhere, it’s time for an example of how they can be broken. Suppose we intercept the following ciphertext.

```
JDS CGWMUJNCQV NSIBVMJCBG QGW CJU ZBGUSHMSGZSU DQIS ASSG Q
WCUQUJSN XBN JDS DMTQG NQZS.
```

We can begin our attack by constructing a frequency table for the ciphertext letters (Table 1.4).

**Table 1.4 Frequency Table for Sample Ciphertext Letters**

| Letter | Frequency | Letter | Frequency |
|---|---:|---|---:|
| A | 1 | N | 5 |
| B | 4 | O | 0 |
| C | 5 | P | 0 |
| D | 4 | Q | 7 |
| E | 0 | R | 0 |
| F | 0 | S | 11 |
| G | 7 | T | 1 |
| H | 1 | U | 6 |
| I | 2 | V | 2 |
| J | 6 | W | 3 |
| K | 0 | X | 1 |
| L | 0 | Y | 0 |
| M | 4 | Z | 3 |

The letter S sticks out as having the largest frequency; therefore, it’s likely that it represents the plaintext letter E. The three letter ciphertext word JDS appears twice. The most common three letter combination (as well as the most common three letter word) is THE. This agrees with our suspicion that S represents E. Is it likely that J represents T? T is very common in English and the ciphertext letter J appears 6 times, so it seems plausible. Writing our guesses above the corresponding ciphertext letters gives:

```
THE         T    E    T         T    E  E E H E  EE
JDS CGWMUJNCQV NSIBVMJCBG QGW CJU ZBGUSHMSGZSU DQIS ASSG Q

       TE        THE H          E.
WCUQUJSN XBN JDS DMTQG NQZS.
```