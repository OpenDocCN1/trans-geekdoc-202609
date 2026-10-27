

### Table 2.9 Finding **STAGE** in the Second Block

```text
L A E K A H B W A G W I P T U K V S G B
E H A R H O I E H N E E E A H R E E N I
H T E T T T S T T S E L T N T R O T T
S I N D I D N I I O I A H I D D I A O N
T S R H S E O O S S O I I L R H N S S O
A A L E A A H D A C D O T E A E H H C H
L A T G A H U T A E T U W P U G O L E U
D E I S E N A A E A A R C F C S D F A A
I W W S W U B W W G W R N O S S S N G B
R N M C N P D F N I F P A C I C C B I D
U N S I N S Y R N Y R T P R M I T R Y Y

H T E T T T S T T S E L T N T R O T T
E H A R H O I E H N E E E A H R E E N I
T S R H S E O O S S O I I L R H N S S O
S I N D I D N I I O I A H I D D I A O N
L A T G A H U T A E T U W P U G O L E U
A A L E A A H D A C D O T E A E H H C H
I W W S W U B W W G W R N O S S S N G B
D E I S E N A A E A A R C F C S D F A A
U N S I N S Y R N Y R T P R M I T R Y Y
R N M C N P D F N I F P A C I C C B I D
```

### Table 2.10 Working from **THE TH** in the First Block and **START** in the Second Block

```text
L A E K A H B W A G W I P T U K V S G B
E H A R H O I E H N E E E A H R E E N I
H T E T T T S T T S E L T N T R O T T
S I N D I D N I I O I A H I D D I A O N
T S R H S E O O S S O I I L R H N S S O
A A L E A A H D A C D O T E A E H H C H
L A T G A H U T A E T U W P U G O L E U
D E I S E N A A E A A R C F C S D F A A
I W W S W U B W W G W R N O S S S N G B
R N M C N P D F N I F P A C I C C B I D
U N S I N S Y R N Y R T P R M I T R Y Y

H T E T T T S T T S E L T N T R O T T
E H A R H O I E H N E E E A H R E E N I
T S R H S E O O S S O I I L R H N S S O
S I N D I D N I I O I A H I D D I A O N
L A T G A H U T A E T U W P U G O L E U
A A L E A A H D A C D O T E A E H H C H
I W W S W U B W W G W R N O S S S N G B
D E I S E N A A E A A R C F C S D F A A
U N S I N S Y R N Y R T P R M I T R Y Y
R N M C N P D F N I F P A C I C C B I D
```

with (in the top rectangle) the Y it must combine with to yield the ciphertext letter T (Table 2.11). We can always add letters in this manner, but really shouldn't unless we are either fairly confident that they are correct or have no other reasonable options.

### Table 2.11 Adding Y and K as Needed

Two rectangular letter grids with underlined letters Y and K indicating the positions used for the cipher analysis.

