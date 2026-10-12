
## 5. Refer to the results of Turow’s survey on shopping on the Internet in [Section 9.5](#ch09.html#ch09lev1sec5)

Many people thought certain common practices of Internet commerce were illegal. Should a law be passed to make those illegal? Why or why not?

## 6. Discuss the algebra of authentication and its implications for privacy

That is, assume a situation with two-factor authentication, and call the factors A and B. Consider the four cases in which each one is strong or weak. What conclusions would you draw about the results: weak A and weak B; weak A and strong B; strong A and weak B; strong A and strong B? Does order matter? Does it matter if both factors are of the same type (what you know, what you have, what you are)? What happens if you add a third factor, C?

## 7. You have forgotten your password, so you click on “forgot my password” to have a new password sent by email

Sometimes the site tells you what your password was; other times, it sends you a new (usually temporary) password. What are the privacy implications of each approach?

## 8. Present arguments for and against having a so-called aging function for personal Internet data

That is, some postings might be automatically removed after one month, others after one year, others after one decade. Is this a feasible way to ensure privacy? Why or why not?

## 9. Is it ethical for a school to make videos of students using school-provided computers outside of class?

What ethical principles would justify such monitoring? Would the school be similarly justified in recording all web behavior? All keystrokes? Support your arguments with ethical principles, not just personal opinion.

## 10. Describe a situation in which the source of information is more sensitive than the information itself

Explain why the sum of sensitive data might also be sensitive.

## 11. Suggest a design for a filter that would distinguish queries revealing sensitive data about the inquirer from those that do not reveal anything

What qualities might indicate that a query was sensitive?

## 12. Find three websites that publish their privacy policies

Compare their policies. Which offers the most privacy, and under what circumstances? Which offers the least? How can privacy be improved at each site? How can you tell that the stated privacy policy has been implemented completely and correctly?

## 13. Is legal protection an effective countermeasure for privacy intrusion?

Explain the difficulties or efficacy of using the law to provide privacy protection.

## 10. Management and Incidents

***

In this chapter:

- Security planning
- Incident response and business continuity planning
- Risk analysis
- Handling natural and human-caused disasters

***

In this chapter we introduce concepts of managing security. Many readers of this book are, or will be, practitioners or technologists, people who design, implement, and use security. Devices, algorithms, architectures, protocols, and mechanisms are important for those readers.

Some technologists think security involves just designing a stronger (faster, better, bigger) appliance or selecting the best cryptographic algorithm. That these are important considerations is true. But what if you build something that nobody adopts? Perhaps the user interface is inscrutable. Or people cannot figure out how to integrate your product into any existing system. Maybe it doesn’t really address the underlying security problem. Perhaps it is too restrictive, preventing users from getting real work done. And maybe it is or seems too expensive. Technology—even the best product—has to be used and usable.

In this chapter we consider two important topics: how security is managed and how it is used. These topics relate to human behavior, and also the business side of computing. We also address the physical side of security threats: natural disasters and those caused by humans.

### 10.1 Security Planning

Years ago, when most computing was done on mainframe computers, data processing centers were responsible for protection. Responsibility for security rested neither with the programmers nor the users but instead with the computing center staff itself. These centers developed expertise in security, and they implemented many protection activities in the background, without users having to be conscious of protection needs and practices.

But beginning as far back as the 1980s, the introduction of personal computers and the general ubiquity of computing have changed the way many of us work and interact with computers. In particular, a significant amount of the responsibility for security has shifted to the user and away from the computing center. Alas, many users are unaware of (or choose to ignore) this responsibility, so they do not deal with the risks posed or do not implement simple measures to prevent or mitigate problems.

You have probably seen many common examples of this neglect in news stories. Moreover, neglect is exacerbated by the seemingly hidden nature of important data: Things we would protect if they were on paper we ignore when they are stored electronically. For example, a person who carefully locks up paper copies of company confidential records overnight may leave running a personal computer on an assistant’s or manager’s desk. We access sensitive data from laptops, smartphones, and tablets, which we leave on tables and chairs in restaurants, airports, and bars or coffee shops. In this situation, a curious or malicious person walking past can retrieve confidential memoranda and data. Similarly, the data on laptops and workstations are often more easily available than on older, more isolated systems. For instance, the large and cumbersome disk packs and tapes from years ago have been replaced by media such as diskettes, CDs, DVDs, flash drives, and solid-state disks, which hold a huge volume of data but fit easily in a pocket or briefcase. Moreover, we all recognize that a single CD or DVD may contain many times more data than a printed report. But since the report is an apparent, visible exposure and the disk is not, we leave the computer media in plain view, easy to borrow or steal.

In all cases, whether the user initiates some computing action or simply interacts with an active application, every application has confidentiality, integrity, and availability requirements that relate to the data, programs, and computing machinery. In these situations, users suffer from lack of sensitivity: They often do not appreciate the security risks associated with using computers.

For these reasons, every organization using computers to create and store valuable assets should perform thorough and effective security planning. A **security plan** is a document that describes how an organization will address its security needs. The plan is subject to periodic review and revision as the organization’s security needs change.

***

**Enterprise security starts with a security plan that describes how an organization will address its security needs.**

***

#### Organizations and Security Plans

Consider a simple example: You have several things you need to do in the next few days. You can keep them in your head or write them down on paper or an electronic device. In your head, it is easy to forget some or to focus on a less important activity. Writing matters down encourages you to think for a moment of other things you need to do. And a recorded list to which you can refer gives you a structure to remind you of the important items or help you choose something you can complete if you have a few free minutes.
