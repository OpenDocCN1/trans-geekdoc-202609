
In order to provide a thorough and rigorous examination of a software product, development testing is typically organized into levels. As an example, a software product’s testing can be organized into unit, integration, and system levels of testing.

Unit (module or component) level testing focuses on the early examination of sub-program functionality and ensures that functionality not visible at the system level is examined by testing. Unit testing ensures that quality software units are furnished for integration into the finished software product.

Integration level testing focuses on the transfer of data and control across a program’s internal and external interfaces. External interfaces are those with other software (including operating system software), system hardware, and the users and can be described as communications links.

System level testing demonstrates that all specified functionality exists and that the software product is trustworthy. This testing verifies the as-built program’s functionality and performance with respect to the requirements for the software product as exhibited on the specified operating platform(s). System level software testing addresses functional concerns and the following elements of a device’s software that are related to the intended use(s):

- Security and privacy performance (e.g., function of encryption, security log reporting);
- Performance issues (e.g., response times, reliability measurements);
- Responses to stress conditions (e.g., behavior under maximum load, continuous use);
- Operation of internal and external security features;
- Effectiveness of recovery procedures, including disaster recovery;
- Usability;
- Compatibility with other software products;
- Behavior in each of the defined hardware configurations; and
- Accuracy of documentation.

Control measures (e.g., a traceability analysis) should be used to ensure that the intended coverage is achieved.

System level testing also exhibits the software product’s behavior in the intended operating environment. The location of such testing is dependent upon the software developer’s ability to produce the target operating environment(s). Test plans should identify the controls needed to ensure that the intended coverage is achieved and that proper documentation is prepared when planned system level testing is conducted at sites not directly controlled by the software developer.

Test procedures, test data, and test results should be documented in a manner permitting objective pass/fail decisions to be reached. They should also be suitable for review and objective decision making subsequent to running the test, and they should be suitable for use in any subsequent regression testing. Errors detected during testing should be logged, classified, reviewed, and resolved prior to release of the software. Software error data that is collected and analyzed during a development lifecycle may be used to determine the suitability of the software product for release for commercial distribution. Test reports should comply with the requirements of the corresponding test plans.

Enterprise software products are often complex. Software testing tools are frequently used to ensure consistency, thoroughness, and efficiency in the testing of such software products and to fulfill the requirements of the planned testing activities. These tools may include supporting software built in-house to facilitate unit (module) testing and subsequent integration testing (e.g., drivers and stubs) as well as commercial software testing tools. Such tools should have a degree of quality no less than the software product they are used to develop. Appropriate documentation providing evidence of the validation of these software tools for their intended use should be maintained.

As applied to software, the term maintenance does not mean the same as when applied to hardware. The operational maintenance of hardware and software are different because their failure/error mechanisms are different. Hardware maintenance typically includes preventive hardware maintenance actions, component replacement, and corrective changes. Software maintenance includes corrective, perfective, and adaptive maintenance but does not include preventive maintenance actions or software component replacement.

Changes made to correct errors and faults in the software are corrective maintenance. Changes made to the software to improve the performance, maintainability, or other attributes of the software system are perfective maintenance. Software changes to make the software system usable in a changed environment are adaptive maintenance.

When changes are made to a software system, either during initial development or during post release maintenance, sufficient regression analysis and testing should be conducted to demonstrate that portions of the software not involved in the change were not adversely impacted. This is in addition to testing that evaluates the correctness of the implemented change(s).

The specific validation effort necessary for each software change is determined by the type of change, the development products affected, and the impact of those products on the operation of the software. Careful and complete documentation of the design structure and interrelationships of various modules, interfaces, etc., can limit the validation effort needed when a change is made. The level of effort needed to fully validate a change is also dependent upon the degree to which validation of the original software was documented and archived. For example, test documentation, test cases, and results of previous verification and validation testing need to be archived if they are to be available for performing subsequent regression testing. Failure to archive this information for later use can significantly increase the level of effort and expense of revalidating the software after a change is made.

In addition to software verification and validation tasks that are part of the standard software development process, the following additional maintenance tasks should be addressed:

- **Software Validation Plan Revision —** For software that was previously validated, the existing software validation plan should be revised to support the validation of the revised software. If no previous software validation plan exists, it should be established to support the validation of the revised software.
- **Anomaly Evaluation —** Software organizations frequently maintain documentation, such as software problem reports that describe software anomalies discovered and the specific corrective action taken to fix each anomaly. Too often, however, mistakes are repeated because software developers do not take the next step to determine the root causes of problems and make the process and procedural changes needed to avoid recurrence of the problem. Software anomalies should be evaluated in terms of their severity and their effects on system operation and safety, but they should also be treated as symptoms of process deficiencies in the quality system. A root cause analysis of anomalies can identify specific quality system deficiencies. Where trends are identified (e.g., recurrence of similar software anomalies), appropriate corrective and preventive actions must be implemented and documented to avoid further recurrence of similar quality problems.
- **Problem Identification and Resolution Tracking —** All problems discovered during maintenance of the software should be documented. The resolution of each problem should be tracked to ensure it is fixed, for historical reference, and for trending.
- **Proposed Change Assessment –** All proposed modifications, enhancements, or additions should be assessed to determine the effect each change would have on the system. This information should determine the extent to which verification and validation tasks need to be iterated.
- **Task Iteration –** For approved software changes, all necessary verification and validation tasks should be performed to ensure that planned changes are implemented correctly, all documentation is complete and up to date, and no unacceptable changes have occurred in software performance.
- **Documentation Updating –** Documentation should be carefully reviewed to determine which documents have been impacted by a change. All approved documents (e.g., specifications, test procedures, user manuals, etc.) that have been affected should be updated in accordance with configuration management procedures. Specifications should be updated before any maintenance and software changes are made.

## Negative Testing/Misuse Case Testing

There are two main testing strategies in software testing: positive testing and negative testing.

Positive testing determines that your application works as expected. If an error is encountered during positive testing, the test fails.

Negative testing ensures that your application can gracefully handle invalid input or unexpected user behavior. For example, if a user tries to type a letter in a numeric field, the correct behavior in this case would be to display the "Incorrect data type, please enter a number" message. The purpose of negative testing is to detect such situations and prevent applications from crashing. In addition, negative testing helps to improve the quality of the application and find its weak points. A core difference exists between positive testing and negative testing: Throwing an exception is expected in negative testing. When you perform negative testing, exceptions are expected – they indicate that the application handles improper user behavior correctly. It is generally considered a good practice to combine both the positive and the negative testing approaches. This strategy provides higher tested application coverage as compared to using only one of the specified testing methodologies.

### Typical Negative Testing Scenarios

Negative testing is aimed at detecting possible application crashes in different situations. Below are several possible examples of such situations:
