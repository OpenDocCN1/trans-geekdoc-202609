to use one byte, it would only be able to create 256 unique tokens - one for each unique byte. If we were to increase the number of bytes used to 2 the number of unique tokens we could create would increase to 65,536 (256 x 256).

More generally, when we are using N bytes in our remember remember token function the total number of unique tokens we can create is equal to 256^N. When using 32 bytes this translates to 256 ^ 32 = 1e77 tokens, which is an incredibly large number. Do we really need that many potential tokens to choose from?

There are a lot of factors that go into picking the number of bytes to use for our remember token, but in my opinion the simplest way to understand this is to look at a simple game as an example.

Imagine that you and a friend are playing a game where you pick a number between 1 and 10, and your friend tries to guess the number that you picked.

Assuming you pick randomly, if your friend has N guesses before he loses, he has a N/10 chance of guessing the number correctly on the first try. If they get it wrong and guess again, they would have a 1/9 chance of getting it the second time.

More generally put, if your friend has N guesses before he loses, he has a N/10 chance of getting it right. So if they were able to guess 10 times, they would have a 100% (10/10) chance of getting it right. With 5 guesses they would have a 50% (5/10) chance of getting it right.

Now imagine that a few friends came over and wanted to join the game, so you decide to change the rules a bit. There will still be one person guessing, but everyone else pick a unique number between 1 and 10 that nobody else has picked yet. For example, if you had four people playing in total you would have one person guessing, three picking numbers, and their choices would be 1, 3, and 5.

Now that you have 3 friends, it doesn’t make sense to guess a single person’s number. Instead, you decide that the guess wins whenever he picks anyone’s