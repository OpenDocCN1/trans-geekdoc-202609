
# Even though passwords are widely used, they suffer from some difficulties of use:

* **Use**. Supplying a password for each access to an object can be inconvenient and time consuming.
* **Disclosure**. If a user discloses a password to an unauthorized individual, the object becomes immediately accessible. If the user then changes the password to re-protect the object, the user must inform any other legitimate users of the new password because their old password will fail.
* **Revocation**. To revoke one user’s access right to an object, someone must change the password, thereby causing the same problems as disclosure.
* **Loss**. Depending on how the passwords are implemented, it may be impossible to retrieve a lost or forgotten password. The operators or system administrators can certainly intervene and provide a new password, but often they cannot determine what password a user had chosen previously. If the user loses (or forgets) the password, administrators must assign a new one.

## Attacking and Protecting Passwords

How secure are passwords themselves? Passwords are somewhat limited as protection devices because of the relatively small number of bits of information they contain. Worse, people pick passwords that do not even take advantage of the number of bits available: Choosing a well-known string, such as `qwerty`, `password`, or `123456` reduces an attacker’s uncertainty or difficulty essentially to zero.

Knight and Hartley [[KNI98](#bib01.html#bib_335)] list, in order, 12 steps an attacker might try in order to determine a password. These steps are in increasing degree of difficulty (number of guesses), and so they indicate the amount of work to which the attacker must go in order to derive a password. Here are their password guessing steps:

* no password
* the same as the user ID
* is, or is derived from, the user’s name
* on a common word list (for example, `password`, `secret`, `private`) plus common names and patterns (for example, `qwerty`, `aaaaaa`)
* contained in a short college dictionary
* contained in a complete English word list
* contained in common non-English-language dictionaries
* contained in a short college dictionary with capitalizations (`PaSsWorD`) or substitutions (digit `0` for letter `O`, and so forth)
* contained in a complete English dictionary with capitalizations or substitutions
* contained in common non-English dictionaries with capitalization or substitutions
* obtained by brute force, trying all possible combinations of alphabetic characters
* obtained by brute force, trying all possible combinations from the full character set

Although the last step will always succeed, the steps immediately preceding it are so time consuming that they will deter all but the most dedicated attacker for whom time is not a limiting factor.

***

**Every password can be guessed; password strength is determined by how many guesses are required.**

***

We now expand on some of these approaches.

### Dictionary Attacks

Several network sites post dictionaries of phrases, science fiction character names, places, mythological names, Chinese words, Yiddish words, and other specialized lists. These lists help site administrators identify users who have chosen weak passwords, but the same dictionaries can also be used by attackers of sites that do not have such attentive administrators. The `COPS` [[FAR90](#bib01.html#bib_188)], `Crack` [[MUF92](#bib01.html#bib_419)], and `SATAN` [[FAR95](#bib01.html#bib_189)] utilities allow an administrator to scan a system for weak passwords. But these same utilities, or other homemade ones, allow attackers to do the same. Now Internet sites offer so-called password recovery software as freeware or shareware for under $20. (These are password-cracking programs.)

People think they can be clever by picking a simple password and replacing certain characters, such as `0` (zero) for letter `O`, `1` (one) for letter `I` or `L`, `3` (three) for letter `E` or `@` (at) for letter `A`. But users aren’t the only people who could think up these substitutions.

### Inferring Passwords Likely for a User

If Sandy is selecting a password, she is probably not choosing a word completely at random. Most likely Sandy’s password is something meaningful to her. People typically choose personal passwords, such as the name of a spouse, child, other family member, or pet. For any given person, the number of such possibilities is only a dozen or two. Trying this many passwords by computer takes well under a second! Even a person working by hand could try ten likely candidates in a minute or two.

Thus, what seemed formidable in theory is in fact quite vulnerable in practice, and the likelihood of successful penetration is frighteningly high. Morris and Thompson [[MOR79](#bib01.html#bib_415)] confirmed our fears in their report on the results of having gathered passwords from many users, shown in [Table 2-1](#ch02.html#ch02tab01). [Figure 2-1](#ch02.html#ch02fig01) (based on data from that study) shows the characteristics of the 3,289 passwords gathered. The results from that study are distressing, and the situation today is likely to be the same. Of those passwords, 86 percent could be uncovered in about one week’s worth of 24-hour-a-day testing, using the very generous estimate of 1 millisecond per password check.

![Image](graphics/02tab01.jpg)

**TABLE 2-1** Password Characteristics

![Image](graphics/02fig01.jpg)

**FIGURE 2-1** Distribution of Password Types

Lest you dismiss these results as dated (they were reported in 1979), Klein repeated the experiment in 1990 [[KLE90](#bib01.html#bib_332)] and Spafford in 1992 [[SPA92a](#bib01.html#bib_585)]. Each collected approximately 15,000 passwords. Klein reported that 2.7 percent of the passwords were guessed in only 15 minutes of machine time (at the speed of 1990s computers), and 21 percent were guessed within a week! Spafford found that the average password length was 6.8 characters and that 28.9 percent consisted of only lowercase alphabetic characters.

Then, in 2002 the British online bank Egg found its users still choosing weak passwords [[BUX02](#bib01.html#bib_101)]. A full 50 percent of passwords for their online banking service were family members’ names: 23 percent children’s names, 19 percent a spouse or partner, and 9 percent their own. Alas, pets came in at only 8 percent, while celebrities and football (soccer) stars tied at 9 percent each. And in 1998, Knight and Hartley [[KNI98](#bib01.html#bib_335)] reported that approximately 35 percent of passwords are deduced from syllables and initials of the account owner’s name. In December 2009 the computer security firm Imperva analyzed 34 million Facebook passwords that had previously been disclosed accidentally, reporting that

* about 30 per cent of users chose passwords of fewer than seven characters.
* nearly 50 per cent of people used names, slang words, dictionary words or trivial passwords—consecutive digits, adjacent keyboard keys and so on.
* most popular passwords included `12345`, `123456`, `1234567`, `password`, and `iloveyou`, in the top ten.

Two friends we know told us their passwords as we helped them administer their systems, and their passwords would both have been among the first we would have guessed. But, you say, these are amateurs unaware of the security risk of a weak password. At a recent meeting, a security expert related this experience: He thought he had chosen a solid password, so he invited a class of students to ask him questions and offer guesses as to his password. He was amazed that they asked only a few questions before they had deduced the password. And this was a security expert!
