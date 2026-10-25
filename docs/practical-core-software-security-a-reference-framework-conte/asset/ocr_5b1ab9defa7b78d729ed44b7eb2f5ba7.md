# Input
(Running application, infrastructure, or operational deployment [Source Code not required])

# Testing
(Fuzz Testing)

# Output
(Potential Defects Identified)

+   - Does not have access to the actual instructions the software will be executing.
+   - Cannot point out exact location of problem in code.
+   - Works by providing random and invalid inputs that can cause application to crash.

+   - Defects identified include application/system crashes, assertion failures, memory leaks, error handling, and invalid input problems.
+   - Limited utility in finding bugs that do not cause crash.

Figure 6.5 Fuzz testing flow diagram.

software. Although all of the issues found by fuzzing tools are critical and exploitable, unlike static analysis tools, fuzzing can only find bugs that can be accessed through an open interface. Fuzzing tools must also be able to interoperate with the tested software so that they can access the deeper protocol layers and test the system more thoroughly by testing multiple layers.

Although static analysis has the benefit of full test coverage and is a good method for improving the general software quality level, it cannot easily provide test results that solve complex problems, and, as discussed previously, it also results in a large number of false positives, both of which require further analysis by a human and consume valuable and limited resources. There are no false positives in fuzz testing because every flaw discovered is a result of a simulated attack

Static analysis is performed on code that is not being executed, and it can only be performed offline. In contrast, fuzz testing must be executed against executable code, can be run against live software, and, therefore, can find vulnerabilities that may not be visible in the static code. Fuzz testing targets the problems attackers would also find and, therefore, is a good test for robustness while also streamlining the process by focusing only on the most critical interfaces that may be susceptible to attack. Because of its ability to test robustness, fuzz testing is typically used during the verification phase of the SDLC just before product release. As with static and dynamic analysis, fuzz testing can be used from the moment the first software components are ready and even after release—not just at some point in time during the SDLC process. This attribute, of course, can yield significant cost savings by finding and fixing vulnerabilities early in the SDLC.

Standard fuzz testing techniques are limited in their use of random mutation to create test cases, which will find only some of the software vulnerabilities. However, this testing still has value because these are the same vulnerabilities that attackers would find. It is important to