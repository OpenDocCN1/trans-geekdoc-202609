
```go
cookie := http.Cookie{
  Name: "remember_token",
  Value: user.Remember,
  HttpOnly: true,
}
```

This will tell our cookie that it is not accessible to scripts. If you were to view the cookie in Google Chrome like we did earlier, you would see something like this in the cookie:

Accessible to script: No (HttpOnly)

This means that the cookie isn’t accessible for scripts run in the browser.

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

- Completed - book.usegolang.com/11.9
- Changes - book.usegolang.com/11.9-diff

# 11.10 Securing our cookies from theft

The next attack vector we are going to discuss is cookie theft. There are two potential ways to steal cookies, and we will discuss both briefly.

The first way to steal cookies is via packet sniffing, and this occurs when some-one manages to intercept your web requests and steal data from them before forwarding them along to where they were intended to go. This one is tricky because you might not even realize someone stole your data if they forward your request along and you continue to get a response as expected.

The second, theft via physical access, is exactly what it sounds like. It occurs when someone has physical access to your computer, laptop, or some other hardware and steals a cookie from it.

The only real solution to the first type of theft is to make packet sniffing isn't a viable option for attackers, which means making sure your application is served over SSL/TLS. This is why any people are pushing for always using https on your website these days - is relatively easy to do, can make your website faster, and helps prevent hard-to-detect attacks.

If your website doesn't have https (the s the important bit) in the URL bar when people visit it, you are not secure from this. We will discuss how to do this later when we talk about deploying our application to production, but keep this in mind if you consider alternative deployment methods than what we discuss in this book as you will want to make sure your site is secure.

Box 11.9. A cookie theft example

While theft of cookies via packet sniffing might not seem like a serious concern, a developer named Eric Butler shed a lot light on the issue when he published a Firefox extension named Firesheet which demonstrates just how easy this attack is to administer.

With the extension installed, all anyone needs to connect is a busy wifi network. If anyone else on that network visits a site that Firesheet recognizes and does so over an insecure connection, Firesheet would show the user's name and the service they connected to on the left. After that, all an attacker needs to log in as that user is double click on the user and Firesheet would instantly log them in as that user.

Lastly, we have physical theft which we really can't prevent on our end. If someone manages to access someone's physical hardware, it is virtually impossible to detect, but what we can do is make it easy for a user to invalidate all existing sessions. Luckily, our application already does this by changing the RememberToken time a user logs in. All a user needs to log in with a new device and those cookies will be invalidated.

Note: There are alternatives to this approach that are as secure as secure, but most of these involve using session expirations and are a little more complicated.

# 11.11 Preventing CSRF attacks

CSRF attacks are a potential attack that occurs when a website creates a form that submits false data to a different website. For example, a nefarious site might have a form that submits a fake money transfer to your banking website.

This works because from the server's perspective it looks like you initiated the web request yourself because you clicked a button and submitted the form.

To prevent this we will eventually implement something known as CSRF tokens, but that won't happen until later in the book when we prepare our application for production. I am telling you about it now you so you understand why you shouldn't deploy your application until then.

# 11.12 Exercises

At this point most of your authentication system should be in place, so it is time to review a few exercises to test your understanding of the material.

## 11.12.1 Ex1 - Experiment with redirection

In our cookie test we show an error when the user isn’t logged in. Try to update it or another handler function to redirect the user to the login page instead when this happens, much like we in our final version of the application.

## 11.12.2 Ex2 - Create cookies with different data

Cookies can be used for storing all sorts of data so long as it isn’t sensitive data. For example, if you need to redirect a user to the login page, you could store the page they were coming from and send them back to that page after they log in. Try creating a few different cookies and validating that they are being set correctly.

## 11.12.3 Ex3 - [HARD] Experiment with the hash package

We used the hash package in the standard library a bit, but we didn’t get to explore it too much. Try experimenting with different portions of the standard library’s hash package and get a better sense for what is available there.

# Chapter 12

# Normalizing and validating data

In this chapter our primary focus is going to be validating and normalizing data. In the process we will also look at cleaning up our code a bit and coming up with a nice code structure, but this will all be done in an effort to improve our validation code.

Before we can really jump into writing any code we need to first discuss validation and normalization are, so we will start here.

### What are validation and normalization?

Validation can mean different things to different people, but in the context of web development it most commonly refers to verifying that data is in an acceptable state. For example, we might want to verify that email address is valid, or that it is not taken by another user. Or we might want to verify that every user has a password with at least eight characters in it.

Similarly, normalization is a term that can mean different things depending on the context; when we look at normalizing our data we are talking about making sure our data is in the format we expect, and if not attempting to transform it into that format. For example we might verify that a phone number matches the format we expect before persisting it in our database, or we might convert all email addresses to their lowercase equivalent.

The reasons for using validation is much more obvious than normalization. We clearly need to verify that data is valid, but why do we care about the format of phone numbers? Does it really matter?

Imagine we are storing each user's phone number in our database. If we didn't normalize the data, we might end up with a table with data similar to below.

| user_id | phone_number |
|---|---|
| 1 | (123) 456-7890 |
| 2 | 123-456-8989 |
| 3 | 12345699999 |

Now imagine that we wanted to search for a user by their phone number. Perhaps we needed a support call, and we go to know which account is linked to that phone number. When we go to search we run into a problem - how do we search for a phone number when they are all stored in a different format? Despite that phone number “1234567890” existing in our database, searching for it in that format wouldnt return any result because it is in a different format.

If we were to instead normalize our data, we could write code that takes in any format and trims everything except the digits. That would leave us with a database that much easier to search.

| user_id | phone_number |
|---|---|
| 1 | 1234567890 |
| 2 | 1234568989 |
| 3 | 12345699999 |

It also makes other features, like formatters, easier to write, because they can always assume the data is in a consistent format. Converting “1234567890” to “(123) 456-7890” is fairly easy to do, but if we had to deal with many different-formats and convert each to the “#### format it would become much harder.

Note: When we talk about normalization we ARE NOT talking about normalization that you might hear about when learning SQL. That form of normalization revolves around avoiding duplicate/unsynced data in your database. We won't be covering that.

While validation and normalization are not the same, the two are very tightly linked. For starters, it is very hard to separate the two entirely. Whenever we want to verify an email address isn't taken we need to first normalize it, then search our database for a user with that email address. If we didn't normalize first we might end trying to create two users with the same email address. In this case we are doing normalization first, then validation, but there are also cases where we must validate data first, then normalize it. One instance of this is validating a password has a minimum length; we can't tell how long an original password is once it is hashed (normalized), so we need to validate it first, then normalize it.

This tends to lead to a common pattern where we don't perform one then the other, but instead create a sort of sandwich:

- 1. Some normalization
- 2. All validations
- 3. Remaining normalizations

As a result of the tight dependency between the two, we will be keeping all of this code together in our application.
