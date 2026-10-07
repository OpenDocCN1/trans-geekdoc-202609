
Option C is incorrect. Visiting each vendor’s site for an in-person assessment would be time-consuming, costly, and logistically challenging, especially when dealing with a large number of vendors.

Option D is incorrect. Annual financial reports provide financial data and do not offer in-depth details on a vendor’s security posture or practices.

Question 241. A developer has implemented a new feature on a company’s website that allows users to search for products by their names. Within a few days, the IT team noticed abnormal activities where entire tables from the database were being dumped. Which vulnerability might the new feature have introduced?

- (A) Cross-Site Scripting (XSS)
- (B) Distributed Denial-of-Service (DDoS)
- (C) Structured Query Language injection (SQLLi)
- (D) Cross-Site Request Forgery (CSRF)

Explanation 241. Correct Answer: C. Structured Query Language injection (SQLi). SQL attacks occur when an attacker can insert or “inject” SQL code into a query. If user input is not properly sanitized before being used in SQL statements, attackers can exploit this to manipulate the queries, which can lead to unauthorized viewing of data, corrupting or deleting data, and other malicious activities.

Structured Query Language injection, or SQLi, is a code injection technique that attackers use to run malicious SQL statements on a database. Given that entire tables from the database were dumped after implementing a search feature, it’s a clear indication that the feature did not properly sanitize user input, allowing for SQLi.

**Option A is incorrect.** Cross-Site Scripting (XSS) attacks inject malicious scripts into web pages viewed by users. It doesn’t leading to dumping of database tables as described in the scenario.

**Option B is incorrect.** Distributed Denial-of-Service (DDoS) attacks overwhelm a target with traffic, causing service interruptions. It’s not related to the extraction of database information.

**Option D is incorrect.** Cross-Site Request Forgery (CSRF) tricks victims into submitting malicious requests. It doesn’t result in the dumping of database tables.

Question 242. DeltaSoft has released a new web application. The security team is tasked with observing the application’s behavior and responses when it is running to identify potential vulnerabilities. Which method is most appropriate for this purpose?

- (A) Static Analysis
- (B) Fuzz Testing
- (C) Whitebox Testing
- (D) Dynamic Analysis

Explanation 242. Correct Answer: D. Dynamic Analysis. Dynamic analysis focuses on examining an application during its execution, or runtime. By observing the application’s behavior and responses, security teams can identify vulnerabilities that might not be evident in the static code.

**Option A is incorrect.** Static analysis evaluates an application’s code without executing the application. It does not focus on observing the application’s behavior during runtime.

**Option B is incorrect.** Fuzz testing involves submitting random inputs to an application to observe its behavior and detect vulnerabilities, but it’s just one subset of dynamic analysis.

**Option C is incorrect.** Whitebox testing involves understanding the internal structures and workings of an application while testing, which can be part of static or dynamic testing, but on its own, it does not specifically focus on runtime behavior observation.

Question 243. GlobalTech, a multinational corporation, is negotiating a cloud storage contract with CloudCorp. GlobalTech wants to ensure that data retrieval remain under 2 seconds 99.9% of the time. Which component should be explicitly defined in their agreement to set this expectation?

- (A) Pricing model
- (B) Data sovereignty clauses
- (C) Service-level agreement (SLA)
- (D) Termination clauses

Explanation 243. Correct Answer: C. Service-level agreement (SLA). Service-level agreements (SLAs) are designed to define specific metrics, responsibilities, and expectations to ensure that both parties understand and agree to the performance benchmarks and consequences if those benchmarks are not achieved. In this scenario, the SLA would specify the expected data retrieval times.

**Option A is incorrect.** While pricing is an essential aspect of any contract, it does not specify performance expectations like data retrieval times.

**Option B is incorrect.** Data sovereignty clauses pertain to the legal aspects of where data is stored and processed, not to performance metrics.

**Option D is incorrect.** Termination clauses deal with the conditions under which the agreement might be terminated, not with performance expectations.

Question 244. SoftTech Inc., a software company, is considering expanding its operations to Europe. They will be collecting and processing personal data of EU citizens. Which of the following legal implications are MOST for SoftTech Inc. to consider?

- (A) The need to register with each country's software association
- (B) Compliance with the Data Protection Regulation (GDPR)
- (C) Ensuring software rights in each country
- (D) The European standard for coding

Explanation 244. Correct Answer: B. Compliance with the Data Protection Regulation (GDPR). When dealing with personal data of EU citizens, companies must comply with the GDPR, which outlines strict requirements on data protection and privacy. Non-compliance can lead to hefty fines and legal repercussions.

**Option A is incorrect.** Registering with each country’s software association is not related to the privacy of personal data.

**Option C is incorrect.** While software rights are essential, they don’t directly address the privacy of personal data.

**Option D is incorrect.** There is no “European standard for coding” that relates to the privacy.

Question 245. A multinational organization recently experienced a significant security breach. After investigating, it was determined that a change to the network infrastructure was made without undergoing the standard approval process. As a result, there was a misconfiguration which allowed unauthorized access. What security principle related to change management did the organization neglect?

- (A) Configuration baseline reviews
- (B) Least privilege enforcement
- (C) Approval process adherence
- (D) Patch management

Explanation 245. Correct Answer: C. Approval process adherence. The approval process is a critical aspect of change management. Before any changes are made, especially to critical systems like network infrastructure, they need to undergo a rigorous approval process. This ensures multiple experts evaluate the change for potential vulnerabilities or issues. In this scenario, skipping the approval process led to a significant security breach.

**Option A is incorrect.** Configuration baseline reviews involve regularly checking and ensuring that systems are configured as per the organization's approved baseline. While it's important, the issue in the scenario was directly related to bypassing the approval process.

**Option B is incorrect.** Least privilege enforcement means providing only the minimal necessary access to users to perform their tasks. This scenario doesn't deal with access rights or privileges.

**Option D is incorrect.** Patch management concerns the process of applying updates to software and systems. The breach in the question wasn't related to missing patches but was due to bypassing the approval process.

Question 246. Carlos, an IT consultant, advises a startup on cybersecurity best practices. The company plans to launch several microsites under various subdomains. They want a solution that is cost-effective but also ensures that the sites are validated by a third-party. What type of certificate should Carlos recommend?
