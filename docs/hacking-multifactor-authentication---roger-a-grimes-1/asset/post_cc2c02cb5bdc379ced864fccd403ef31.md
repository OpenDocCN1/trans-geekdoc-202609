
## Chapter 22 Designing a Secure Solution

### Miscellaneous

There are lots of other considerations necessary for a real-world MFA online voting implementation, not the least of which is funding. A world of secure online remote voting is not cheap. Someone (e.g., voter registration office, City Council, federal, state, or local government, etc.) has to buy the devices and give them away for free. Someone has to build the infrastructure, ongoing operations, and tech support.

Not all people have computers or the ability to use computers. How can special needs and disabled individuals vote? There will need to be alternative voting methods for them, or the MFA device and experience will have to handle all types of disabilities. Will there be multilingual support? How long will version of a device be handled? How can we handle power outages, Internet outages, cell phones, and so forth? Will alternative methods of voting lead to other types of hacking?

Send me comments and recommendations for my secure online remote voting MFA device to roger@annerets.com.

Even with best efforts to prevent hacking, this theoretical, ultra-secure MFA device could be hacked, potentially in several ways. But security is binary, and anything we do to decrease malicious intention is good. The primary objective of a remote online voting implementation would be to create a highly secure solution that allowed more voters to participate in the process with less hassle and with fewer errors and hacks compared to the existing systems. From a security perspective, if remote electronic voting actually resulted in fewer fraudulent votes (or rates per voters), it would be beneficial. It doesn't have to be perfect.

### Summary

The chapter covered how to build a secure MFA device that would allow secure online voting. We discussed the use cases and did some threat modeling. From these scenarios, we developed a descriptive model for what we think is a highly secure MFA device for secure online voting.

Chapter 23, "Selecting the Right MFA Solution" will discuss how you can pick the right MFA solution for your organization.

Hacking Multifactor Authentication, First Edition, Roger A Grimes.
© 2021 Roger A Grimes. Published 2021 by John Wiley & Sons, Inc.

## 23 Selecting the Right MFA Solution

This chapter will cover how to pick the right MFA solution for your organization and needs. We'll proceed as if you are tasked with choosing your organization's future MFA solution. You'll find dozens of questions and requirements, in checklist form, which you can use during any MFA evaluation project; a list of MFA vendors you can research; a summary plan outline; and a link to a spreadsheet that lists over 115 MFA vendors, along with a summary of their particular features and options. This chapter will give you a leg up in evaluating MFA solutions for you.

### Introduction

One of the most common questions I get from people who have my MFA presentations or read my related articles is, “What MFA solution should I get?” Let’s start off by setting expectations for this chapter. There is no perfect MFA solution that works for everyone. Knowing a little more about your organization, its risk tolerances, applications, and security culture, I can't even begin to have a guess about what would be best for you and your organization.

I know what the question is asking and why. We are super busy and with a hundred other things, and picking the right MFA solution for their company is just one of them. They want someone else, more knowledgeable about MFA, to pick the solution they need out of the hundreds available. They are looking for the one I would personally deem “least hackable.” They want to start their research with solutions the MFA expert most to cut down the learning curve. It’s a plausible strategy. They may even think that I have a solution that I love above all others that I can recommend if only someone asks.

Unfortunately, there isn't really a single solution that works for everyone. What is good for one organization may not work for another. And they are all hackable—in multiple ways. Asking anyone to pick the “right” MFA solution without knowing any of the relevant details is like someone you do not know at all, “What car or house should I get?” A lot of factors go into those sorts of big decisions to make someone happiest, especially if that “someone” is an organization full of people who often value drastically different things.

## Hacking Multifactor Authentication

I have some crucial points to make to anyone considering buying a new MFA solution, not least of which is that all MFA solutions are hackable and no single MFA solution works with everything. We covered the first point well within this book. It's the second point that makes the right MFA solution to start with. If you take the most popular and widely used MFA solutions, they work less with than one percent of the digital world. The most popular MFA solutions are software and hardware TOTP implementations and SMS-based options. You may already use one of them.

Think about the MFA solution you use currently and how many websites, services, and applications you authenticate on a monthly basis. I don't mean just the sites where you purposefully turned on MFA, but all the websites and services you volunteer or are forced to authenticate to each month. These sites use social media, email, instant messaging, banking, health care, insurance, investment, Internet search engines, research, databases, payroll services, software downloads, file sharing, VoIP, remote meetings, government services, blogs, auction/buying, news, educational, financial, wikis, television, video, tax/preparation, package delivery services, pharmacy, magazines, security services, research, ancestry, hotel, airline, car rental, ratings, identity protection, music, conferences, utility, card cards, loans, food, shopping. The average number of sites and services that an average user authenticates is about 190 (www.securitymagazine.com/articles/88475-average-user-has-1-passwords). I've got 176 logons, so I'm above average.

Now, how about many of those websites and services allow MFA. I'm guessing a significant percentage do, although whether that a minority or majority percentage will depend on the person and the sites. But now you will need to ask what MFA solution you use or know about with the most sites that you use in a given month.

At last company, we were lucky. We had a single-signon (SSO) portal that was MFA-protected. Once we logged in using MFA to portal, we could access 24 different applications. That's a pretty good number for a small business. But it's because of the SSO portal and not because of the MFA solution that we used. If I think about how of the 24 applications could have been reduced to two. And there were nearly many sites and services related to doing business for our company (travel, hotel, airline, car, 401k, investments, blogs, etc.) that were not located on the SSO portal that require me to provide entirely different logons. I also had different I/MFA methods for the parking lot, building entry, elevators, and office doors. I think this authentication amalgam experience is normal in most business environments, even in businesses trying to get a single sign-on experience.
