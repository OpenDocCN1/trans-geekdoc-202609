
From a declassified NSA history, we have the following.^30^

In 1973 NBS solicited private industry for a data encryption standard (DES). The first offerings were disappointing, so NSA began working on its own algorithm. Then Howard Rosenblum, deputy director for research and engineering discovered that Walter Tuchman of IBM was working on a modification to Lucifer for general use. NSA gave Tuchman a clearance and brought him in to work jointly with the Agency on Lucifer modification.^31^

NSA worked closely with IBM to strengthen the algorithm against all except brute force attacks and to strengthen substitution tables, called *S*-boxes. Conversely, NSA tried to convince IBM to reduce the length of the key from 64 to 48 bits. Ultimately, they compromised on a 56-bit key.^32^

Though its export was restricted, it was known to be widely used outside the United States. According to a March 1994 study, there were some 1,952 products developed and distributed in thirty-three countries.^33^

## 13.2.2 Objection 2: *S*-Box Secrecy

Cryptologists also expressed concern over the secret manner in which the *S*-boxes were designed and suggested that either this should be revealed or new *S*-boxes should be created in an open manner.^34^ At the second NBS workshop, an IBM representative said the S-boxes were constructed to *increase* security. Morris, Sloane, and Wyner commented, “While there is no particular reason to doubt this, some doubt remains.”^35^ Some regularities in the S-box structure were described in a Lexar Corporation report.^36^

Pointing out that DES had already been proposed for being used as a one-way function to verify computer log-ons and for sending keys over insecure channels, Morris et al. continued, “It is clear that once the DES is approved as a standard, it will find applications in every part of the communications, data processing, and banking industries, by the police and the medical and legal professions, as well as being widely used by the Federal agencies for which it was officially designed.” They were right:

DES quickly took over the encryption market, becoming the code provided by 99 percent of the companies selling equipment.^37^

Even the Moscow-based Askri company offers a software encryption package called Cryptos for $100. The package is based on the Data Encryption Standard, America’s own national standard.^38^

The plea for a longer key wasn’t heeded, nor were details of the S-box construction revealed. Although adoption of DES was widespread, these problems prevented it from being universally accepted.

Robert Morris of Bell Laboratories in Murray Hill, New Jersey, says that officials of the Bell Telephone Company have decided that the DES is too insecure to be used in the Bell System.^39^

In 1985, when DES was used by bankers to encrypt electronic fund transfers, NSA Deputy Director Walter Deeley said he “wouldn’t bet a plugged nickel on the Soviet Union not breaking it.”^40^ Yet, DES remained mandatory until 2002 for all federal agencies, for protection of sensitive unclassified information needing encryption.

A common question over the years since the arrival of DES was whether or not NSA could break it. The quote above seems to indicate an affirmative answer by 1985, but the quote by Matt Blaze reproduced below comes at the question from another perspective.^41^

An NSA-employed acquaintance, when asked whether the government can crack DES traffic, quipped that real systems are so insecure that they never need to bother.

Blaze went on to give a list of the “Top Ten Threats to Security in Real Systems.” Anyone concerned with actual security, and not just the mathematical aspects of the subject should study this list.^42^

## 13.2.3 S-Boxes Revealed!

In 1990, Eli Biham and Adi Shamir applied a new attack they had developed, called *differential cryptanalysis*, to DES. It turned out that this approach was only better than brute force if there were 15 or fewer rounds and DES had 16. Perhaps this was why! In fact, differential cryptanalysis was known to the DES designers. They called it “T attack.” The mysterious S-boxes were generated and tested until ones that fit certain criteria were found; they needed to be able to resist T attack and linear cryptanalysis. Neither attack was publicly known at the time. The NSA knew about differential cryptanalysis, but didn’t want the information shared; hence, the generation of the S-boxes had to remain secret. Susan Landau, among others, believes that NSA had not anticipated linear cryptanalysis.^43^ In any case, both of these attacks were rediscovered in the open community and are now available to anyone.

There are some “weak” keys for DES. This term is used to denote keys such that all of the round keys they produce are identical. Obvious examples are a key consisting of 56 zeros and a key consisting of 56 ones, but there are two others. There are also six pairs of semi-weak keys that should be avoided. Rather than generating 16 distinct round keys, these only produce two, each of which is then used for 8 rounds. The result is that a key in each semi-weak pair can decrypt messages enciphered with the other key.^44^ Each extra key that can be used reduces the average run-time of a brute-force attack by a factor of two.

## 13.3 EFF vs. DES

