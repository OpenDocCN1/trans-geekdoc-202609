
![](img/181571ad74cba0e6a2f38fcd2658651e_163_0.png)

**FIGURE 5.19** Screenshot of the PicoCTF scoreboard and various challenges available.

There is an annual PicoCTF competition which occurs around March each year as well. This is a classic competition where there is a time limit to complete challenges versus the always-open nature of the PicoGym. Competing against others is another fun way to challenge yourself into becoming better at what you do. If you’ve never done it before, it is highly recommended!

## National Cyber League (NCL)

The NCL is a twice-a-year competition for collegiate cyber athletes to represent their school in a set of CTFs. This competition is specifically limited to college students who are taking courses at their school. The NCL is focused on introducing new students to the cyber field, providing hands-on experience, and giving employers a level of familiarity and experience when hiring a candidate. If you are a college student who is eligible to compete in the NCL, it is highly recommended to get started and learn. The community and learning within the NCL are unmatched and drive us as cyber analysts to be better.

## US Cyber Games (USCG)

The USCG is an organization that runs the US Cyber Team which competes in international cyber competitions. The team is comprised of 30 athletes who train, travel, and compete in cyber competitions throughout the season. The competitions are a mix of Jeopardy-style questions and Attack/Defense scenarios.

Open-source Content Management System (CMS) projects tend to have misconfigurations since they are developed for free by others, we can search for some lesser-known CMS software that may not have seen much security testing. Since we are starting to go down our path to learn from experience, open-source projects are fantastic resources for us to evaluate. Our findings can be used to send code updates directly to the developers so that we can help improve the security of the project as a whole.

## Identifying a Project

To find a project, we can start by searching for open-source CMS’s for a specific type of activity or group. By narrowing down the projects, we’re more likely to find a CMS that is very specific and has been less likely to be reviewed by a separate security professional. Some ideas to search for specific software CMS’s are below:

- Billing
- Accounting
- Church Management
- Bowling Management
- Movies
- Restaurant Menu
- Ticketing System
- Calendar Reservation System

These are only scratching the surface of the projects available online. There are hundreds of thousands of different public software projects available on GitHub which are only one **git clone** request away from analysis. Use your imagination to search for a specific project that we can download and attempt to view.

One way to find projects is to search within GitHub. In this instance, I’ve searched within GitHub’s topics to find projects that involve some type of ticketing system. This was found by searching for **ticketing-system** and resulted in 320 separate projects with that tag.

![](img/181571ad74cba0e6a2f38fcd2658651e_167_0.png)

**FIGURE 5.22** Finding projects within GitHub that have the tag of “ticketing-system”. Notice the high amount of stars on the top project; this indicates that it may be more difficult to find vulnerabilities.

The top results in Figure 5.22 show projects that have well over 1,000 stars, which indicates that they are popular and have a much higher chance of already being analyzed for security vulnerabilities. While it is still very possible that they have vulnerabilities, we want to focus on trying to find easier to locate vulnerabilities which gives us a good possibility of getting a CVE. To increase our chances, we need to scroll down to find projects with fewer stars.

However, keep in mind that the MITRE Corporation will only accept CVEs for projects that are used actively in the field. It would be downright silly to create a CVE for a personal project that is not used for an operational capability. As such, we need to find a project that we can prove is used on the Internet and is part of a real threat to users who have the application.

In this case, I’ve scrolled down through the projects and identified a project which is called **movie_ticket_booking_system_php** which has 10 stars indicating that it may be used more frequently on the Internet.

![](img/181571ad74cba0e6a2f38fcd2658651e_170_0.png)

**FIGURE 5.27** Running SQLMap on a live version of the software which shows a SQL injection vulnerability.

After running various tools, we can prove that the exploit is effective on the software and that it is vulnerable to this type of attack. In most cases, it may take longer to find the vulnerabilities and prove their impact, but spending more time working on these items will help them appear faster during your analysis.

## Submitting the CVE

