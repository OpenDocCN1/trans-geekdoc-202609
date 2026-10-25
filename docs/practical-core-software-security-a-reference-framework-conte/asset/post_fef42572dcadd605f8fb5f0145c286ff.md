
## Phase 3: Dig deep into risky code.

- Analysts should also use manual analysis (e.g., code inspection) to more thoroughly evaluate any risky code that has been identified based on the attack surface, or based on the heuristics as discussed previously.
- Such code review should start at the entry point for each module under review and should trace data flow through the system, evaluating the data, how it is used, and whether security objectives might be compromised.

Below is an example of an issue that can be found through static analysis. Injection vulnerabilities are at the top of the OWASP® Top 10 2021 list.19 These vulnerabilities occur when untrusted data is used directly for a query or as a result of construct commands without validation. There are different types of injection vulnerabilities—SQL, OS, and LDAP among them. SQL injection attacks are possible if user input is used directly to craft an SQL query.

Let's say that a user wants to review his account details. The application needs his user id or identifier to query account information from a back-end database. The application can pass this on through a URL parameter by doing something like this:

```
http://example.com/application/reviewaccount?account_id='1007'
```

In this case, the application is getting user account_id '1007' and will use this id to pull information from the database. Let's say the backend query looks like this:

```
String insecureQuery = "SELECT * FROM accounts WHERE accountID= '" + request.getParameter("account_id") + " ' ";
```

If a malicious user changes the parameter value to \ or '1'='1, the following string insecure query will have the value

```
SELECT * FROM accounts WHERE accountID= '' \\ or '1'='1';
```

'1'='1' will always be true, and thus this query can yield information about all accounts. This was not the intention of the developer, but by trusting user input to create a query, he or she has allowed a malicious user to execute arbitrary database commands.

Static analysis tools executed against code will identify that the query is built with user input and can result in SQL injection attacks.

### 6.4.2 Dynamic Analysis

Dynamic program analysis is the analysis of computer software that is performed by executing programs on a real or virtual processor in real time. The objective is to find security errors in a program while it is running, rather than by repeatedly examining the code offline. By debugging a program under all the scenarios for which it is designed, dynamic analysis eliminates the need to artificially create situations likely to produce errors. It has the distinct advantages of having the ability to identify vulnerabilities that might have been false negatives and to validate findings in the static code analysis.

Input (Running application, infrastructure, or operational deployment [Source Code not required])

Testing (Dynamic Analysis)

Output (Potential Defects Identified)

- Does not always have access to the actual instructions the software will be executing.
- Cannot provide exact location of code where problem resides.
- Executed in operations environment.

- Defects identified include buffer overflows, SQL injection, XSS, memory leaks, weak ciphers, etc.
- Does not find vulnerabilities introduced in the runtime environment or operations deployment.
- Does not always find authentication issues, business logic flaws, or insecure use of cryptography.

Figure 6.4 Dynamic analysis flow diagram.

Dynamic analysis (see Figure 6.4) is also known as dynamic application security testing (DAST). It identifies vulnerabilities within a production application. DAST tools are used to quickly assess a system’s overall security and are used within both the SDL and SDLC. The same advantages and cautions about using static analysis tools apply to dynamic analysis tools.

The following explanation of how dynamic analysis is used throughout the SDLC is taken from the Peng and Wallace (1993) NIST Special Publication 500-209, “Software Error Analysis.”20

- Commonly used dynamic analysis techniques for the design phase include sizing and timing analysis, prototyping, and simulation. Sizing and timing analysis is useful in analyzing real-time programs with response time requirements and constrained memory and execution space requirements. This type of analysis is especially useful for determining that allocations for hardware and software are made appropriately for the design architecture; it would be quite costly to learn in system testing that the performance problems are caused by the basic system design. An automated simulation may be appropriate for larger designs. Prototyping can be used as an aid in examining the design architecture in general or a specific set of functions. For large, complicated systems, prototyping can prevent inappropriate designs from resulting in costly, wasted implementations.21

- Dynamic analysis techniques help to determine the functional and computational correctness of the code. Regression analysis is used to re-evaluate requirements and design issues whenever any significant code change is made. This analysis ensures awareness of the original system requirements. Sizing and timing analysis is performed during incremental code development, and analysis results are compared against predicted values.22

- Dynamic analysis in the test phase involves different types of testing and test strategies. Traditionally, there are four types of testing: unit, integration, system, and acceptance. Unit testing may be either structural or functional testing performed on software units, modules, or subroutines. Structural testing examines the logic of the units and may be used to support requirements for test coverage—that is, how much of the program has been executed. Functional testing evaluates how software requirements have been implemented. For functional testing, testers usually need no information about the design of the program because test cases are based on the software requirements.23

- The most commonly used dynamic analysis techniques for the final phase of the SDLC are regression analysis and test, simulation, and test certification. When any changes to the product are made during this phase, regression analysis is performed to verify that the basic requirements and design assumptions affecting other areas of the program have not been violated. Simulation is used to test operator procedures and to isolate installation problems. Test certification, particularly in critical software systems, is used to verify that the required tests have been executed and that the delivered software product is identical to the product subjected to software verification and validation.24

Static analysis finds issues by analyzing source code. Dynamic analysis tools do not need source code but can still identify the problem. During our discussion of static analysis, we reviewed an SQL injection attack example. For that example, the tool would identify that account_id is passed as a URL parameter and would try to tamper the value of the parameter and evaluate the response from the application.

### 6.4.3 Fuzz Testing

Fuzz testing (see Figure 6.5), or fuzzing, is a black-box software testing technique that can be automated or semiautomated and provides invalid, unexpected, or random data to the inputs of a computer software program. In other words, it finds implementation bugs or security flaws by using malformed/semi-malformed data injection in an automated fashion. Inputs to the software program are then monitored for exception returns such as crashes, failing built-in code assertions, and potential memory leaks. Fuzzing has become a key element in testing for software or computer system security problems. Fuzz testing has a distinct advantage over other tools in that the test design is extremely simple and free of preconceptions about system behavior.

Fuzzing is a key element of software security and must be embedded in the SDL. There are many vendors to choose from in this space, and some even develop their own tools. Fuzzing is used for both security and QA testing. Fuzzing has recently been recognized as both a key element and a major deficiency in many software development programs, so much so that it is now a U.S. Department of Defense (DoD) Information Assurance Certification and Accreditation Process (DIACAP) requirement.

Fuzzing is a form of attack simulation in which unexpected data is fed to the system through an open interface, and the behavior of the system is then monitored. If the system fails, for example, by crashing or by failing built-in code assertions, then there is a flaw in the
