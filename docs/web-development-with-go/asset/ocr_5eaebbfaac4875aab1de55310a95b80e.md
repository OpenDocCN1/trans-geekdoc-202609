# 11.6. HASHING REMEMBER TOKENS

number correctly.

This drastically changes the odds of the game!

Now rather than having a 1/10 chance of getting a number right on the first guess you have a 3/10 chance. If you guessed three different numbers you would have over a 70% chance of guessing someone's number.

Guessing a remember token is similar to this game. When an attacker tries to guess a valid remember token and you have one user you don't need a lot of unique values to make it challenging, but as you gain more users the odds of them guessing any single user's remember token increases drastically.

To make matters worse, attackers using computers to generate remember tokens can guess faster than people can. Rather than taking 1 guess every few seconds, and attacker is likely to be making 10,000 or more guesses every second. Yikes!

Putting this all together, we need to pick a large enough set of remember tokens that an attacker can't easily guess remember token even when they are guessing for many users and guessing thousands of times per second. 32 bytes allows us to choose from enough unique remember tokens that this isn't likely to happen.

# 11.6 Hashing remember tokens

While our remember tokens are hard to guess, we still have another issue to address. If we were to store remember tokens in our database and an attacker gained access to our database they would be able to manually create cookies and impersonate any of our users.

We obviously don't want this to happen, so than storing raw remember tokens in our database we are going to store the hash of each remember token similar to what we do for passwords, but rather than using bcrypt we are going