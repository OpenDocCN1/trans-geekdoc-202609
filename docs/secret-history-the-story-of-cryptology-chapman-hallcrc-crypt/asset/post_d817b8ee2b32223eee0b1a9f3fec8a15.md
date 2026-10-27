
MD5 … SHA-1 hashing is also used in distributed revision control systems such as Git, Mercurial, and Monotone to identify revisions, and to detect data corruption or tampering. The algorithm has also been used on Nintendo console Wii for signature verification during boot, but a significant implementation flaw allowed an attacker to bypass the security scheme.[^14]

Few organizations update their security in a timely manner.

Since 2013, more and more impressive attacks against SHA-1 have been found. While the attacks against SHA-2 are far less impressive, the similarities between this set of algorithms and SHA-1 are enough to concern cryptologists. Therefore, NIST held a competition to find an alternative (not a replacement) to SHA-2. This alternative was to be called SHA-3. Following a lengthy competition with 64 contenders, the winner, announced on October 2, 2012, was Keccak, a hash function designed by Guido Bertoni, Joan Daemen, Michael Peeters, and Gilles Van Assche.[^15] In the abstract of their paper titled “The Making of KECCAK,” the designers wrote

Its structure and components are quite different from its predecessors, and at first sight it seems like a complete break with the past. In this article, researchers show that KECCAK is the endpoint of a long learning process involving many intermediate designs, mostly gradual changes, but also some drastic changes of direction.[^16]

Daemen remarked, “Personally I consider my greatest result Keccak and not Rijndael. In fact its design contains the best elements of all cryptographic research I’ve done since I’ve started in 1989.”[^17]

While mathematicians are working out security issues, world governments are racing ahead. Bill Clinton was the first U.S. President to use digital signatures. These were applied, most suitably, to an e-commerce treaty with Ireland in September 1998 and, in 2000, a bill that gave digital signatures the same status, legally, as traditional signatures.

You may have noticed that I didn’t provide details of any of the algorithms mentioned above. It’s not because these details are unimportant. It’s simply because this is one of the few areas in cryptology that I could never get too excited about. I think part of the problem for me is that, unlike cipher systems, there’s no message to uncover. One usually just looks for collisions. The References and Further Reading list at the end of this chapter provides several books that devote serious space to the topic of hash functions, as well as some important papers, if you’re interested. We now move on to how hash functions can be used to protect passwords, a topic I find much more interesting.

## 17.3.2 Hash Functions and Passwords

Hash functions have applications other than allowing for quicker digital signatures. Passwords should never be stored on a computer, but there needs to be a way to tell if the correct password has been entered. This is typically done by hashing the password after it is entered and comparing

[^14] https://web.archive.org/web/20110221161831/http://en.wikipedia.org/wiki/SHA-1. The Wikipedia article provided the following reference for the Wii hack: http://debugmo.de/?p=61.

[^15] See https://www.nist.gov/news-events/news/2012/10/nist-selects-winner-secure-hash-algorithm-sha-3-competition and https://csrc.nist.gov/groups/ST/hash/sha-3/sha-3_selection_announcement.pdf.

[^16] Bertoni, Guido, Joan Daemen, Michaël Peeters, and Gilles Van Assche, “The Making of KECCAK,” *Cryptologia*, Vol. 38, No. 1, January 2014, pp. 26–60.

[^17] Email from Joan Daemen to the author, March 28, 2012. See Chapter 20 for a description of Rijndael.

the result with a value that is stored. Because computing any preimage should be difficult for a good hash function, someone gaining access to the hashed values shouldn’t be able to determine the passwords.

In the first edition of this book, I wrote, “The important idea of storing the password in a disguised form doesn’t seem to be strongly associated with anyone. Somebody had to be first to hit on this idea, but I haven’t been able to learn who.” After quoting what was clearly an incorrect account of this innovation from Wikipedia, I wrote, “Anyone who can provide a definitive first is encouraged to contact me!” I soon heard from Steven Bellovin (see Section 2.12). He wrote:

> While visiting Cambridge (my 1994 visit, I think), I was told by several people that Roger Needham had invented the idea. I asked him why he had never claimed it publicly; he said that it was invented at the Eagle Pub – then the after-work gathering spot for the Computer Laboratory – and both he and the others present had had sufficiently much India Pale Ale that he wasn’t sure how much was his and how much was anyone else’s…¹⁸

Ross Anderson noted, “For some time Roger Needham and Mike Guy each credited the other with the invention.”¹⁹ In any case, Maurice Wilkes was the first to publish the solution (in 1968), giving Needham full credit.²⁰ Needham’s good night in the pub was back in 1967.²¹ A decade later, he continued to pursue his research in the same manner. Sape Mullender, a PhD student at the time, recalled:

