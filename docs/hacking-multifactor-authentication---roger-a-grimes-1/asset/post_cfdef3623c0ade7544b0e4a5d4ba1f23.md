
## 190 Hacking Multifactor Authentication

number, and that phone is now under the control of the hacker and linked to the hacker's cell phone, the SMS message is sent to the hacker instead of the legitimate user. The hacker uses the SMS recovery message to get access to the account. Once the victim's account, they change as much authentication information as they can to prevent the victim from reasserting immediate control.

I have read many stories of victims arguing over with technical support about how the recently changed information was not done by them and how the technical support person had a hard time validating that the person claiming to be the "victim" was really the victim. How is the technical support person supposed to know that the person claiming to be the victim really is, especially if the hacker used secret information that only the legitimate owner was supposed to know in the first place?

NOTE: Here is a 2020 research paper on how easy it is to do SIM attacks: www.issms2fsecure.com/assets/sim_swaps-01-10-2020.pdf.

## Real-Life SIM Swap Attack Examples

Rogue SIM swaps have happened thousands of times, as shown in the news headline examples in Figure 8.6. Some of the world's largest and most notorious have involved SIM swapping. One cryptocurrency millionaire had over $24 million from his crypto-wallet (www.bankinfsecurity.com/att-sued-over-24m-cryptocurrency-sim-hijack-attacks-a-11365) because it relied on SMS-based MFA. He sued AT&T for $224 million because they transferred his SIM without authorization.

![](img/c78b0f79db62998ee317a35df5629d85_212_0.png)

Figure 8.6: Headlines from real-life SIM swap attacks

A SIM-based attack was also used in 2018 to compromise Reddit's company network (www.wired.com/story/reddit-hacked-thanks-to-woefully-insecure-two-factor-setup), an attack that led to Reddit's source code and network login credentials being compromised. Here are other SIM swap attack examples:

- krebsonsecurity.com/2018/08/florida-man-arrested-in-sim-swap-conspiracy
- coolwallet.io/smartphone-crypto-hack
- motherboard.vice.com/en_us/article/a3q7mz/hacker-allegedly-stole-millions-bitcoin-sim-swapping
- krebsonsecurity.com/2018/08/reddit-breach-highlights-limits-of-sms-based-authentication
- blog.knowbe4.com/sim-card-attack-may-affect-over-1-billion-mobile-phones-wide

## SMS Impersonation

SIM swap attacks take at least a bit of advanced knowledge and preparation on behalf of the attacker. But SMS-based MFA solutions are so easy even a child can do it. I can make you an SMS hacker so never go against anyone who hasn't given you permission. The key to SMS impersonation attacks is that SMS is not authenticated to anything other than a phone number and most people do not know if the phone or code is legitimate. Here are some common examples of SMS impersonation.

## Fake Technical Support Messages

Here's how the attack goes:

1. The attacker sends the victim a fake text message, claiming to be from Google Gmail security support (see Figure 8.7), and tells the victim to expect a forthcoming recovery code via SMS from another phone number, which needs to be back in reply to the message.

![](img/c78b0f79db62998ee317a35df5629d85_213_0.png)

Figure 8.7: Fake tech support message

2. The hacker then attempts to log in to your legitimate service, but then acts they do not know the right password to put Gmail in "account recovery" mode (see Figure 8.8).

![](img/c78b0f79db62998ee317a35df5629d85_214_0.png)

Figure 8.8: Example Gmail login by attacker acting like they are the legitimate user and forgotten their password

3. In this example, Gmail first offers to let the attacker/user use their previous password if it is known. An attacker would just click "Try way" to get a list of recovery choices, as shown in Figure 8.9.

![](img/c78b0f79db62998ee317a35df5629d85_214_1.png)

Figure 8.9: Example of Gmail being in “recovery mode” and telling Gmail to let the attacker/user select their recovery method

4. Gmail then offers a selection of options for recovery mode, and the attacker can choose the SMS option which brings up the screen in Figure 8.10.

5. The legitimate recovery code gets sent from the service to the victim’s previously registered phone via SMS (see Figure 8.11).

6. The tricked victim then sends that recovery code back to the originally requesting impersonated message (see Figure 8.12).

![](img/c78b0f79db62998ee317a35df5629d85_215_0.png)

Figure 8.10: Attacker/using to recover the account using the SMS method: Your verification code is 954327

![](img/c78b0f79db62998ee317a35df5629d85_215_1.png)

Figure 8.11: Example of Gmail sending a legitimate recovery code via SMS to the victim

7. The hacker takes the code and types it into the user's legitimate service's recovery prompt that they initiated, gets authenticated to the account, and takes control of.

This is a very common type of phishing scam, although the scammer may claim to be your bank, investment company, PayPal, airline, hotel company, or any other entity with whom you have a membership and financial information. In all cases, they will claim to have detected some rogue activity and claim to be saving you from criminal activity. They will then claim sending you a code via SMS that you need to tell them to verify that “you are who you say you,” and when we tell them that code (sent by your service's legitimate recovery service), they take over your account. This type of scam is likely targeting thousands of people a day and can fool the most skeptical among us. Here are two real-world examples of hack:

- macking/a-scam-targeting-amer-over-the-phone-has-resulted-in-millions-of-dollars-lost-to-hackers-don't-be-the-next-victim/aarJpEj
- nakedsecurity.sophos.com/instagram-phishing-using-2fa-as-a-lie

Even without asking for recovery code, SMS impersonation scams can send potential vulnerabilities to the rogue websites. Here is a real-world story about Paypal scams: nakedsecurity.sophos.com/2020/02/05/paypal-sms-scams-dont-fall-for-them.

NOTE Some Apple engineers have proposed a new SMS standard that would allow users to be sent legitimate recovery codes in SMS that they can simply select to complete the recovery process (www.hackingnews.com/2020/02/apple-engineers-unveils-proposal-to.html). Because the proposed standard relies on the user's previously registered device information, it could potentially mitigate the types of attacks described in.

## SMS Buffer Overflow

You can be sent messages containing malicious URLs, which if opened can try to exploit your cell phone and its software. In most cases, the victim must have some vulnerable piece of software installed that can be taken advantage of the exploit code. This attack method has occurred many times before, although usually it is accompanied by a nation-state. The most famous example to date is Saudi Arabia's exploitation of Amazon CEO Jeff Bezos' cell phone (www.wired.com/story/bezos-phone-hack-mbs-saudi-arabia). In this case, it involved WhatsApp and not SMS, but the modality is the.

In this case, the messaging app was SMS. A journalist was apparently targeted, but he was too suspicious of the message to trust it or click the included link. In stead, he his phone and the message analyzed. The message link pointed to software called Pegasus, was by Israeli company, NGO Group. It would have likely confirmed the journalist's phone. This article includes good detail about what the journalist did to confirm the message was bogus and how he was getting exploited: www.nytimes.com/2020/01/28/reader-center/phone-hacking-saudi-arabia.html.

This article details, along with an excellent screenshot of the original message in its Arabic format: citizenlab.ca/2020/01/stopping-the-press-new-york-times-journalist-targeted-by-saudi-linked-pegasus-spyware-operator.
