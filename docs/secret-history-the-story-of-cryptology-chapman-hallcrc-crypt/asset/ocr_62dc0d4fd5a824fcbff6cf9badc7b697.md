where π ≈ 3.1415 and e ≈ 2.71828. The ~ is read as “asymptotically approaches” and means

lim n→∞ n! / ( √(2πn) (n^n) (e^{-n}) ) = 1

So, we have a nice compact formula that relates the concept of factorials to some of the most important constants in mathematics!

In classical cryptography, it has often been desirable to have a key that can be memorized, because if the key is written down, it is susceptible to seizure. It would be time-consuming to memorize A goes to H, B goes to Q, C goes to R, etc. for all 26 letters. This leads us to keyword ciphers.13 For example, using the keyword PRIVACY, we have

A B C D E F G H I J K L M N O P Q R S T U V W X Y Z plaintext
P R I V A C Y B D E F G H J K L M N O Q S T U W X Z ciphertext

Letters that are not used in the keyword follow it in alphabetical order when writing out the ciphertext alphabet. Thus, we have a cipher superior to the Caesar shift, but still weakened by some order being retained in the cipher alphabet. Such ciphers may be further complicated by having the keyword placed somewhere other than the start of the alphabet. For example, we may use the two-part key (PRIVACY, H) and encipher with

A B C D E F G H I J K L M N O P Q R S T U V W X Y Z plaintext
Q S T U W X Z P R I V A C Y B D E F G H J K L M N O ciphertext

Also, long key phrases may be used to determine the order of the substitutions. If a letter is repeated, simply ignore it when it reappears,14 as you write the cipher alphabet out. Key phrases may be chosen that contain all of the letters of the alphabet. For example,

The quick brown fox jumps over a lazy dog. (33 letters)

A B C D E F G H I J K L M N O P Q R S T U V W X Y Z plaintext
T H E Q U I C K B R O W N F X J M P S V A L Z Y D G ciphertext

Richard Lederer provides several shorter phrases using all 26 letters:15

+   - Pack my box with five dozen liquor jugs. (32 letters)
+   - Jackdaws love my big sphinx of quartz. (31 letters)
+   - How quickly daft jumping zebras vex. (30 letters)
+   - Quick wafting zephyrs vex bold Jim. (29 letters)
+   - Waltz, nymph, for quick jigs vex Bud. (28 letters)
+   - Bawds jog, flick quartz, vex nymphs. (27 letters)
+   - Mr. Jock, TV quiz Ph.D., bags few lynx. (26 letters, a minimum)

13 The Argentis were the first to use keywords in this manner (during the late 1580s). See Kahn, David, The Codebreakers, second edition, Scribner, New York, 1996, p. 113.

14 An enciphered message sent to Edgar Allan Poe was made much more difficult to break because the sender did not do this (more on this later).

15 Lederer, Richard, Crazy English, Pocket Books, New York, 1989, pp. 159–160.