> The first time I met Roger was in the late seventies and, at the end of the afternoon, a chunk of the department, including Roger, went to the Eagle, the pub in Bene’t Street. Until the Computer Laboratory moved to the outskirts of the city, that was the place where the day’s events were discussed almost daily. It’s also the pub where Crick and Watson contemplated DNA and came up with the double helix structure.²²

Mullender checked in again after another decade:

> I spent a sabbatical in Cambridge in 1987/1988 and daily trips to the Eagle were still very much part of the culture. Roger would definitely join a few times a week. During that time, the Eagle was renovated and lost some of its dingy charm, so excursions further afield were also undertaken. The Bath and the Mill became frequent haunts. I think the reason those places became so inspirational was that (1) students were relaxed when there and that’s a condition for having brainwaves and (2) mingling took place between different groups and this gave an opportunity for fresh ideas to come to some of the problems.²³

18 Bellovin, Steven, email to the author, August 5, 2013.
19 Email from Ross Anderson to the author, May 20, 2020. Anderson credits both in his forthcoming book Anderson, Ross, Security Engineering, Third Edition, Wiley, Indianapolis, Indiana, see chapter 3, p. 108, available online at https://www.cl.cam.ac.uk/~rja14/book.html.
20 Wilkes, Maurice V., Time-Sharing Computer Systems, American Elsevier, New York, 1968, pp. 91–92.
21 Schofield, Jack, “Roger Needham,” The Guardian, March 10, 2003, available online at https://www.theguardian.com/news/2003/mar/10/guardianobituaries.microsoft.
22 Email from Sape Mullender to the author, May 20, 2020.
23 Email from Sape Mullender to the author, May 20, 2020.

Cipher Deavours, perhaps unaware of Needham’s role in this story, wrote, “Non-classified work on such functions dates back to the early 1970s.”[^24] One would assume that the government had studied the problem before then. Deavours went on to reference a 1977 paper by Peter J. Downey that describes a system in use in 1972.[^25] This system’s initial step was vaguely described as “some preliminary reductions in [the password’s] length.” But after that, the next step is crystal clear. The password, *p*, was enciphered as

$$C = (2^{16})(p) \pmod{10^{19}-1}.$$

Downey broke this system, recovering passwords from their enciphered values. Doing so only required computing the multiplicative inverse of $2^{16} \pmod{10^{19}-1}$. It’s a wonder anyone thought this could be secure!

Hashes used in this manner needn’t decrease the size of the data being “hashed,” but they must have the property that preimages are difficult to compute. Sometimes such hashes are referred to as one-way functions; however, there is no mathematical proof that one-way functions even exist! Some other references to password protection from the early 1970s are listed below:

- Bartek, Douglas J., “Encryption for Data Security,” *Honeywell Computer Journal*, Vol. 8, No. 2, September 1974, pp. 86–89.
- Evans, Jr., Arthur, William Kantrowitz and Edwin Weiss, “A User Authentication Scheme not Requiring Secrecy in the Computer,” *Communications of the ACM*, Vol. 17, No. 8, August 1974, pp. 437–442.
- Purdy, George B., “A High Security Log-in Procedure,” *Communications of the ACM*, Vol. 17, No. 8, August 1974, pp. 442–445.
- Wilkes, Maurice V., *Time-Sharing Computer Systems*, American Elsevier, New York, 1972. This is a second edition of the work that first presented Needham’s idea.

A 1979 paper by Robert Morris and Ken Thompson of Bell Labs is worth looking at in greater detail.[^26] It gave the history of password security on the UNIX time-sharing system. At first, the passwords were enciphered by software simulating a cipher machine used by the United States during WW II, namely the M-209 (see the last paragraph of [Section 9.1](#)). However, it turned out that the machine wasn’t any better in this capacity than it was for keeping secrets long-term during the war.

It turned out that the M-209 program was usable, but with a given key, the ciphers produced by this program are trivial to invert. It is a much more difficult matter to find out the key given the cleartext input and the enciphered output of the program. Therefore, the password was used not as the text to be encrypted but as the key, and a constant was encrypted using this key. The encrypted result was entered into the password file.[^27]

[^24]: Deavours, Cipher, “The Ithica Connection: Computer Cryptography in the Making, A Special Status Report,” *Cryptologia*, Vol. 1, No. 4, October 1977, pp. 312–316, p. 313 cited here.

[^25]: Downey, Peter J., *Multics Security Evaluation: Password and File Encryption Techniques*, ESD-TR-74-193, Vol. III, Electronic Systems Division, Hanscom Air Force Base, Massachusetts, June 1977.

[^26]: Morris, Robert and Ken Thompson, “Password Security: A Case History,” *Communications of the ACM*, Vol. 22, No. 11, November 1979, pp. 594–597.

[^27]: Morris, Robert and Ken Thompson, “Password Security: A Case History,” *Communications of the ACM*, Vol. 22, No. 11, November 1979, pp. 594–597, quotation taken from online version at https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.128.1635.
