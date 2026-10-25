+   - You have determined whether the security test case execution results are conclusive. If the results do not meet the acceptance criteria, then the test is likely inconclusive because the test results are not reproducible and you are unable to determine what is causing the security issue in the software. If results are inconclusive, an exploratory test will be needed.

+   - You have determined whether tuning is required at this point. At this stage, either a security issue has been detected or more tests are needed to validate compliance with additional acceptance criteria. Either the last test will be executed again to see whether the results are reproducible, or you will move on to tuning,

+   - There are some tests where no security issues are found and no tuning is required, but the software must be tested because there it is mandatory to validate the security of the software and its associated system(s) against specifically known software security issues and vulnerabilities.

Successful security test case execution completion criteria include the following:

+   - The specific target security requirements and goals of the software that has been tested have been met.

+   - When a situation outside the control of the software security group or its equivalent cannot be resolved, the security testing may be deemed complete as a result of any one of the following situations, if the company stakeholders responsible for the development of the software accept the risk:

+   - The situation preventing the software security group or its equivalent from achieving its security test case criteria is outside the group's control or contractual obligations.

+   - The predetermined engagement end date is reached and company stakeholders responsible for the development of the software accept the risk of not meeting the security criteria. In many cases, this is accepted if a commitment to fix the vulnerability is scheduled for the next update of the product and/or patch release.

+   - The software security group or its equivalent and all other stakeholders agree that the application performs acceptably, even though some security requirements or goals have not been achieved. As with the previous situation, this is typically not accepted unless the commitment to fix the vulnerability is scheduled for the next update of the product and/or patch release.

# ## 6.3 Code Review in the SDLC/SDL Process

Code review can be especially productive for identifying security vulnerabilities during software development. A properly conducted code review can do more for the security of your code than nearly any other activity. A code review allows you to find and fix a large number of security issues before the code is tested or shipped. There are four basic techniques for analyzing the security of a software application: automated scanning, manual penetration testing, static analysis, and manual code review. All of these methodologies, of course, have strengths, weaknesses, sweet spots, and blind spots. Collectively, these four types of security code reviews are likely the fastest and most accurate way to find and diagnose many security problems while