To submit one of the findings we’ve located, we need to visit the CVE website at [cve.org](https://cve.org). Within this page, there is a button to report a CVE. After reviewing the information, if the vulnerability we’re reporting is not covered by a CVE Numbering Authority (CNA), we will click on the MITRE CNA-LR as a CNA of Last Resort to request a CVE. This indicates that the weakness we’re reporting does not fall under an existing CNA and must go through the MITRE system.

A CVE Numbering Authority is a partner organization that helps track and maintain CVEs on behalf of MITRE for the products they are in charge of. For example, Adobe and Microsoft are two large software manufacturers who are registered as a CNA for their products. To identify if a product is covered by a CNA, we can use the search function on the MITRE website. If we find that the product vendor is not listed, we will select the CNA of Last Resort.

![](img/181571ad74cba0e6a2f38fcd2658651e_170_1.png)

**FIGURE 5.28** Requesting a CVE through MITRE as a CNA of Last Resort.

![](img/181571ad74cba0e6a2f38fcd2658651e_171_0.png)

**FIGURE 5.29** CVE submission form on the MITRE website.

Filling out the CVE request form requires very specific information that lists out the vulnerability and the impact that it contains. We must specify the version of the software that is affected, along with any resolved versions if available. The affected component must be clearly labeled to describe where the vulnerability lies within the system as well as to allow others to understand where the risk exists.

When defining the suggested description of the CVE, there are certain key details for phrasing that we must use. Failure to use these descriptions will reduce the likelihood that our CVE will be accepted. Thankfully, the CVE team links resources on using proper phrasing within the CVE submission form itself.

![](img/181571ad74cba0e6a2f38fcd2658651e_171_1.png)

**FIGURE 5.30** Suggested CVE description on MITRE’s website.

Visiting this link at [http://cveproject.github.io/docs/content/key-details-phrasing.pdf](http://cveproject.github.io/docs/content/key-details-phrasing.pdf) brings up a PowerPoint presentation from 2016. This presentation covers why the description is used to separate various CVE entries and provide reporting details within the submission process. Specifically, the description should be formatted in a way that matches something similar to the formats below:

- [VULN TYPE] in [COMPONENT] in [VENDOR] [PRODUCT] [VERSION] allows [ATTACKER] to [IMPACT] via [VECTOR].
- [COMPONENT] in [VENDOR] [PRODUCT] [VERSION] [ROOT CAUSE], which allows [ATTACKER] to [IMPACT] via [VECTOR].

Writing the correct description can be difficult and we need to make sure that we provide enough information for MITRE to make an informed decision about issuing a CVE or not. Make sure that this description reflects the time and effort that we’ve spent finding the CVE and analyzing it. Keep in mind also that MITRE can make adjustments to the submission form once they have been submitted as needed to help with wording.

If we’re lucky enough to have a CVE accepted, we will be notified via email. However, initially, the CVE will be listed in a “reserved” state, indicating that the CVE number has been issued but remains controlled information. The reserved state is to help protect others who use the software/product until a patch is released or a public analysis is published. Keep in mind that since we identified the bug, it is our responsibility to ensure that we responsibly disclose and assist with remediation.

For open-source projects, we can always open a security issue in GitHub, SourceForge, or wherever the repository is hosted. At the same time, we can make the changes to the code in a git branch and submit a pull request, indicating that we have already worked on a fix to resolve the vulnerability. Most open-source maintainers are volunteers who do their development for free, so pushing some of your code to help remediate the risk you identified will be well received. Steps on creating a branch, committing changes, and submitting a pull request are outside the scope of this book but are readily available online.

Once the issue has been resolved through either a patch or some other type of mitigation and has a publicly available disclosure, such as an accepted pull request, we can notify MITRE to request full disclosure of the CVE. This will be accomplished on the same CVE form we submitted the CVE, only that we will select “Notify CVE about a publication”. This will ask for the link to the resource and the affected CVE numbers, as well as any additional description updates if needed.

Once received and processed by the MITRE CVE team, we’ll have our first CVE published and out in the world! Don’t forget to celebrate and continue to pass the knowledge along to help develop a more secure Internet and connected online world.

## Bug Bounties

Finding bugs and vulnerabilities can pay well too! Over the last decade, bug bounty systems have become incredibly popular and have created a conducive environment for hackers to find vulnerabilities for companies willing to pay for these to be found. This also ensures that the hackers don’t use the bugs for personal gain, but rather send them into bounty resources as a legitimate form of reporting and income.

However, bug bounties are *hard*. There is a lot of competition from other hackers since cash money is on the table. As assets are published in programs, hundreds or even thousands of like-minded hackers swarm onto the assets to try and find vulnerabilities. Many of these hackers have well-established tools and methodologies to quickly identify locations that have a higher likelihood of being vulnerable to attacks. The first to report the bug is usually the one who gets the cash, resulting in a mad dash to find bugs when new targets are posted.

Do not be discouraged when starting to hunt for bounties, it is an exceptionally rewarding experience when one is found. Just like everything else, it becomes easier the more you do it as well.

Bounties can be gathered at authorized locations that a company either publishes publicly or within a strictly controlled group of select hackers to target for attacks. These hackers are given permission, within a specific scope, that allows them to attack and try to find weaknesses within an organization. As vulnerabilities are identified, the hackers must prove their impact on the organization and how it can be used to harm them – the higher the impact, the more the bounty pays.

For most programs and platforms, identifying a high-impact vulnerability such as SQL injection or remote code execution can pay up to $10,000 for each finding. Other vulnerabilities in key products for Google and Apple can pay up to a million dollars each – but keep in mind the vulnerability must prove a significant impact to those products.
