
- Where appropriate, verify the digital signatures of routines that process sensitive data when the code is being loaded for execution.
- If you include checksums on executables for production code, include routines that verify the checksums at every system restart.

The Carnegie-Mellon Software Engineering Institute Computer Emergency Response Team (CERT) provides a good “Top 10 Secure Coding Practices”² list. The list below provides some additional items to consider in addition to the items previously listed:

- Validate input from data sources. Proper input validation can eliminate many software vulnerabilities.
- Compile code using the highest warning level available for the compiler and eliminate warnings by modifying the code.
- Create a software architecture and design the software to implement and enforce security. Carnegie-Mellon has pre-established programming standards by language that can be found at www.cert.org/secure-coding/scstandards.html
- Remember the K-I-S-S (Keep It Simple, Stupid) principle. Complex designs increase the likelihood of errors or vulnerabilities and the need for security mechanisms or resulting mitigations to become more complex.
- Base access decisions on permission rather than exclusion to adhere to the principle of least privilege.
- Sanitize data sent to other systems, such as command shells, relational databases, and commercial off-the-shelf (COTS) components.
- Practice defense in depth within the application, so that if one layer of defense turns out to be inadequate, another layer of defense can prevent or limit a security flaw from becoming an exploitable vulnerability.
- Establish good quality assurance techniques to be more effective in identifying and eliminating vulnerabilities.
- Develop and/or apply a secure coding standard for your target development language and platform.
- Define security requirements at the start of the project.
- Think like a hacker and use threat modeling to anticipate the threats to which the software may be subjected. If you consider how it can be attacked, you will be able to prevent the attack before it can occur.

## 38.3.5 Languages.

To date, no common computer languages have security specific features built-in. Java does include provisions for limiting access to resources outside the “sandbox” reserved for a process, as described in the books by Felten and McGraw. Nevertheless, Java is still one of the languages targeted as an attack vector by many malware implementations. Pascal uses strong typing and requires full definition of data structures, thus making it harder to access data and code outside the virtual machine defined for a given process. In contrast, C and C++ allow programmers to access any region of memory at any time the operating system permits it.

Computer languages allow developers to write code as well as they can. Strongly typed languages may offer better constraints on programmers, but the essential requirement is that the programmers continue to think about security as they design and build code.

There are several sets of security utilities and resources available for programmers; for example, RSA has a number of cryptographic toolkits. Some textbooks (e.g., Schneier's Applied Cryptography) include CD-ROMs with sample code. In addition, the Computer Emergency Response Team Coordination Center (CERT/CC) was started in December 1988 by the Defense Advanced Research Projects Agency (DARPA), which was part of the U.S. Department of Defense. CERT/CC is located at the Software Engineering Institute, a federally funded research center operated by Carnegie Mellon University.

CERT/CC studies Internet security vulnerabilities, provides services to Websites that have been attacked, and publishes security alerts. CERT/CC's research activities include the area of WAN computing and developing improved Internet security.

As mentioned in Section 38.3.4, Carnegie-Mellon has established secure coding standards based on language that can help establish a uniform set of principles and guidelines across your development group. Regardless of the language selected for software development, it is important to make the decision based on the strengths and weaknesses of the language. This means that a risk analysis needs to be a part of the design of any development project, including the selection of the development language. By understanding those strengths and weaknesses, better decisions can be made to prevent the inherent vulnerabilities within the language from becoming exposed inadvertently during development.

## 38.4 Types of Software Errors.

New programmers should review the range of root causes for software errors. Such review is particularly useful for students who have completed training that did not include discussions of systematic quality assurance methodology. The next sections can serve as a basis for creating effective sets of test data and test procedures for unit tests of new or modified routines.

### 38.4.1 Internal Design or Implementation Errors.

A general definition of a software error is a mismatch between a program and its specifications: a more specific definition is the failure of a program to do what the end user reasonably expects. There are many types of software errors. Some of the most important include:

- Initialization
- Logic flow
- Calculation
- Boundary condition violations
- Parameter passing
- Race condition
- Load condition
- Resource exhaustion
- Resource, address, or program conflict with the operating system or application(s)
- Regulatory compliance considerations
- Other errors

#### 38.4.1.1 Initialization.

Initialization errors are insidious and difficult to find. The most insidious programs save initialization information to disk and fail only the first time used—that is, before they create the initialization file. The second time a given user activates the program, there are no further initialization errors. Thus, the bugs appear only to employees and customers when they activate a fresh copy of the defective program. Other programs with initialization errors may show odd calculations or other flaws the first time they are used or initialized; because they do not store their initialization values, these initialization errors will continue to reappear each time the program is used.

#### 38.4.1.2 Logic Flow.

Modules pass control to each other or to other programs. If execution passes to the wrong module, a logic-flow error has occurred. Examples include calling the wrong function, or branching to a subroutine that lacks a RETURN instruction, so that execution falls through the logical end of a module and begin executing some other code module.

#### 38.4.1.3 Calculation.

When a program misinterprets complicated formulas and loses precision as it calculates, it is likely that a calculation error has occurred; for example, an intermediate value may be stored in an array with 16 bits of precision when it needs 32 bits. This category of errors also includes computational errors due to incorrect algorithms.

#### 38.4.1.4 Boundary Condition Violations.

Boundaries refer to the largest and smallest values with which a program can cope; for example, an array may be dimensioned with 365 values to account for days of the year, and then fail in a leap year when the program increments the day-counter to 366 and thereby attempts to store a value in an illegal address. Programs that set variable ranges and memory allocation may work correctly within the boundaries but, if incorrectly designed, may crash at or outside the boundaries. The first use of a program also can be considered a boundary condition.

One of the most important types of boundary violations is the buffer overflow. In this error, data placed into storage exceed the defined maximum size and overflow into a section of memory identified as belonging to one or more different variables. The consequences can include data corruption (e.g., if the overflow overwrites data that are interpreted as numerical or literal values) or changes in the flow of execution (e.g., if the altered data include logical flags that are tested in branch instructions).

Buffer overflows have been exploited by writers of malicious code who insert data that overflows into memory areas of interpreted programs and thus become executed as code.

All programs should verify that the data being stored in an array or in any memory location do not exceed the expected size of the input. Data exceeding the expected size should be rejected or, at least, truncated to prevent buffer overflow.

#### 38.4.1.5 Parameter Passing.

Sometimes there are errors in passing data back and forth among modules. For instance, a call to a function accidentally might pass the wrong variable name so that the function acts on the wrong values. When these parameter-passing errors occur, data may be corrupted, and the execution path may be affected because of incorrect results of calculations or comparisons. As a result, the
