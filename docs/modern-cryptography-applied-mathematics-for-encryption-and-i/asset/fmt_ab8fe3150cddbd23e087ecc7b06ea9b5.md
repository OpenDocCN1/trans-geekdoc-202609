
There is a mathematical puzzle that can help, however, called the `birthday paradox` (sometimes called the birthday problem). Here’s the basic idea: How many people would you need to have in a room to have a strong likelihood that 2 would have the same birthday (month and day, not year)? Obviously, if you put 367 people in a room, at least 2 of them must have the same birthday, as there are only 365 days in a year (plus one more on a leap year). However, we are not asking how many people you need to *guarantee* a match, just how many you need to create a strong probability. It just so happens that with only 23 people in the room, there is a 50 percent chance that 2 people will have the same birthday.

How is this possible with so few people? How is it that such a low number can work? Basic probability tells us that when events are independent of one another, the probability of all the events occurring is equal to a product of the probabilities of each event occurring. So the probability that the first person does not share a birthday with any previous person is 1.0, or 100 percent, since there are no previous people in the set: That can be written as `365/365`. For the second person, there is only one preceding person, and the odds that the second person has a birthday different from the first are `364/365`. For the third person, the odds of having a different birthday than either of the two preceding people are `363/365`. Since each of these is independent, we can compute the probability as follows:

`365/365 \* 364/365 \* 363/365 \* 362/365 … \* 342/365`

(342 is the probability of the 23rd person sharing a birthday with a preceding person.) Let’s convert these to decimal values (truncating at the third decimal point):

`1 \* 0.997 \* 0.994 \* 0.991 \* 0.989 \* 0.986 \* … 0.936 = 0.49 or 49%`

This 0.49, or 49 percent, is the probability that none of the 23 will have a birthday in common, which means there is a 0.51, or 51 percent (better than even odds) probability that 2 of the 23 will have a birthday in common.

Just for reference, if 30 people are involved, the probability that 2 have the same birthday is 0.706, or 70.6 percent. With 50 people the probability raises to 0.97, or 97 percent, which is quite high. This does not simply apply to birthdays, of course. The same concept can be applied to any set of data, and it is often used in cryptography and cryptanalysis.

In reference to cryptographic hash functions, the goal is to find two different inputs that produce the same output. When two inputs produce the same output from a cryptographic hash, this is referred to as a `collision`. It just so happens that from any set of *n* elements, the number of samples required to get a match or collision with a greater than 0.5, or 50 percent, probability is `1.174 √*n*`. Returning to the preceding birthday problem, `1.174 √365 = 22.49`.

You can apply this to other cryptographic issues as well. Let’s return to the DES algorithm. Recall that it has 72,057,594,037,927,936 possible keys. To guarantee that you find the correct key, you may need to check all 72,057,594,037,927,936 possibilities. However, if all you are seeking is a greater than 50 percent chance of finding the right key, you can try `1.774 √72,057,594,037,927,936` possible keys—only 476,204,499 possible keys. This is far more manageable. In fact, again referring to our earlier scenario with DES, if you can attempt 1 million keys per second, you have a 50 percent chance of finding the right key in 7.9 minutes. Although 1 million keys per second is beyond the capability of your standard personal computer, it is well within the capabilities of supercomputers or even computing clusters.

The birthday paradox is one reason why larger key sizes are necessary for security. If we move our attention from DES to an AES 128-bit key, there are approximately `3.402 * 10^(38)` possible keys. Applying the birthday paradox gives us `1.774 √(3.402 * 10^(38))`, or 32,724,523,986,760,744,567, keys that need to be attempted to have a 50 percent chance of finding a match. This number is large enough that it is computationally infeasible to break it through brute-force methods, even with the birthday paradox.

**Note**

For more details on this mathematical problem and how it applies to cryptography, you can consult [Chapter 2](#part0010.xhtml#ch02) of *Modern Cryptanalysis: Techniques for Advanced Code Breaking* (Wiley, 2008), which provides even more detailed coverage of the birthday paradox. Professor Dan Boneh also created a very good video on this topic at [www.youtube.com/watch?v=ZZovSCFZffM](http://www.youtube.com/watch?v=ZZovSCFZffM).

#### Other Methods

Cryptanalysis is a formal process whereby one applies specific techniques in an attempt to crack cryptography. However, as you have seen in this chapter, one’s ability to crack a cipher completely is quite limited. In many cases, the best one can hope to achieve is to derive some additional information about the target key. In many cases, breaking cryptography is so time consuming, and the probability of actually deriving the key is so small, that cryptanalysis provides no practical means of breaking ciphers. Put another way, cryptanalysis is an excellent tool for testing the security of a given cipher, but it is usually not efficient enough to make it a practical means for situations that require that the cipher be compromised in a short period of time. For example, a law enforcement agency that needs to break the encryption on a hard drive is unlikely to find cryptanalysis techniques of much use. However, using other methods for compromising ciphers might provide more immediate results. These methods all depend on some flaw in the implementation of the cryptography.

##### Other Passwords

Particularly with e-mail and hard drive encryption, a user is typically required to know some password in order to decrypt and access the information. Many hard drive encryption tools use very strong encryption. For example, Microsoft BitLocker, introduced with Windows 7, uses AES with a 128-bit key.

Several open source hard drive encryption tools use AES with a 256-bit key. It is simply not feasible to break this key. However, because it is possible that the user has used the same password (or a substantially similar permutation) somewhere else—such as with an e-mail account, or with a Windows password—you can check these sources for the key. You might even use Ophcrack on a Windows computer and use those passwords (and permutations of those passwords) to try and decrypt the encrypted partition or e-mail.

After the fact, many people are not even aware that their e-mail password has been cracked. Several web sites keep lists of e-mail accounts that have been breached, including [haveibeenpwned.com](http://haveibeenpwned.com) and [PwnedList.com](http://PwnedList.com).

**Note**

If you are a law enforcement officer attempting to breach an encrypted drive belonging to a suspect, you can check these sites to see if the suspect’s e-mail account has been breached. You can then use the e-mail password, and close permutations, to attempt to decrypt the hard drive.

##### Related Data

It is often the case that people choose passwords that have some meaning for them. This makes memorization much easier. I frequently advise forensic analysts to learn all they can about a suspect, and photographing or videotaping the area where the computer is seized can be quite valuable as well. If, for example, the suspect is an enthusiastic fan of a particular sports team, with memorabilia extensively displayed in his or her home or office, this type of information might aid in breaking encrypted drives, phones, and e-mails. It is at least reasonably likely that this individual’s cryptography password is related to a beloved sports team.

##### Spyware
