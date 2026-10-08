# Compromised Server

Although the effects of a compromised server can include the effects of many of the threats previously listed, it is still worth noting that sometimes the goal of invaders is to gain access to our system, most often as a super user (administrator on Windows-based systems and root on Unix-like systems). With this, they have nearly free rein over the compromised computer and can execute any program they want, shut the computer off, or install software.

We want to be particularly vigilant against this type of attack because one of the first attackers are likely to do it after they have compromised a server is to cover their tracks to hide the evidence.

# Reducing the Risks

Protecting against server compromise requires an approach called defense-in-depth, which we will discuss in more detail in Chapter 15. In summary, means thinking about all the possible things that could go wrong in different aspects of a system, and putting in layers of protection for each aspect.

One mitigation strategy worth mentioning here is the use of an Intrusion Detection System (IDS) such as Snort. These are used to monitor and alert for network traffic that looks like an attack.

# Repudiation

The final risk we will consider is reputation. Repudiation occurs when a party involved in a transaction denies having taken part. E-commerce examples might include a person ordering goods off a website and denying having authorized the charge on their credit card, or a person agreeing to something in it and claiming that somebody forged the email.

Ideally, financial transactions should provide the peace of mind of nonrepudiation to both parties. Neither party could deny their part in a transaction, or, more precisely, both parties could conclusively prove the actions of the other to a third party, such as a court. In practice, this rarely happens.

# Reducing the Risk

Authentication provides some surety about whom you are dealing with. If issued by a trusted organization, digital certificates of authentication can provide greater confidence. The certificate authentication system has some flaws, but it's the current standard.

Messages sent by each party also need to be tamperproof. There is not much value in being able to demonstrate that Corp Ltd sent you a message if you cannot demonstrate that what you received was exactly what the company sent. As mentioned previously, signing or encrypting messages makes them difficult to surreptitiously alter.

For transactions between parties with an ongoing relationship, digital certificates together with either encrypted or signed communications are an effective way of limiting reputation.