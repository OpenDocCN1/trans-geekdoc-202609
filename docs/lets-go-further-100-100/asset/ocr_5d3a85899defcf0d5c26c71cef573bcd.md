# Chapter 15.

# # User Activation

At the moment a user can register for an account with our *Greenlight* API, but we don’t know for sure that the email address they provided during registration *actually belongs to them*.

So, in this section of the book, we’re going to build up the functionality to confirm that a user used their own, real, email address by including ‘account activation’ instructions in their welcome email.

There are several reasons for having an activation step, but the main benefits are that it adds an additional hoop for bots to jump through, and helps prevent abuse by people who register with a fake email address or one that doesn’t belong to them.

To give you an overview upfront, the account activation process will work like this:

+   1. As part of the registration process for a new user we will create a cryptographically-secure random *activation token* that is impossible to guess.
+   2. We will then store a hash of this activation token in a new tokens table, alongside the new user’s ID and an expiry time for the token.
+   3. We will send the original (unhashed) activation token to the user in their welcome email.