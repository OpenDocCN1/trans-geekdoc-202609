# 276 Hacking Multifactor Authentication

# Example Downgrade/Recovery Attacks

I already covered some of these types of attacks in previous chapters, where they were slightly more representative of the particular chapter topic. In Chapter 8, "SMS Attacks," we explored recovery attacks involving SMS. These included the run-of-the-mill fake support SMS messages and fraudulent phone calls, both of which are hard to authenticate. Chapter 11, "Fake Authentication Attacks," covered fake authentication attacks, where the victim is led through a completely fraudulent experience. As previously discussed, these types of experiences are very hard for authentication to vendors. And the previous chapter, Chapter 12, "Social Engineering Attacks," covered multiple social engineering attacks, which allow hackers to bypass MFA protections. All of the previous attack types could be classified as downgrade/recovery attacks, but here are three more common attack types specifically related to recovery issues: alternate email address recovery, master code abuse, and guessing personal-knowledge questions.

# Alternate Email Address Recovery

Most MFA solutions allow an alternate recovery code to be sent to an alternate email address. Most of the time, the alternate email address must be previously registered during the initial registration, but not always. Figure 13.1 shows two examples of alternate email addresses used as account recovery options.

| Account recovery options |
| If you forget your password or cannot access your account, we will use this information to help you get back in. |
| Recovery email | ro****@hotmail.com |
| Recovery phone | |

Microsoft account

# Security code

Please use the security code for the Microsoft account ro****@hotmail.com.

Security code: 0152772.

If you don't recognize the Microsoft account ro****@hotmail.com, you can click here to remove your email address from that account.

**Figure 13.1:** Two examples of alternate email addresses used as account recovery options