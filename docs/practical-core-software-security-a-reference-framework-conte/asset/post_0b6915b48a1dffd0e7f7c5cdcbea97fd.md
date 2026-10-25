
application compared to another. It could be because developers in the former were better trained or implemented the framework more effectively. Such feedback should be looped back into earlier stages of the SDL during the next release cycle.

## Remediation Report

A remediation report/dashboard should be prepared and updated regularly from this stage. The purpose of this report is to showcase the security posture and risk of the product at a technical level.

## 6.7 Metrics

The following metrics should be collected during this phase of the SDL (some of which may overlap metrics we discussed earlier).

- Percent compliance with company policies (updated)
  - Percent of compliance in Phase 3 versus Phase 4
- Number of lines of code tested effectively with static analysis tools
- Number of security defects found through static analysis tools
- Number of high-risk defects found through static analysis tools
- Defect density (security issues per 1000 lines of code)
- Number and types of security issues found through static analysis, dynamic analysis, manual code review, penetration testing, and fuzzing
  - Overlap of security issues found through different types of testing
  - Comparison of severity of findings from different types of testing
  - Mapping of findings to threats/risks identified earlier
- Number of security findings remediated
  - Severity of findings
  - Time spent (approximate) in hours to remediate findings
- Number, types, and severity of findings outstanding
- Percentage compliance with the security test plan
- Number of security test cases executed
  - Number of findings from security test case execution
  - Number of retests executed

## 6.8 Summary

During our discussion of the design and development (A4) phase, we described the process for successful test case execution, the process of proper code review through the use of both automated tools and manual review, and the process for privacy validation and remediation to be conducted during this phase of the SDL. The most critical processes and procedures described in this chapter are those that provide the ability to effectively and efficiently test, tune, and remediate known vulnerabilities and to ensure that secure coding policies have been followed, which provide the necessary security and privacy vulnerability protections before moving on to the product ship (A5) phase of the SDL.

## Chapter Quick-Check

1. The following are primary mitigation methods except:
   a. Locking down the environment
   b. Input validation
   c. Use of deprecated libraries for legacy code
   d. Output validation

2. Elements of defensive coding include all the following except:
   a. Custom cryptographic functions to avoid algorithm disclosure
   b. Exception handling to avoid program termination
   c. Interface coding efforts to avoid API-facing attacks
   d. Cryptographic agility to make cryptographic functions stronger

3. Static analysis can be used to check for:
   a. Approved function/library calls, examining rules and semantics associated with logic, and thread performance management
   b. Syntax, approved function/library calls, and race conditions
   c. Syntax, approved function/library calls, and memory management
   d. Syntax, approved function/library calls, and examining rules and semantics associated with logic and calls

4. Automated testing has the following advantages over manual code review except:
   a. Detection of unsafe or deprecated function calls
   b. Identification of obfuscated routines
   c. Speed of analysis
   d. Integration into the IDE

## Exercises

The following exercises are based on the case study discussed in Appendix A. These exercises are intended to give you some practice in applying the steps and producing deliverables for Phase A4 of the SDL.

At this point, you’ve created a management plan and a roadmap to implement an SDL at Revvin’ Engines. With a solid system and process that yields secure architecture and design for an API-based system of microservices that reflect the business requirements and the security and nonfunctional requirements for an application, you can gain assurance that the applications and infrastructure can stand up to the hostile public Internet.

As you move into the development activities, you’ll need a plan and roadmap for security at development time, unit testing time, integration testing time, and pre-release testing for assurance that the applications are secure enough for release to production.

1. Revisit the initial testing plan and include all activities you deem are needed for the application(s) testing—both manual and tool-based.

2. Design processes to integrate testing activities in development pipelines for automation of testing tasks that can be automated. Make certain that all testing results are reported to a gatekeeper function that will fail the build if the scan policies are unmet.

3. Establish the scanner policies needed for each scanning tool or process to determine pass/failure limits that trigger appropriate security events.

4. Determine the metrics needed across all mandated testing processes and determine the most appropriate reporting methods and mechanisms.

## References

1. Kaner, C. (2008, April). “A Tutorial in Exploratory Testing,” p. 36. Retrieved from http://www.kaner.com/pdfs/QAIEexploring.pdf

2. Chmielewski, M., Clift, N., Fonrobert, S., and Ostwald, T. (2007, November). “MSDN Magazine: Find and Fix Vulnerabilities Before Your Application Ships.” Retrieved from http://msdn.microsoft.com/en-us/magazine/cc163312.aspx

3. Microsoft Corporation. (2012). “How To: Perform a Security Code Review for Managed Code (.NET Framework 2.0).” Retrieved from http://msdn.microsoft.com/en-us/library/ff649315.aspx

4. Ibid.

5. Jackson, W. (2009, February). GCN—Technology, Tools and Tactics for Public Sector IT: “Static vs. Dynamic Code Analysis: Advantages and Disadvantages.” Retrieved from http://gcn.com/Articles/2009/02/09/Static-vs-dynamic-code-analysis.aspx?p=1

6. Cornell, D. (2008, January). OWASP San Antonio Presentation: “Static Analysis Techniques for Testing Application Security.” Retrieved from https://1library.net/document/y94orglq-static-analysis-techniques-testing-application-security-antonio-january.html

7. Jackson, W. (2009, February). GCN—Technology, Tools and Tactics for Public Sector IT: “Static vs. Dynamic Code Analysis: Advantages and Disadvantages.” Retrieved from http://gcn.com/Articles/2009/02/09/Static-vs-dynamic-code-analysis.aspx?p=1

8. Cornell, D. (2008, January). OWASP San Antonio Presentation: “Static Analysis Techniques for Testing Application Security.” Retrieved from https://1library.net/document/y94orglq-static-analysis-techniques-testing-application-security-antonio-january.html

9. Jackson, W. (2009, February). GCN—Technology, Tools and Tactics for Public Sector IT: “Static vs. Dynamic Code Analysis: Advantages and Disadvantages.” Retrieved from http://gcn.com/Articles/2009/02/09/Static-vs-dynamic-code-analysis.aspx?p=1

10. Cornell, D. (2008, January). OWASP San Antonio Presentation: “Static Analysis Techniques for Testing Application Security.” Retrieved from https://1library.net/document/y94orglq-static-analysis-techniques-testing-application-security-antonio-january.html

11. Jackson, W. (2009, February). GCN—Technology, Tools and Tactics for Public Sector IT: “Static vs. Dynamic Code Analysis: Advantages and Disadvantages.” Retrieved from http://gcn.com/Articles/2009/02/09/Static-vs-dynamic-code-analysis.aspx?p=1

12. Cornell, D. (2008, January). OWASP San Antonio Presentation: “Static Analysis Techniques for Testing Application Security.” Retrieved from https://1library.net/document/y94orglq-static-analysis-techniques-testing-application-security-antonio-january.html

13. The Open Web Application Security Project (OWASP). (2012). “Fuzzing.” Retrieved from https://www.owasp.org/index.php/Fuzzing

14. R2Launch. (2012). “Fuzz.” Retrieved from http://www.r2launch.nl/index.php/software-testing/fuzz

15. The Open Web Application Security Project (OWASP). (2012). “Testing Guide Introduction.” Retrieved from https://www.owasp.org/index.php/Testing_Guide_Introduction#Manual_Inspections_._26_Reviews
