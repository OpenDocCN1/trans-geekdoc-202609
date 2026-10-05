# Hacking Multifactor Authentication

disguise. It masqueraded as a Chinese TOTP app known as MinaOTP. It appears to have been loose in the wild for three weeks before being discovered and revealed. You can't trust every MFA vendor to be scrupulous.

# Hackers Turn MFA to Defeat You

In 2020, Brian Krebs reported (krebsonsecurity.com/2020/turn-on-mfa-before-crooks-do-it-you) the story of a victim whose son had his Microsoft Xbox account taken over. As the father, a career IT security professional, tried to regain control of his son's account, he contacted Microsoft tech support, which like a lot of tech support, is reachable only through email or online. The man started through the automated tech support reports to report the malicious takeover and to initiate the steps to regain control of the account. While doing this, he learned that any account changes would be sent to a rogue Gmail account, set up by the attackers, for approval. Not only that, but the attackers had up MFA protection so that the legitimate users could not regain control without having access to the newly selected, rogue MFA protection instance.

Microsoft sent him a list of 20 increasingly sophisticated known questions, similar to what I revealed in Chapter 13, "Downgrade/Recovery Attacks," such as the serial number of his Xbox console. Even though he answered all 20 questions successfully, Microsoft refused to reset the account to his control because they did not have the (rogue) MFA option as the last confirmation. Microsoft had apparently never considered the scenario of an attacker enabling MFA after account takeover. After much wrangling, the victim had to create a new Xbox account (again, Microsoft had no way of recovering the original without the victim knowing the attacker's MFA code), and they were able to transfer his son's account and information to the new account. I guess the moral of the story is to enable MFA before the attacker does.

# Summary

This chapter discussed eight miscellaneous MFA attacks. Chapter 21, "Test: Can You Spot the vulnerabilities?" will explore real life MFA solution to complete all the examples of real-world and theoretical MFA attacks explored in Part II, "Hacking MFA". Also, chapter 21 will cover a secure and sophisticated MFA hardware device and ask if you can spot the potential vulnerabilities.