Cipher Deavours, perhaps unaware of Needham’s role in this story, wrote, “Non-classified work on such functions dates back to the early 1970s.”[^24] One would assume that the government had studied the problem before then. Deavours went on to reference a 1977 paper by Peter J. Downey that describes a system in use in 1972.[^25] This system’s initial step was vaguely described as “some preliminary reductions in [the password’s] length.” But after that, the next step is crystal clear. The password, *p*, was enciphered as

$$C = (2^{16})(p) \pmod{10^{19}-1}.$$

Downey broke this system, recovering passwords from their enciphered values. Doing so only required computing the multiplicative inverse of $2^{16} \pmod{10^{19}-1}$. It’s a wonder anyone thought this could be secure!

Hashes used in this manner needn’t decrease the size of the data being “hashed,” but they must have the property that preimages are difficult to compute. Sometimes such hashes are referred to as one-way functions; however, there is no mathematical proof that one-way functions even exist! Some other references to password protection from the early 1970s are listed below:

+   - Bartek, Douglas J., “Encryption for Data Security,” *Honeywell Computer Journal*, Vol. 8, No. 2, September 1974, pp. 86–89.
+   - Evans, Jr., Arthur, William Kantrowitz and Edwin Weiss, “A User Authentication Scheme not Requiring Secrecy in the Computer,” *Communications of the ACM*, Vol. 17, No. 8, August 1974, pp. 437–442.
+   - Purdy, George B., “A High Security Log-in Procedure,” *Communications of the ACM*, Vol. 17, No. 8, August 1974, pp. 442–445.
+   - Wilkes, Maurice V., *Time-Sharing Computer Systems*, American Elsevier, New York, 1972. This is a second edition of the work that first presented Needham’s idea.

A 1979 paper by Robert Morris and Ken Thompson of Bell Labs is worth looking at in greater detail.[^26] It gave the history of password security on the UNIX time-sharing system. At first, the passwords were enciphered by software simulating a cipher machine used by the United States during WW II, namely the M-209 (see the last paragraph of [Section 9.1](#)). However, it turned out that the machine wasn’t any better in this capacity than it was for keeping secrets long-term during the war.

It turned out that the M-209 program was usable, but with a given key, the ciphers produced by this program are trivial to invert. It is a much more difficult matter to find out the key given the cleartext input and the enciphered output of the program. Therefore, the password was used not as the text to be encrypted but as the key, and a constant was encrypted using this key. The encrypted result was entered into the password file.[^27]

+   [^24]: Deavours, Cipher, “The Ithica Connection: Computer Cryptography in the Making, A Special Status Report,” *Cryptologia*, Vol. 1, No. 4, October 1977, pp. 312–316, p. 313 cited here.
+   
+   [^25]: Downey, Peter J., *Multics Security Evaluation: Password and File Encryption Techniques*, ESD-TR-74-193, Vol. III, Electronic Systems Division, Hanscom Air Force Base, Massachusetts, June 1977.
+   
+   [^26]: Morris, Robert and Ken Thompson, “Password Security: A Case History,” *Communications of the ACM*, Vol. 22, No. 11, November 1979, pp. 594–597.
+   
+   [^27]: Morris, Robert and Ken Thompson, “Password Security: A Case History,” *Communications of the ACM*, Vol. 22, No. 11, November 1979, pp. 594–597, quotation taken from online version at https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.128.1635.