
for identifying jobs you may be interested in. It seems like human resources people, specifically recruiters, commonly use LinkedIn to find people to fill positions, whether it's an internal recruiter or someone who works for a recruiting company.

Because of the amount of business information LinkedIn collects, we can make use of it as a hunting platform. Especially with the paid memberships, LinkedIn does a lot of analytics about the businesses that make use of it, as well as the people who are on the site. If you are looking for information about a target, LinkedIn provides a lot of detail. Just as one example, Figure 4.9 shows some statistics about applicants for a position that is open and advertised through the Jobs section of the website. We can see that the position attracts educated applicants. You can start to get a sense for the workforce by looking at these statistics across multiple positions.

### FIGURE 4.9 LinkedIn job statistics

| Category | Details |
| :--- | :--- |
| Seniority level | 98 Director level applicants<br>76 Senior level applicants<br>38 Manager level applicants<br>37 VP level applicants |
| Education | 50% have a Bachelor's Degree<br>31% have a Master of Business Administration<br>11% have a Master's Degree<br>8% have other degrees |
| Location | Greater Denver Area: 182 applicants<br>Greater New York City Area: 6–10 applicants<br>United States, Other Areas: 6–10 applicants |

![](img/421171b17a0c0dfae0aacde15d9831c1_133_0.png)

Job listings are another place to look for details beyond the statistics about applicants and the workforce overall. What we can see from these listings is technology that may be in place within the organization. A listing for a network security engineer has requirements that can be seen in Figure 4.10. While some of these requirements are generic, there are also some that are very specific about the technology in use in the network. For example, it appears that the company may be using CheckPoint and Palo Alto Networks firewalls. Additionally, it has Cisco routers and switches in its network. This is a foothold. We can now starts you can get.

### InSpy Results from an Employee Search

```
$ ins --empspy title-list-small.txt Wiley

InSpy 2.0.3

2018-07-02 16:00:52 59 Employees identified
2018-07-02 16:00:52 Felix R Cabral Sr. Avaya Voice Engineer – Voice Infrastructure
2018-07-02 16:00:52 Uta Goebel Deputy Editor at Wiley VCH
2018-07-02 16:00:52 Janice Cruz (L.I.O.N.) Quality Assurance Analyst at Wiley
Education Solut
2018-07-02 16:00:52 Coral Nuñez Puras Financial Planning and Analyst in Wiley
2018-07-02 16:00:52 Jamie Wielgus Editor at John Wiley and Sons
2018-07-02 16:00:52 Stacy Gerhardt Engineer in Training at Wiley|Wilson
2018-07-02 16:00:52 Martin Graf-Utzmann Editor at Wiley VCH
2018-07-02 16:00:52 James Smith, EIT Mechanical Engineer at Wiley|Wilson
2018-07-02 16:00:52 Mohammad Karazoun Software Test Engineer (Product Analyst)
at John W
2018-07-02 16:00:52 Robert Vocile Strategic Market Analyst at Wiley
2018-07-02 16:00:52 Misha Davidof Senior Business Analyst Consultant at Wiley
2018-07-02 16:00:52 Aleksandr Lukashevich Automation Testing Engineer at John
Wiley and Sons
2018-07-02 16:00:52 Ekaterina Perets, Ph.D. Assistant editor at Wiley
2018-07-02 16:00:52 Guangchen Xu Editor @ Wiley
2018-07-02 16:00:52 Ralf Henkel Editor in Chief at Wiley-Blackwell
2018-07-02 16:00:52 sonal jain Wiley India
2018-07-02 16:00:52 Abhinay Kanneti QA Automation Engineer at Wiley Publishing
2018-07-02 16:00:52 Olga Roginkin, PMP Business Analyst at John Wiley and Sons
2018-07-02 16:00:52 Razi Gharaybeh Senior Quality Assurance Engineer at John
Wiley an
2018-07-02 16:00:52 Daniel Bleyer Senior SCCM Systems Engineer at Wiley
2018-07-02 16:00:52 John Coughlan Senior Project Engineer at Wiley
2018-07-02 16:00:52 Stephanie Hill Production Editor at Wiley
2018-07-02 16:00:52 Jörn Ritterbusch Editor-in-Chief bei Wiley-VCH
2018-07-02 16:00:52 Alden Farrar Assistant Editor at Wiley
2018-07-02 16:00:52 Gilat Mandelbaum Strategy Analyst Intern at Wiley
2018-07-02 16:00:52 Chelsea Meade Pricing Analyst at Wiley
2018-07-02 16:00:52 Babak Mostaghaci Associate Editor at Wiley-VCH
2018-07-02 16:00:52 Vibhushita Misra Testing Analyst/Testing Team Lead at Wiley
2018-07-02 16:00:52 Mohammed Mnayyes Quality Engineer at John Wiley and Sons
2018-07-02 16:00:52 David Kim Associate Editor | Society Journals | Wiley
2018-07-02 16:00:52 Lauren Ellis Project Engineer at Wiley
2018-07-02 16:00:52 Amit Wawdhane Data Analyst at Wiley | Masters in Information Sys
```

InSpy is not the only utility we can use to do automatic searches in LinkedIn. We can also use theHarvester, just as we did earlier. Instead of search sites like Google or Bing, we can indicate LinkedIn as the data source to search in. Fortunately, this is something theHarvester will do without requiring an API key. Many sites will require API keys to
