
# Extreme Programming (XP)

Extreme Programming (XP) is an Agile development method that uses pairs of programmers who work off a detailed specification. There is a high level of customer involvement. “Extreme Programming improves a software project in five essential ways; communication, simplicity, feedback, respect, and courage. Extreme Programmers constantly communicate with their customers and fellow programmers. They keep their design simple and clean. They get feedback by testing their software starting on day one. They deliver the system to the customers as early as possible and implement changes as suggested” [\[13\]](#Ch009_459-508_B9780443187346000088.xhtml#bb0070). XP core practices include:

*   **Planning**: specifies the desired features, which are called the User Story. They are used to determine the iteration (timeline) and drive the detailed specifications.
*   **Paired programming**: programmers work in teams.
*   **Forty-hour workweek**: the forecasted iterations should be accurate enough to forecast how many hours will be required to complete the project. If programmers must put in additional overtime, the iteration must be flawed.
*   **Total customer involvement**: the customer is always available, and carefully monitors the project.
*   **Detailed test procedures**: they are called Unit Tests [\[13\]](#Ch009_459-508_B9780443187346000088.xhtml#bb0070).

> **Note**
>
> The XP development model is not to be confused with Microsoft Windows XP: Extreme Programming’s use of the acronym “XP” predates Microsoft’s use.

## Spiral

The Spiral Model is a software development model designed to control risk. Barry W. Boehm created the model, described in his 1986 paper “A Spiral Model of Software Development and Enhancement” (see [http://portal.acm.org/citation.cfm?id=12948](http://portal.acm.org/citation.cfm?id=12948)). Boehm states, “The major distinguishing feature of the spiral model is that it creates a risk-driven approach to the software process rather than a primarily document-driven or code-driven process. It incorporates many of the strengths of other models and resolves many of their difficulties” [\[8\]](#Ch009_459-508_B9780443187346000088.xhtml#bb0045).

The spiral model repeats steps of a project, starting with modest goals, and expanding outwards in ever-wider spirals (called rounds). Each round of the spiral constitutes a project, and each round may follow traditional software development methodology such as Modified Waterfall. A risk analysis is performed in each round. Fundamental flaws in the project or process are more likely to be discovered in the earlier phases, resulting in simpler fixes. This lowers the overall risk of the project: large risks should be identified and mitigated.

Boehm used the Spiral Model to develop the TRW Software Productivity System (TRW-SPS), a complex software project that resulted in 1,300,000 computer instructions. “Round zero” was a feasibility study, a small project designed to determine if the TRW-SPS project represented significant value to the organization, and was thus worth the risk of undertaking. The feasibility study indicated that the project was worthwhile (low risk), and the project spiraled outward. The deliverables of further rounds included:

1.  Concept of Operations (COOP)
2.  Software Requirements
3.  Software Product Design
4.  Detailed Design [\[8\]](#Ch009_459-508_B9780443187346000088.xhtml#bb0045)

Each round included multiple repeated steps, including prototype development and, most importantly, a risk analysis. Boehm’s spiral is shown in [Fig. 9.5](#Ch009_459-508_B9780443187346000088.xhtml#f0030).

![Fig. 9.5 The Spiral Model. Source: https://upload.wikimedia.org/wikipedia/commons/e/ec/Spiral_model_%28Boehm%2C_1988%29.svg. Image under permission of Creative Commons.](images/B9780443187346000088/f09-05-9780443187346.jpg)

[Fig. 9.5](#Ch009_459-508_B9780443187346000088.xhtml#B-f0030) The Spiral Model. Source: [https://upload.wikimedia.org/wikipedia/commons/e/ec/Spiral_model_%28Boehm%2C_1988%29.svg](https://upload.wikimedia.org/wikipedia/commons/e/ec/Spiral_model_%28Boehm%2C_1988%29.svg). Image under permission of Creative Commons.

The spiral ended with successful implementation of the project. Any potential high risk, such as lack of value to the organization or implementation failure, was identified and mitigated earlier in the spiral, when it was cheaper and easier to mitigate.

## Rapid Application Development (RAD)

**Rapid Application Development** (RAD) rapidly develops software via the use of prototypes, “dummy” GUIs, back-end databases, and more. The goal of RAD is quickly meeting the business need of the system; technical concerns are secondary. The customer is heavily involved in the process.

According to the Centers for Medicare & Medicaid Services (see [http://www.cms.gov/Research-Statistics-Data-and-Systems/CMS-Information-Technology/XLC/Downloads/SelectingDevelopmentApproach.pdf](http://www.cms.gov/Research-Statistics-Data-and-Systems/CMS-Information-Technology/XLC/Downloads/SelectingDevelopmentApproach.pdf)), RAD “Aims to produce high quality systems quickly, primarily through the use of iterative prototyping (at any stage of development), active user involvement, and computerized development tools. These tools may include Graphical User Interface (GUI) builders, Computer Aided Software Engineering (CASE) tools, Database Management Systems (DBMS), fourth-generation programming languages, code generators, and object-oriented techniques” [\[14\]](#Ch009_459-508_B9780443187346000088.xhtml#bb0075).

## Prototyping

Prototyping is an iterative approach that breaks projects into smaller tasks, creating multiple mockups (prototypes) of system design features. This lowers risk by allowing the customer to see realistic-looking results long before the final product is completed. As with other modern development methods, there is a high level of customer involvement: the customer inspects the prototypes to ensure that the project is on track and meeting its objective.

The term “prototype” may be a bit misleading: later stage prototypes may be used as the actual final product. Prototypes can be thought of as “working models.” Prototyping is not a full-fledged software development methodology: it is used by other iterative methods such as Spiral or RAD.

## DevOps

Traditional software development was performed with strict separation of duties between the developers, quality assurance teams, and production teams. Developers had hardware that mirrored production models, and test data. They would hand code off to the quality assurance teams, who also had hardware that mirrored production models, as well as test data. The quality assurance teams would then hand tested code over to production, who had production hardware and real data.

In the old (less agile) model: developers had no direct contact with production, and in fact were strictly walled off from production via separation of duties.

DevOps is a more agile development and support model, echoing the agile programming methods we learned about previously in this chapter, including Sashimi and Scrum. DevOps is “the practice of operations and development engineers participating together in the entire service lifecycle, from design through the development process to production support” [\[15\]](#Ch009_459-508_B9780443187346000088.xhtml#bb0080).

## DevSecOps

DevSecOps is an agile method that integrates information security into the development process. Security is involved in every step. The DevSecOps Manifesto outlines the goals:

*   **Leaning in** over Always Saying “No”
*   **Data & Security Science** over Fear, Uncertainty and Doubt
*   **Open Contribution & Collaboration** over Security-Only Requirements
*   **Consumable Security Services with APIs** over Mandated Security Controls & Paperwork
*   **Business Driven Security Scores** over Rubber Stamp Security
