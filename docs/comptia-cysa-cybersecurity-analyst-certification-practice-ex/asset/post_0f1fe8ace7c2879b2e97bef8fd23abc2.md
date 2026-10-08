
A, B, and D are incorrect. SANS Institute is an authority on security—be it web, application, system, or network—but does not specialize in web security. CMMI is the Capability Maturity Model Integration, the well-known, five-level maturity model from the Software Engineering Institute, a federally funded research and development center at Carnegie-Mellon University. The Center for Internet Security (CIS) is a nonprofit organization that excels in enhancing security with its collaborative approach.

- To reduce the number of modifications soon after an application’s release, what practice is to verify the application will be used as developers expected?
- A. Stress testing
- B. Static code analysis
- C. User acceptance testing
- D. Manual peer review
- C is correct. Before an application gets released, it’s common to have it tested by a handful of users. These early users will report on what should be changed before the application goes to a wider audience. This is called user acceptance testing.

- A, B, and D are incorrect. Stress testing involves pushing the application to its limits to see what breaks or fails first. Static code analysis is an automated form of reviewing code without having to run the program. This is typically performed by a specialized application. Manual peer review is a slower but methodical code review done by the developers’ peers. This code review allows others to catch the simple errors or typos that developers might too easily skip over from being familiar with the code

Use the following scenario to answer Questions 5–7:
Tywin is the CEO of a factory where employees are paid hourly. Employees must submit on all their expected hours for the week by Tuesday to get paid on Friday. The factory manager, shares with Tywin that every he hears the complaints from employees: “How do I know by Tuesday that my schedule won’t change by Friday?” Understanding the need for a quicker way to submit hours, Tywin remembers that his neighbor’s son, Sam, has been taking development courses at a university for a few semesters. Therefore, Tywin offers Sam an opportunity to help.

After a few weeks of development, Sam launches a web application. Employees are told to authenticate and enter their hours using this application. The application then submits the hours to the Finance department and tells employees how much they can expect to get paid on Friday. Hours can be submitted as late as Thursday night. Jon reports to Tywin employees are happy with the web application and it seems to be the subject of a constant buzz around the break room.

- 5. A very honest user tells Jon that if a user enters a single quote, followed by “OR 1=1” in the password field, they can make the application reply with the hours of any employee. What part of software development did Sam likely overlook?
- A. Parameter validation
- B. Input validation
- C. Stress testing
- D. Session tokens not randomized
- B is correct. Input validation is the coding practice of verifying that a user’s input falls within the expected range in size, character types, and format.

- A, C, and D are incorrect. Parameter validation is the coding practice of verifying the information passed is what the application expects. It’s similar to input validation, but parameter validation might also check in from another portion of the application or another application entirely. Stress testing involves pushing the application to its limits to see what breaks or fails first. Lastly, session tokens not being randomized is incorrect as session tokens are not relevant to the attack.

- 6. Another honest user, Arya, reports that if she changes the user ID in the URL to someone else’s ID, she can get the paycheck for that person’s week. The same user claims by changing other parameters in the URL, she can make the server reveal much information about itself and the application. If you could hire her Arya to perform security analysis work, what type of work would her experience seem to match?
- A. Regression testing
- B. Interception proxy
- C. User acceptance testing
- D. Vulnerability scanning
- D is correct. Arya seems determined to find vulnerabilities in this web application. She successfully attempted URL manipulation as well as found information leaks. In this case, URL manipulation was able to make the application return another person’s paycheck amount. Web application vulnerability scanning would encompass these and many other checks, including cross-site scripting (XSS), improper use of HTTPS, improper authentication, and more.

- A, B, and C are incorrect. Regression testing is applicable, but because this is the first release of the app, we would not call this regression testing. Interception proxy is a software tool, not a person’s role, used to discover similar vulnerabilities by being inserted between two devices. The interception proxy will act as a go-between monitoring device. An analyst can examine the traffic for any vulnerabilities. Up to now, Arya has been a user determined to discover issues. If Arya transitions to the security team, she would no longer be ‘just a user’ but as a team member to validate issues discovered by user testing. Normally, before an application is released, it is tested by a handful of users. These early users will report on what should be changed before the application goes to a wider audience.

- 7. Considering the issues discovered to date, what phase of software development was likely missing during the application lifecycle?
- A. Security requirements definition
- B. Stress testing
- C. Security regression testing
- D. Operations and Maintenance
- E. User acceptance testing
- A is correct. It seems the developer did very little security testing prior to the application’s release. If security requirements had been submitted and followed closely over the course of development, many of these issues have been avoided. Truly, these are dark times.

- B, C, D, and E are incorrect. Stress testing involves trying to break an application by making it work harder than intended. Regression testing is testing the application after a modification to ensure any vulnerabilities were not introduced. Operations and Maintenance is the continued care of the application after its release, so this option doesn’t actually apply to the question. User acceptance testing describes how an application gets tested by a handful of users, prior to release. Early users can report what should be changed before the application goes to a wider audience.

- 8. What detailed guides published by the CIS are equivalent to the Security Technical Implementation Guides published by the Defense Information System Agency and other government entities?
- A. Regression reports
- B. Benchmarks
- C. Security requirements definitions
- D. Secure coding best practice guides
- B is correct. The Center for Internet Security Benchmarks are detailed configuration guides that are comparable to the STIGs published by the DISA and other government agencies. These guides are free to download, are available for desktop, mobile, server, and network devices, and cover both hardware and virtual platforms. They are highly recommended for anyone to review and understand.

- A, C, and D are incorrect. A regression report would detail what, if, security vulnerabilities had appeared due to a modification to software. A security requirements definition is a key document that details the security expectations for software. Ideally, this should be drafted in parallel to the software’s early requirements and definitions documents. Secure coding best practice guides are not a particular publication of CIS.

- 9. The Center for Internet Security has organized focus groups and built consensus to formulate a group of 20 “CIS Controls.” These controls are separated in groups of Basic, Foundational, and Organizational. What is the intended aim of these controls?
- A. Employee-controlled access
- B. Software development best practices
- C. Wireless access control
- D. System design recommendations
- D is correct. The CIS Controls are system design recommendations, grouped into three categories: Basic, Foundational, and Organizational. These consensus-based best practices provide a set of actionable recommendations, intended for anyone responsible for information security.

- A, B, and C are incorrect. Although employee-controlled access, software development, and wireless access controls are all very important, they each represent just one area to be covered by the CIS Controls.
