
## 10.3. HASH PASSWORDS PROPERLY

The first is that two values might be converted to the same hash value. For example, if we provided the input “jon” it would return 3, but if we provided the input “password” it would also return 3 (8 % 5 = 3).

This is inevitable because we are saying that you can put a string of any size into our function, and we are limited to just 5 possible output values.

The second key point is that it is impossible to take a hash value and convert it back into the original string. Looking back at the same example, if we had the output 3, it is impossible to determine if the original input was “jon”, “password”, or some other string entirely.

## 10.3.2 Store hashed passwords, not raw passwords

How does this help us with passwords? Well, instead of storing the password that the user types in, we are instead going to store a hash of their password. That way even if someone gets access to our database, they won’t actually know each user’s password is. They will only know what the hash of each password is.

When we want to authenticate a user we won’t actually know what their password is, so when a user tries to log in we can hash the password they typed in and ask if it matches the hash we stored. If it is, the user provided the correct password. If it isn’t, the user typed the wrong password.

We can effectively validate a user’s password, but we have limited knowledge that we don’t have any way of remembering what their password is, and since we don’t know it, a hacker won’t be able to figure it out.

But that raises another question: Didn’t we say earlier that two inputs hash to the same value? What if two different passwords get hashed to the same value? This is a real possibility with hashes, but we will be using a much better hashing function that has so many possible outputs that it is extremely unlikely. You probably have a better chance of being struck by lightning after winning the lottery ticket. I haven't actually done the math to verify that claim, but my point is that accidentally guessing a password that hashes to the same value as a user's password is not really worrying about.

## 10.3.1. Encryption functions are NOT hashing functions

At some point you may learn about encryption functions like AES and think they would be a good fit here, but I want to again reiterate encryption and hashing are two different things and state that encryption is not appropriate for storing passwords.

The reason for this is simple: when you encrypt a password it is reversible. You do need the encryption key to decrypt a password, but if someone has hacked your encryption key they will be able to figure out every password in your database.

## 10.3.3 Salt and pepper

We have one last thing to discuss before we start storing passwords in our database: adding salt and pepper to passwords. Before anyone asks, I haven't accidentally mixed up manuscript with web development.

### What is a password salt?

Salting a password is the act of adding some random data to a password before hashing it. For example, if you typed in the password “abc123”, a program might salt the password by adding “salt” to it, making the string “abc123salt” which is hashed and stored in the password field instead of the original.

Earlier I told you that it is impossible to go from a hashed value back to the original value, so this might seem like a waste of time at first, but it isn’t. Password salts are necessary to prevent hackers using rainbow tables to crack users' passwords.

### What are rainbow tables?

The goal when designing a password system is to design one such that even if an attacker gets a copy of your database they won’t be able to figure out what each user’s password is. That way, even if your company loses access to your server you don’t have to worry about users having all of their accounts stolen. You should still take every precaution to secure your server, but this is our final fail-safe.

As we discussed earlier, it isn’t possible to hash a value and reverse it into the original password, so at first it would appear that we are covered, but unfortunately hackers are a pesky bunch and over time they have developed new ways of trying to determine passwords. Even if it isn’t possible to reverse a password hash, it is possible to generate a very large list of possible passwords and then hash each of these. Now they don’t actually have to reverse a hash; instead they can just check if their hash value matches the one you generated.

Let's look at an example to clarify. Imagine that I had a really long list of common passwords. My list might even have some random gibberish passwords that I think are likely to be used:

```
password
abc123
abcd1234
aksdfj
```

My list might have several million passwords in it, but for this example we will just use four. Now if I know you are using a specific hashing function, I could then run that hashing function on each of my passwords and store the results:

```
fake-hash-value-for-password
fake-hash-value-for-abc123
fake-hash-value-for-abcd1234
fake-hash-value-for-aksdfj
```

This is called a rainbow table, and after stealing your database I would take all of the hashes in your database and see if any match the values in my rainbow table. If one did match, I would know what their original password was by looking at my original list of passwords and determining which generated that hash.

The problem with this approach is that rainbow tables take a while to create. Hashing millions of possible passwords takes time, and hackers might have dictionaries with billions of possible passwords. As a result, this attack really works only if I can use the same rainbow table on every password stored in a database.

That is where salts come into play. By adding a random string to each password, the rainbow table becomes useless. The hash of “password-salt1” is different than the hash of “password-salt2”, so if every user has a different salt, the attacker would need to create a custom rainbow table for each user. Ouch!

One important thing to note is that salts aren’t private data. An attacker can gain access to a user’s salt, but because each user should have a different salt they would still need to generate a new rainbow table for each individual user, making it impractical.

### What is a password pepper?

A pepper is very similar to a salt, but rather than being user-specific it is application-specific. In our application we would have a universal pepper value that is similar to a salt. It is just some random string that we can append to passwords before hashing them.

Unlike a salt, a pepper is never stored in your database. That way if an attacker manages to gain access to your database but not your application they only have access to hashed passwords and salt values, but they won’t actually know what pepper value you used, making it much harder for them to discover what the underlying passwords were. In my opinion, this is one of the weaker precautions out of all of the ones we will be using, but it is incredibly easy to implement so it is worth adding anyway.
