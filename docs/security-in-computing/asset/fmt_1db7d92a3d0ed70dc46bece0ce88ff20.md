
## Dynamic Token Generators

Dynamic token generators are useful for remote authentication, especially of a person to a computer. An example of a dynamic token is the SecurID token from RSA Laboratories, shown in [Figure 2-6](#ch02.html#ch02fig06). To use a SecurID token, you enter the current number displayed on the token when prompted by the authenticating application. Each token generates a distinct, virtually unpredictable series of numbers that change every minute, so the authentication system knows what number to expect from your token at any moment. In this way, two people can have SecurID tokens, but each token authenticates only its assigned owner. Entering the number from another token does not pass your authentication. And because the token generates a new number every minute, entering the number from a previous authentication fails as well.

![Image](graphics/02fig06.jpg)

**FIGURE 2-6** SecurID Token (Photo courtesy of RSA, the security division of EMS and copyright © RSA Corporation, all rights reserved.)

We have now examined the three bases of authentication: something you know, are, or have. Used in an appropriate setting, each can offer reasonable security. In the next sections we look at some ways of enhancing the basic security from these three forms.

## Federated Identity Management

If these different forms of authentication seem confusing and overwhelming, they can be. Consider that some systems will require a password, others a fingerprint scan, others an active token, and others some combination of techniques. As you already know, remembering identities and distinct passwords for many systems is challenging. People who must use several different systems concurrently (email, customer tracking, inventory, and sales, for example) soon grow weary of logging out of one, into another, refreshing a login that has timed out, and creating and updating user profiles. Users rightly call for computers to handle the bookkeeping.

A **federated identity management** scheme is a union of separate identification and authentication systems. Instead of maintaining separate user profiles, a federated scheme maintains one profile with one authentication method. Separate systems share access to the authenticated identity database. Thus, authentication is performed in one place, and separate processes and systems determine that an already authenticated user is to be activated. Such a process is shown in [Figure 2-7](#ch02.html#ch02fig07).

![Image](graphics/02fig07.jpg)

**FIGURE 2-7** Federated Identity Manager

***

**Federated identity management unifies the identification and authentication process for a group of systems.**

***

Closely related is a **single sign-on** process, depicted in [Figure 2-8](#ch02.html#ch02fig08). Think of an umbrella procedure to which you log in once per session (for example, once a day). The umbrella procedure maintains your identities and authentication codes for all the different processes you access. When you want to access email, for example, instead of your completing a user ID and password screen, the single sign-on process passes those details to the email handler, and you resume control after the authentication step has succeeded.

![Image](graphics/02fig08.jpg)

**FIGURE 2-8** Single Sign-On

The difference between these two approaches is that federated identity management involves a single identity management module that replaces identification and authentication in all other systems. Thus all these systems invoke the identity management module. With single sign-on, systems still call for individual identification and authentication, but the umbrella task performs those interactions on behalf of the user.

***

**Single sign-on takes over sign-on and authentication to several independent systems for a user.**

***

## Multifactor Authentication

The single-factor authentication approaches discussed in this chapter offer advantages and disadvantages. For example, a token works only as long as you do not give it away (or lose it or have it stolen), and password use fails if someone can see you enter your password by peering over your shoulder. We can compensate for the limitation of one form of authentication by combining it with another form.

Identity cards, such as a driver’s license, often contain a picture and signature. The card itself is a token, but anyone seeing that card can compare your face to the picture and confirm that the card belongs to you. Or the person can ask you to write your name and can compare signatures. In that way, the authentication is both token based and biometric (because your appearance and the way you sign your name are innate properties of you). Notice that your credit card has a space for your signature on the back, but in the United States few merchants compare that signature to the sales slip you sign. Having authentication factors available does not necessarily mean we use them.

As long as the process does not become too onerous, authentication can use two, three, four, or more factors. For example, to access something, you must type a secret code, slide your badge, and hold your hand on a plate.

Combining authentication information is called **multifactor authentication**. Two forms of authentication (which is, not surprisingly, known as **two-factor authentication**) are presumed to be better than one, assuming of course that the two forms are strong. But as the number of forms increases, so also does the user’s inconvenience. Each authentication factor requires the system and its administrators and the users to manage more security information. We assume that more factors imply higher confidence, although few studies support that assumption. And two kinds of authentication imply two pieces of software and perhaps two kinds of readers, as well as the time to perform two authentications. Indeed, even if multifactor authentication is superior to single factor, we do not know which value of `n` makes `n`-factor authentication optimal. From a usability point of view, large values of `n` may lead to user frustration and reduced security, as shown in [Sidebar 2-13](#ch02.html#ch02sb13).

## Secure Authentication

Passwords, biometrics, and tokens can all participate in secure authentication. Of course, simply using any or all of them is no guarantee that an authentication approach will be secure. To achieve true security, we need to think carefully about the problem we are trying to solve and the tools we have; we also need to think about blocking possible attacks and attackers.

***

### Sidebar 2-13 When More Factors Mean Less Security

Dave Concannon’s blog at [www.apeofsteel.com/tag/ulsterbank](http://www.apeofsteel.com/tag/ulsterbank) describes his frustration at using Ulsterbank’s online banking system. The logon process involves several steps. First, the user supplies a customer identification number (the first authentication factor). Next, a separate user ID is required (factor 2). Third, the PIN is used to supply a set of digits (factor 3), as shown in the figure below: The system requests three different digits chosen at random (in the figure, the third, second, and fourth digits are to be entered). Finally, the system requires a passphrase of at least ten characters, some of which must be numbers (factor 4).

![Image](graphics/071fig01.jpg)

In his blog, Concannon rails about the difficulties not only of logging on but also of changing his password. With four factors to remember, Ulsterbank users will likely, in frustration, write down the factors and carry them in their wallets, thereby reducing the banking system’s security.

***
