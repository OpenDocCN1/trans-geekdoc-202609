# Chapter 2 Authentication Basics 55

Good auditing is crucial for good security. Without auditing I might not know that someone is trying to guess the password of a single user and is using over a different password guesses in that attempt. An even better configured event log system would notice and alert on an attacker doing a "credential stuffing" attack where they are using all available user accounts to guess against thousands of passwords, but never for any one using the environment's account policy.

These four major authentication components—identity, authentication, authorization, and accounting—are traditionally known as the 4A's of authentication (ignoring the fact that identity can also be known as account management, but that is a legacy term that does not encompass the full range of responsibilities).

Most of MFA hacks that this book will cover are breaks in the individual components of these systems (identity, authentication, authorization, and accounting), or taking advantage of a weakness between the steps. More on that in Chapter 5, "Hacking MFA in General."

All of these we've discussed so far lead to a more complete understanding of the authentication life cycle and all of its phases. Figure 2.7 shows a pictorial snapshot of the authentication life cycle in some of its more complicated glory and associated terms. In general, a subject enrolls with a credential service provider and undergoes identity proofing by successfully submitting one or more required authentication factors. If the subject successfully authenticates to the credential provider, they become a subscriber of that identity provider. A subject trying to log on somewhere is known as a claimant. A claimant that successfully passes authentication to a verifier becomes a subscriber to the verifier andor relying party. A subject/subscriber trying to access a relying party's protected resource(s) undergoes authorization using access control. Behind the scenes, every action is likely being audited in an event log.

![](bbox=[0.094, 0.617, 0.715, 0.876])

**Figure 2.7:** Example of authentication life cycle phases