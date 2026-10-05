# Chapter 13 Downgrade/Recovery Attacks 281

```
Here's your new recovery code
\If you ever need to recover access to your account, this code will help. You should print it or write it down, and store it in a safe place. We strongly recommend that you don't store your recovery code on a device.
If you previously had a recovery code, it is no longer valid. Use this new code instead.
Your code is Y9F9H-ECAU7-CWMQ5-33UVY-LUWHP
[Print] [OK]
```

Figure 13.5: Microsoft recovery code

The problem with master codes is that they often expire and securely storing them is difficult to do. Many people are told to back up their backup codes. That makes them exist in two or more places. Google used to tell users on the default backup code to store the backup codes in their wallet. That sounds like a reasonable idea until you realize that backup codes in both downloaded and print contain the Gmail address as well. If an attacker comes across the backup codes, they can use them at anywhere in the world. If the codes do not expire, you can get new codes and cancel the old codes at any time.

> NOTE It is not super easy with Google or Microsoft to find the right place to generate and manage the backup codes. On a good note, it makes it harder for users to learn about and enable them in the first place, but it also makes it harder to recover or disable them.

# Guessing Personal-Knowledge Questions

Of all the ways someone can recover their MFA-protected account, answering perhaps simple, prereistered personal-knowledge questions is the weakest and easiest of hack—so easy, that many people, including this author, believe the traditional way of using them as implemented by most websites had forbidden by law. Several large authentication providers, including Google and Microsoft, have forbidden their simplistic questions on their sites and services.

Sadly, simple personal-knowledge questions have been one of the most popular account recovery methods and have been for decades. They came out of a need for authentication providers to allow users to recover their forgotten passwords without needing human intervention. Before automated self-service account recovery, a user locked out of their account or forgetting their password had to call a human technical support person, explain the problem, and have the tech support person unlock their account and give them a temporary password.

This method worked fairly well when the number of people, including users and technical support people, was small enough that they would likely be familiar with one another (voice recognition