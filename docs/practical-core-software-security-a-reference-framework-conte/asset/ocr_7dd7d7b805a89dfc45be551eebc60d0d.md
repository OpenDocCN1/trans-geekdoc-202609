to review, so you can differentiate between vulnerability types that have elevated priority and others that may be out of scope based on your security objectives.

Security code review is most successful if it is planned and executed in the context of other security-related efforts such as threat modeling, as described in the previous chapter. Threat modeling helps to identify a critical area of code that then becomes a subject of detailed review, and its results can likewise be used to validate or question security assumptions specified in a threat model and help to understand the application’s functionality, technical design, and existing security threats and countermeasures. A security code review should begin with a review of the threat models and design specifications, then move on to source code.

The ideal flow of activities for code review success is perhaps best described by the steps identified by Chmielewski et al. in MSDN Magazine:

+   (a) Threat Modeling: Understand code and data flows; identify high-risk areas and entry points.
+   (b) Code Reviews: Document all findings in an appropriate way, as well as the process itself.
+   (c) Resolve Problems: Cooperate with owners of code on applying fixes and further efforts.
+   (d) Learn the Lesson: Update tools, educate development teams, improve processes, and plan future iterations.²

For an effective security code review, set goals and constraints for the following.

+   * Time: Set a time limit. This helps you to avoid spending too much time on a single issue. Performing multiple, smaller reviews is more effective than doing one long review.
+   * Types of issues: Determine what types of issues you are looking for. For example, consider:
+       * General issues that affect confidentiality, integrity, and availability
+       * Issues related to your application’s security quality-of-service requirements
+       * Issues related to your application’s compliance requirements
+       * Issues related to the technologies your application uses
+       * Issues related to the functionality your application exposes
+       * Issues you found during threat modeling
+   * Out-of-scope items: Identify what you will not be looking for. Explain why these things are out of scope.³

# 2. Perform Preliminary Scan

Static analysis is used to find an initial set of security issues and to improve your understanding of where you will be most likely to find security issues when you review the code more fully as well as to discover hot spots where additional security issues are likely to be found in later steps. This is typically done with automatic scans, manual scans, or a combination of both, depending on the review objectives and time limitations of the code review plan. Automated scans have an advantage in their ability to quickly identify “low-hanging fruit” across large sets of applications. The results from these scans are used in creating a prioritized list of potential security vulnerabilities and security mechanisms to review and investigate.

An automatic scan can be used to supplement a manual review, as an extra check to go through large volumes of code that would be cost- and/or time-prohibitive to do manually,