Our two texts now read START THE ATTACK and THE THOUSAND INJ... Once more, please take a moment to look for the continuation of INJ in the top rectangle (to see that it's not so hard to do) before reading on.

Of course, one could proceed in a different direction by trying to extend START THE ATTACK. In general though, it's easier to complete partial words than to find new ones, unless the preceding words are the beginning of a well-known phrase. Speaking of which, there will likely be a reader who has already recognized the source of the key being used here. More in a moment.

Okay, did you extend the top text to THE THOUSAND INJURIES? This makes the bottom text read START THE ATTACK AT NOO. Looking at the bottom text one last time, we extend it by another letter and then do the same in the top rectangle.

We now have the message and the key:

```
THE THOUSAND INJURIES O    key
START THE ATTACK AT NOON    message
```

The key was, by the way, the beginning of Edgar Allan Poe's short story “The Cask of Amontillado.”

The example chosen above to illustrate this attack was a little easier than usual. Nine times out of twenty (45%), the pair of letters most likely to yield a particular ciphertext letter did yield that letter. Experiments reveal that this happens less than a third of the time on average. Also, the example only had one ciphertext letter (5% of the cipher) that didn’t arise from one of the five most likely pairings. This was a lower percent than usual.

Nevertheless, this is a great attack. Friedman made the attack even quicker by cutting out the columns. This allowed him to move individual columns up and down. When he got a word or phrase going across letters from the top rectangle, he could glance down at the bottom rectangle and also read the corresponding letters there straight across. I used bold text and underlining, because it is easier to present it this way in a book, but the sliding paper works better for classroom demonstrations.

Although Friedman didn’t pursue it further, his attack can be expanded. Instead of taking the ciphertext characters one at a time, groups may be considered. For example, suppose the ciphertext begins MOI. Our tables suggest

- M is most likely E + I.
- O is most likely A + O.
- I is most likely E + E.

But these tables don’t take context into consideration. The top pairing suggested for O doesn’t consider what letters appear before or after it in the ciphertext. Taking the letters MOI as group and using trigraph frequencies to rank the possibilities, we see it is most likely to arise from THE + THE.

Christian N.S. Tate, an undergraduate at the time, and I investigated this new attack. We split the ciphertext into groups of characters and used frequencies for letter combinations of the group size to rank our pairings. For example, if the ciphertext was HYDSPLTGQ, and we were using groups of three characters to launch our attack, we’d split the ciphertext up as HYD SPL TGQ and replace each trigram with the pair most likely to yield it.

The idea needed to be tested and the easiest way to do this was to write computer programs to carry out the calculations and analyze the results. We tested single character analysis (as Friedman had), digraphs, trigraphs, tetragraphs, pentagraphs, and hexagraphs.

I expected that after the results were in, I could compare the new attack to Friedman’s and say, “It is a far far better thing I have done.” However, this was not the case. The results were only marginally better! We tried to place the results in the best light possible for the write-up. Figuring even the slightest improvement on Friedman’s work ought to be worth publishing, we submitted the paper. A kind editor accepted it following some revising.

Fortunately, Alexander Griffing, a student in the Bioinformatics Ph.D. program at North Carolina State University, saw the paper and was able to turn the attack into something truly successful. He did this by not just taking the blocks of ciphertext characters one after the other, but by also considering their overlap when computing the most likely solution.25 So, when considering the ciphertext HYDSPLTGQ, Griffing’s method didn’t just look at how HYD, SPL, and TGQ could arise, but rather HYD, YDS, DSP, SPL, PLT, LTG, and TGQ. A graph reproduced from his paper is provided in Figure 2.15. It shows how his method is better than the method Tate and I proposed for every size letter group considered, and dramatically better when pentagraphs and hexagraphs are used.

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_118_0.png)

Figure 2.15 Griffing’s results (solid line) compared to an earlier attempt by others (dotted line).

With the techniques discussed in this chapter, running key ciphers of any length can be broken; however, extremely short messages are not likely to have unique solutions. The graph in Figure 2.16 shows how the number of potential solutions changes as a function of the message’s length. Beyond eight characters, we expect only a single solution.

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_118_1.png)

Figure 2.16 Number of spurious decipherments as a function of the message size. (From Deavours, Cipher A., “Unicity Points in Cryptanalysis,” Cryptologia, Vol. 1, No. 1, January 1977, pp. 46-68, p. 62 cited here.)

## 2.7 The One-Time Pad or Vernam Cipher

The Vigenère cipher was seen to be easily broken due to a weakness caused by the keyword repeating. Modifying the system so that the key never repeats gives us the running key cipher. Although the new system can’t be defeated by the attacks that succeeded against the Vigenère cipher, there are other attacks that work, as we saw. The weakness this time was that both the key and the message are made up of meaningful words. Thus, the next step for those who seek to make ciphers secure seems obvious—use a running key that consists of letters chosen randomly. Such a system resists