The Electronic Frontier Foundation (EFF), a civil liberties group, eventually buried DES. They did this by designing and building a DES cracker, a specialized piece of hardware that could defeat the system in a reasonable amount of time (see Figures 13.8–13.10). It did so by testing over 90 billion keys per second. It should be noted that DES crackers can be run in parallel; hence, someone with ten of these machines can break DES ten times faster than someone with just one.

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_421_0.png)

**Figure 13.8** The EFF DES Cracker sits behind Paul Kocher, the principal designer, who is holding one of the 29 boards, each of which contains 64 custom microchips. (From [http://www.cryptography.com/technology/applied-research/research-efforts/des-key-search/des-key-search-photos.html](http://www.cryptography.com/technology/applied-research/research-efforts/des-key-search/des-key-search-photos.html) and used with the permission of Paul Kocher.)

---

^30^ Although not in the original declassified version, these passages were later released thanks to a FOIA request filed by John Young.

^31^ Johnson, Thomas, R., *American Cryptology During the Cold War, 1945–1989, Book III: Retrenchment and Reform, 1972–1980*, Center for Cryptologic History, National Security Agency, Fort George G. Meade, Maryland, 1995, p. 232.

^32^ Johnson, Thomas, R., *American Cryptology During the Cold War, 1945–1989, Book III: Retrenchment and Reform, 1972–1980*, Center for Cryptologic History, National Security Agency, Fort George G. Meade, Maryland, 1995, p. 232. Another source tells it differently: Foerstel, Herbert N., *Secret Science: Federal Control of American Science and Technology*, Praeger, Westport, Connecticut, 1993, p. 129 says the key was chopped from 128 bits (as used in Lucifer) to 56 bits and that NSA really wanted a 32 bit key!

^33^ Johnson, Thomas, R., *American Cryptology During the Cold War, 1945–1989, Book III: Retrenchment and Reform, 1972–1980*, Center for Cryptologic History, National Security Agency, Fort George G. Meade, Maryland, 1995, p. 239.

^34^ Morris, Robert, Neil J. A. Sloane, and Aaron D. Wyner, “Assessment of the National Bureau of Standards Proposed Federal Data Encryption Standard,” *Cryptologia*, Vol. 1, No. 3, July 1977, pp. 281–291, p. 282 cited here.

^35^ For claim and quote about doubt (from the authors), see Morris, Robert, Neil J. A. Sloane, and Aaron D. Wyner, “Assessment of the National Bureau of Standards Proposed Federal Data Encryption Standard,” *Cryptologia*, Vol. 1, No. 3, July 1977, pp. 281–291, p. 287 cited here.

^36^ Lexar Corporation, *An Evaluation of the NBS Data Encryption Standard*, unpublished report, Lexar Corporation, 11611 San Vicente Boulevard, Los Angeles, California, 1976.

^37^ Foerstel, Herbert N., *Secret Science: Federal Control of American Science and Technology*, Praeger, Westport, Connecticut, 1993, p. 129.

^38^ Foerstel, Herbert N., *Secret Science: Federal Control of American Science and Technology*, Praeger, Westport, Connecticut, 1993, p. 138.

^39^ Kolata, Gina Bari, “Computer Encryption and the National Security Agency Connection,” *Science*, Vol. 197, No. 4302, July 29, 1977, pp. 438–440.

^40^ Foerstel, Herbert N., *Secret Science: Federal Control of American Science and Technology*, Praeger, Westport, Connecticut, 1993, p. 129.

^41^ Schneier, Bruce, *Applied Cryptography*, second edition, John Wiley & Sons, Inc., New York, 1996, p. 619 from the afterword by Matt Blaze.

^42^ Schneier, Bruce, *Applied Cryptography*, second edition, John Wiley & Sons, Inc., New York, 1996, pp. 620–621 from the afterword by Matt Blaze.

^43^ In any case, it first appeared publicly in Matsui, Mitsuru, “Linear Cryptanalysis Method for DES Cipher,” in Helleseth, Tor, editor, *Advances in Cryptology – EUROCRYPT ’93 Proceedings*, Lecture Notes in Computer Science, Vol. 765, Springer, Berlin, Germany, 1994, pp. 386–397.

^44^ For more on this topic see Moore, Judy H. and Gustavus Simmons, “Cycle Structure of the DES with Weak and Semiweak Keys,” in Odlyzko, Andrew M., editor, *Advances in Cryptology – CRYPTO ’86 Proceedings*, Lecture Notes in Computer Science, Vol. 263, Springer, Berlin, Germany, 1987, pp. 9–32.
