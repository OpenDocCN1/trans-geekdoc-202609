encrypting a message. Regardless of whether you go on to study modern, sophisticated encryption methods, it is important for you to have some basic idea of how encryption works at a conceptual level. Having a basic grasp of how encryption works, in principle, will help you better understand the concepts of any encryption method you encounter in the real world. Khan Academy has an online cryptography course that is good for beginners.

# The Caesar Cipher

One of the oldest encryption methods is the *Caesar cipher*. This method is purported to have been used by the ancient Roman Caesars—thus, the name. It is actually quite simple to do. You choose some number by which to shift each letter of a text. For example, if the text is:

A cat

and you choose to shift by two letters, then the message becomes:

C ecv

Or, if you choose to shift by three letters, it becomes:

D fdw

Julius Caesar was reputed to have used a shift of three to the right. However, you can choose any shifting pattern you wish. You can shift either to the right or to the left by any number of spaces you like. Because this is a very simple method to understand, it makes a good place to start our study of encryption. It is, however, extremely easy to crack. You see, any language has a certain letter and word frequency, meaning that some letters are used more frequently than others). In the English language, the most common single-letter word is *A*. The most common three-letter word is *the*. Those two rules alone could help you decrypt a Caesar cipher. For example, if you saw a string of seemingly nonsense letters and noticed that a three-letter word was frequently repeated in the message, you might easily surmise that this word was *the*—and the odds are highly in favor of this being correct. Furthermore, if you frequently noticed a single-letter word in the text, it is most likely the letter *A*. You now have found the substitution scheme for *A, T, H,* and *E*. You can now either translate all of those letters in the message and attempt to simulate the rest or simply analyze the substitute letters used for *A, T, H,* and *E* and derive the substitution cipher that was used for this message. Decrypting a message of this type does not even require a computer. It can be done in less than 10 minutes using pen and paper by someone with no background in cryptography. There are other rules that will help make cracking this code even easier. For example, in the English language the two most common two letter combinations are *ee* and *oo*. That gives you even more to work on.

Another reason this algorithm can be easily cracked is an issue known as *key space*—the number of possible keys that can be used. In this case, when applied to the English alphabet, there are only 26 possible keys since there are only 26 letters in the English alphabet. This means you could simply try each possible key (+1, +2, +3,… +26) until one works. Trying all possible keys is referred to as a *brute-force attack*.

The substitution scheme you choose (for example, +2, +1) is referred to as a *substitution alphabet* (for example, *B* substitutes for *A*, *U* substitutes for *T*). Thus, the Caesar cipher is also referred to as a *mono-alphabet substitution* method, meaning that it uses a single substitution for the encryption. There are other mono-alphabet algorithms, but the Caesar cipher is the most widely known.

# Atbash

In ancient times, Hebrew scribes used the Atbash substitution cipher to encrypt religious works such as the book of Jeremiah. Applying this cipher is fairly simple: Just reverse the order of the letters of the alphabet. This is, by modern standards, a very primitive and easy-to-break cipher.

The Atbash cipher is a Hebrew code that substitutes the first letter of the alphabet for the last and the second letter for the second to the last, and so on. It simply reverses the alphabet. For example, in English, *A* becomes *Z*, *B* becomes *Y*, *C* becomes *X*, and so on. Of course, the Hebrews used a