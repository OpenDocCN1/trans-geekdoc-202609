
# 272 Hacking Multifactor Authentication

that I can think of social engineering and phishing. You can watch it by registering at this link: info.knowbe4.com/webinar-stay-of-the-net.

## Pulling Off Top-Not Security Awareness Training

Security awareness training is supposed to give your coworkers a healthy level of skepticism to recognize, and report social engineering attacks. For years, we wondered how to pull off great security awareness training. I am fortunate enough to be working at the world's number one security training vendor. We have looked at how their customers have deployed security awareness training and determined what methods work best. I will share them with you.

### Publicize the Security Awareness Training Program
Let all your coworkers that you are doing a formal security awareness training program. Explain how you will be doing it and how you expect to participate. Don't surprise anyone. No one ever got promoted for surprising someone, least of senior management. Instead, let everyone know that your regular awareness training and how you will do it. This phase of the system is part of the training.

### Establish a Baseline
Send a simulated phishing email to all your coworkers. Create a phishing email that accurately represents a common phishing email that you've seen before. It is not crafted to be sneaky and hard to recognize. You want to send a phishing test that most people would recognize as a phishing test and not click. You'll likely be surprised by how many people click on this easy-to-spot fish. It is not uncommon for up to 30 percent of employees of an organization to fall victim to a simulated phishing test.

### Train at Least Once a Month
Send your coworkers to some sort of training at least once a month in addition to performing the simulated phishing tests. The training should vary, should be interesting enough that people won't hate it, and should be monthly. Monthly trainings shouldn't be longer than a few minutes each. Ideally, the training would be around current social engineering trends or focus on preventing social engineering for your implemented MFA solution.

### Do Simulated Phishing Tests at Least Once a Month
Send your coworkers a simulated phishing test (or SMS message or voice call) at least once a month. Like the training, the simulated phishing should be focused on current social engineering trends. If someone fails a simulated test, they should be provided with immediate feedback on what they should have noticed it was a phishing (test) and not a legitimate email. As your user base gets better at spotting phishing emails, you can increase the level of sneakiness. You want to ramp up the training as your end-user base knowledge of phishing increases.

### Stay Current on Your Training
Make a priority to keep the social engineering training current up-to-date real social engineering trends. When a world event happens that real phishers are using, model your simulated phishing tests and training after what the phishers are doing.

## Chapter 12 Social Engineering Attacks 273

If you follow these recommendations, you will likely see a significant reduction in the amount of successful social engineering. KnowBe4's average customer who follows these recommendations cuts the percentage of employees who can be easily socially engineered from around 30 percent to 2-5 percent within a year. That's not the best customers or some customers. That's all customers who follow these recommendations.

**NOTE** I cannot recommend a better book on how to craft and deliver the best security awareness training program than the recommendations in my friend and coworker Perry Carpenter's book, *Transformational Security Awareness Training: What Neuroscientists, Storytellers, and Marketers Teach Us About Driving Secure Behaviors* (Wiley, 2019). I also recommend you check out articles published on my current employer's blog website, www.knowbe4.com/resources, which features many useful free tools, whitepapers, and dozens of webinars, including many of mine.

## Summary

This chapter covered social engineering and provided examples of how it can be used to bypass MFA solutions. You learned about common social engineering attributes and how to educate your MFA users against social engineering attacks. Chapter 13, “Downgrade/Recovery Attacks” will explore downgrade and recovery attacks.

# 13 Downgrade/ Recovery Attacks

This chapter will cover additional sneaky ways hackers take advantage to get around MFA solutions focusing on alternative authentication methods vendors provide to recover MFA-protected accounts.

## Introduction

No matter what your MFA solution is, implementing it is more expensive, both initially and ongoing, than traditional logon name and password solutions. If you use MFA, your organization is nearly guaranteed to have increased support calls and costs. It's the nature of using a more involved, complex solution. It takes longer to train people in how to appropriately use MFA solutions. MFA solutions involving additional hardware devices naturally mean those hardware devices will break and be lost or stolen. Even if all your MFA solution uses SMS or an app on a cell phone, that means more support calls and more operational disruption as compared to password-based solutions.

Large-scale MFA solutions with hundreds of thousands of users are challenged with how to provide technical support to all those customers and at the same time keep support costs to an acceptable minimum. Because of this, I've yet to see the large-scale MFA solution that didn't offer a recovery method that ultimately involved something less secure than the MFA it was backing up. I've even seen many MFA solutions that had an admin or user option that enabled the user to "REQUIRE MFA", that in the end didn't allow a logon method that didn't require MFA. Required apparently doesn't always mean required. Ironically, this means that although the legitimate user is using and requiring multifactor authentication, attackers can use something less. I will cover three example downgrade/recovery attacks, one of which is so weak that it should be outlawed.

# 276 Hacking Multifactor Authentication

## Example Downgrade/Recovery Attacks

I already covered some of these types of attacks in previous chapters, where they were slightly more representative of the particular chapter topic. In Chapter 8, "SMS Attacks," we explored recovery attacks involving SMS. These included the run-of-the-mill fake support SMS messages and fraudulent phone calls, both of which are hard to authenticate. Chapter 11, "Fake Authentication Attacks," covered fake authentication attacks, where the victim is led through a completely fraudulent experience. As previously discussed, these types of experiences are very hard for authentication to vendors. And the previous chapter, Chapter 12, "Social Engineering Attacks," covered multiple social engineering attacks, which allow hackers to bypass MFA protections. All of the previous attack types could be classified as downgrade/recovery attacks, but here are three more common attack types specifically related to recovery issues: alternate email address recovery, master code abuse, and guessing personal-knowledge questions.

## Alternate Email Address Recovery

Most MFA solutions allow an alternate recovery code to be sent to an alternate email address. Most of the time, the alternate email address must be previously registered during the initial registration, but not always. Figure 13.1 shows two examples of alternate email addresses used as account recovery options.

| Account recovery options |
| :--- |
| If you forget your password or cannot access your account, we will use this information to help you get back in. |
| Recovery email | ro****@hotmail.com |
| Recovery phone | |

Microsoft account

# Security code

Please use the security code for the Microsoft account ro****@hotmail.com.

Security code: 0152772.

If you don't recognize the Microsoft account ro****@hotmail.com, you can click here to remove your email address from that account.

**Figure 13.1:** Two examples of alternate email addresses used as account recovery options
