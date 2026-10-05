
# CHAPTER 9. CREATING THE USER MODEL

recommend rendering raw error messages to the end user, but this code is temporary and will only be seen by developers so I am adding it in case we have an issue and need to debug.

```sql
INSERT INTO "users" ("created_at","updated_at","deleted_at","name","email")
VALUES ('2017-07-24 15:25:45', '2017-07-24 15:25:45',NULL,'Michael Scott', 'michael2@undermifflin.com')
RETURNING "users", "id"
```

> Note: If you see an error like the below, it indicates that you tried to create a user that already exists in your database.

```
pq: duplicate key value violates unique constraint "uix_users_email"
```

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/9.7.3

Changes - book.usegolang.com/9.7.3-diff

# 9.8 Exercises

The exercises for this chapter are once again going to involve code that we won’t be keeping, but are instead meant to help reinforce what we just learned and coded. If you do write and run any of this code, be sure to reset your database to reflect the user table we will be using in the rest of the book.

### 9.8.1 Ex1 - Add an Age field to our user resource

Adding a new field to a resource involved a few steps. Try to walk through them to see if you can figure out what all code you would need to add in order to let a user provide their age when creating an account and have it persisted in the database.

### 9.8.2 Ex2 - Write a method to query the first user with a specific age

Once you have added the age field to your users model, write a method that will allow you to query users with a specific age. This should be attached to the UserService like our other query methods, and should be pretty similar to our ByID method.

### 9.8.3 Ex3 - [HARD] Write a method to query many users by age range

Our last exercises are a little harder only because you will need to write a bit more code and dig into GORM more.

Check out the last chapter and combine the information there demonstrating how to query multiple users with your knowledge of how GORM's Where method works to create an InAgeRange method on our user service.

The InAgeRange method should accept two arguments, a minimum age and a maximum age, and then it should return all users within that age range. If no users are found, you should return an empty slice of users, and you should also return an error when there is one. You DO NOT need to return an error when there are no users found - an empty slice will signify this.

# Chapter 10

# Building an authentication system

Authentication is arguably the most important and most sensitive part of your web application.

Not only can a poorly executed authentication strategy leave your user data at risk, you could also potentially leak passwords that are being used on other websites. Yikes!

While this might seem scary at first, the truth is that implementing a secure authentication service isn’t really that hard, but it is very important that you do not deviate from industry standards when designing authentication system.

Developers with good intentions deviating from the industry standard is what leads to major security issues, and you don’t want to see your website on the front page of the New York Times with a headline like “Data breach could put your accounts at risk.”

To help make sure this doesn’t happen, we will spend the first half of this chapter learning about how to properly store a password without writing any code, and then once we know what we are about to do we will walk through implementing each of the pieces we discussed.

## 10.1 Why not use another package or service?

A fairly common question I receive is, “Why don’t we just use another package or service that does all this for me?”

The short answer is, without truly understanding what goes into a secure authentication system you might unknowingly write code that causes a security leak. Developers need to be aware of what security measures are necessary to properly store passwords, and only then they can make decisions with confidence that they aren’t making an application insecure.

Another reason for this is customization. In my experience, every site has custom requirements for their authentication system. Some sites require you to use two-factor authentication to log in; others require annual password resets without repeating any old passwords. There is no shortage of random criteria that can be added to your authentication system.

Not only will you need to customize your authentication system over time, but these customizations often make it impossible to plug an off-the-shelf solution into your web application. That, as I said before, customizing without knowing what may or may not make the entire system insecure is a bad idea.

In addition to benefiting from the knowledge you will gain building your own authentication system, you very well may end saving time by writing your own authentication system. While this may seem crazy at first, customizing a package someone else means learning how it works so that you can add in your tweaks. This takes time, and often times you can build an authentication system from scratch in a similar amount of time, but you will definitely understand how your system works because you wrote it.

## 10.2 Secure your server with SSL/TLS

And finally, using services like Auth0 and Stormpath add an additional cost to your bottom line. I'm not saying they aren't worth that additional cost. They definitely are in some situations, but many people reading this book are looking to build a small side project application, and it is hard to keep a side project running when it costs hundreds of dollars every month.

If your website stores any sort of user data, you should strongly consider getting a certificate for your site so it can be served by https instead of http. Once you have a certificate, you should redirect all of your web traffic to the https version of your site. This is especially true if you are going to allow users to create accounts and provide you with a password, as otherwise their password would be sent to your server without any encryption.

We won't actually get to this step until later in the book when we prepare for production and deploy our application, but this chapter would feel incomplete if I didn't at least mention that SSL is a requirement for a proper authentication system.

## 10.3 Hash passwords properly

The most common mistake when building a custom authentication system is to choose a bad way to store a user's password in your database.

As a general rule, if you can decrypt the password, you are making a bad mistake. It doesn't matter what your use case is, or what awesome service you are working on; If you can decrypt a user's password, then an attacker can decrypt it as well.

Now that might seem confusing at first. If you can't figure out what a user's password is is, can you verify their password when they log in?

That, my friends, is where hash functions come into the equation.

### 10.3.1 What is a hash function?

A hash function is a function that can be used to take data of any arbitrary size and convert it into data of a fixed size.

The act of applying a hash function is often called “hashing”, and the values returned by a hash function are often referred to as hash values or hashes.

Hashes are useful in a wide variety of programming applications, and I definitely recommend doing some researching and reading up on them in your spare time, but for our purposes we are going to briefly look at a simpler example, then focus exclusively on bcrypt, a hash function designed explicitly for hashing passwords.

For our simple example, imagine a function that takes any string value and translates it into a number between 0 and 4. One way to implement this is to just count the number of letters in the string and then use the modulus (%) operator to get a number between 0 and 4.

Listing 10.1: A fake hash function

```go
// Do not code this
func hash(s string) int {
  return len(s) % 5
}
```

While this might not be a great hashing function, it does illustrate key points that we need to discuss.
