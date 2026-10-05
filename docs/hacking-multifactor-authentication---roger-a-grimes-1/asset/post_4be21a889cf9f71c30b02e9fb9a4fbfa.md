
# 504 Hacking Multifactor Authentication

All of this is also done in a way that requires less user friction for normal, usual, low-risk tasks. Perhaps the way MFA and the new authentication framework meet and meld is that a user allowed to seamlessly log on to any website and service they like without anything traditionally think of authentication being needed. No login name. No password. No MFA needed. The session originating from the user's normal device, location, and time is all that is needed to gain initial access. Is the user doing their regular tasks in a normal manner? Are they accessing the services normally and in the order they normally access them? The user's keyboard and mouse-click activity are evaluated during the rest of the session to determine if the user's actions are normal and natural. And if the user goes to do something of high value or risk, then maybe they be prompted to use their MFA solution (i.e., step-up authentication).

There are many authentication services (like those at Google and Microsoft) that already look at hundreds of user sessions to determine whether the user is who they say they are and are doing what they want to. The future of authentication, regardless of implementation, is likely to look continuously at dozens of user session traits, including these:

- * User ID
- * User login method (password vs., MFA, etc.)
- * Defined role (user vs. admin, etc.)
- * User actions (normal, usual, timing, moving around site normally)
- * Day/time
- * User action. user account history
- * Device ID (preregistered or familiar devices lower risk)
- * Location (physical, IP address, trusted network)
- * Behavioral traits
- * Contextual clues
- * Keyboard/mouse activity analytics

The whole time the authentication system is continuously evaluating the user session's risk score. It points for increase risk and subtracts points for characteristics that decrease risk. If a user's session exceeds a particular risk value score, the system can decide between different risk mitigation outcomes, including these:

- * Continues to allow access as is
- * Continues to allow access as is but increase monitoring
- * Prompts user for step-up authentication
- * Denies user a specific action they are attempting
- * Allows the user action, but an additional system or human is used to confirm validity potential damage can be reversed
- * Kills action/access or does a forced logout of the user

# Chapter 24 The Future of Authentication 505

The whole time you have a threat analytics engine determining how particular traits, characteristics, or actions equate to particular risks. This means the engine has to know the risk from past user actions and newly developing risks and traits that are being learned. For example, a user who is normally logging in from the United States is detected as coming from Romania for this logon session, and the system has been made aware of a slew of Romanian-based account takeovers that have been detected in the last few hours. This sort of adaptive approach to authentication requires that the system has a set of built-in, updatable rules, and ML or AI to help predict developing threats. Figure 24.3 shows a graphical summary of the various main components of a continuous, adaptive, risk-based authentication system.

![](img/c78b0f79db62998ee317a35df5629d85_515_0.png)

**Figure 24.3:** The main components of a continuous, adaptive, risk-based authentication system

# Hacking Multifactor Authentication

Many of us are already quite familiar with similar authentication systems today: credit cards. Our credit card vendors allow us to go around the country (sometimes the world) spending our money to our heart's content. Most of the time we can complete our purchases with little hassle. But sometimes, when the credit card's backend risk analysis engine detects a higher-risk event, your credit card company calls you or sends an SMS message asking you to confirm a particular transaction before they allow it to proceed. For many people, additional transaction 'friction' happens only once or a few times every years. More than that and your credit card vendor will start to worry that you're going to change credit cards.

Sometimes your credit card vendor detects your card being used in an anomalous way that you are not aware of. Your credit company detects this activity, cancels your card, avoids any rogue transactions, and sends you a message before any of anomalous activity. And sometimes, you detect the anomalous activity before the credit card company does, and you initiate the process. The latter scenario is happening less and less as time goes on because the credit card risk analytics engines are improving so much. Expect to see all digital authentication move closer to what we've already been using with credit cards, except that MFA may be instead of a call or SMS message from the vendor.

# Quantum-Resistant Cryptography

I would be remiss if I didn't mention that the current asymmetric ciphers that our authentication systems use and rely on (RSA, Diffie-Hellman, Elliptic Curve Cryptography, etc.) will be replaced in the next few years with quantum-resistant cryptography. If you are interested in learning more, check out my book Cryptography Apocalypse: Preparing for the Day When Quantum Breaks Today's Crypto (Wiley, 2019).

The future of authentication is continuous, adaptive, risk-based, and stepped-up, and with less user friction.

# Interesting Newer Authentication Ideas

The authentication field is full of constantly changing vendors and ideas. Here are some of the ones I've come across recently. Only time will tell me if some of these ideas are involved in the authentication of the future, but they are worth a quick investigation:

- Keystroke, mouse, and touchscreen dynamics (intensityanalytics.com)
- Proximity-based hardware tokens (gkaccess.com/products/halberd)
- Proximity-based MFA using phones (www.whitecyber.com)

I've seen some fantastic ideas and solutions. With that said, I've been contacted by over 100 brand-new authentication vendors over the last two years, all of which believe they have an idea that Chapter 24 The Future of Authentication will take the world by storm, if only they can get enough press and publicity. And perhaps that is true. Some of the solutions are very good. But it's very tough to get the computer world to notice your new product. Unfortunately, I don't think a single new vendor that contacted me over the last two years has survived or significantly expanded. The authentication world is super competitive and eats its.

But hopefully I've covered the traits that I think the future of authentication is going to involve, so if you see an authentication backend solution involving continuous, adaptive, and risk-based authentication, at least you know they are on the right track. And for the next 10 years or more, the MFA I've covered in this book will provide that extra layer of security when it's desired.

# Summary

This chapter covered how authentication will look in the next 10 years and after. We began by discussing what is staying the same and what is changing regarding cybercrime, and then we did the same for authentication.

Chapter 25, “Takeaway Lessons” will recap the individual and larger lessons readers should take away from this book.

# Takeaway Lessons

This chapter will recap the individual user and developer defenses provided by the various MFA solutions shared in the previous chapters and discuss the lessons readers need to take away from this book. We'll start with the broader lessons first.

# Broader Lessons

This section covers general takeaways from all MFA solutions.

# MFA Works

In a book dedicated to hacking MFA, some readers may come away with the idea that MFA is bad or not worth using. Let me be clear: MFA decreases cybersecurity risk in many use cases, especially general account takeover (ATO) scenarios. But there is a difference between decreasing risk in many scenarios and MFA not being hackable.
MFA stops hacking in many scenarios, especially phishing attacks that ask for the user's passwords and then uses fraudulently obtained credentials to log on to the victim's legitimate sites and services. If you don't have a password to be stolen it will not work against you. MFA also stops many types of traditional attacks against sites and services that require MFA for login. Unless an intruder finds a way around the MFA requirement in those scenarios, MFA decreases risk.
Multiple studies have shown that MFA is good at stopping widely broadcast, general, credential phishing attacks, including these:

- security.googleblog.com/2019/05/new-research-how-effective-is-basic.html
- techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Your-Pa-word-doesnt-matter/ba-p31984
- docs.microsoft.com/en-us/azure/security/fundamentals/steps-secure-identity
