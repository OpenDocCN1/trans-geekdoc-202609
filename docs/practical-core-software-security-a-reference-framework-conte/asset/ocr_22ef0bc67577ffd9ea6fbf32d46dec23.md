remember that attackers use fuzzing tools as well, and it is a tell-tale sign of a weak software security development program if fuzzing tools by discoverers or attackers find flaws in products you have already released to your customers. More sophisticated fuzzing techniques are used to improve and optimize coverage by using protocol specifications to target protocol areas most susceptible to vulnerabilities and to reduce the number of test cases needed without compromising test coverage. Static code analysis is used to ensure that secure coding policies are being followed, but protocol fuzzing tools are used to gain an attacker’s perspective to the threat and risk.

Another advantage of fuzz testing is that it can be used with black-box, gray-box, or white-box testing and does not require source code access. Like the dynamic analysis tools discussed in this chapter, this feature makes it a great tool for testing third-party software or software that has been outsourced for development. One drawback of fuzz testing, however, is that it is intrusive and may well crash the system, which will likely require initial testing to occur in a separate environment such as a testing lab or virtualized environment.

There are two main types of fuzz testing: “smart” and “dumb.”

+   - In “smart” (generational) fuzzing, the fuzzer pushes data to the program in a logical way, usually by waiting for responses and possibly altering the stack. This method requires in-depth knowledge of the target and specialized tools, but less crash analysis is required and also less duplication of findings than with dumb fuzzing.25,26
+   - In “dumb” (mutational) fuzzing, the fuzzer systematically pushes data to the program without waiting for proper responses. This method is closely tied to denial-of-service (DoS) attacks. This method requires no knowledge of the target and uses existing tools. However, more crash analysis is required, and there is more duplication of findings than with “smart” fuzzing.27,28

To carry out a fuzz test, the following steps are followed for each file or field that feeds into the application:

+   1. Enter random data or spaces to some part of the input file.
+   2. Execute the application with that input file.
+   3. Evaluate results. What broke? What ran as normal? What was expected to happen?
+   4. Number each test case and report findings to project management.29

# 6.4.4 Manual Code Review

Manual security code reviews are typically done as a line-by-line inspection of the software to determine any security vulnerabilities in the software product. This will include a thorough review of programming source code of multitier and multicomponent enterprise software products. After the use of multiple automated tools, which help quickly analyze flaws and vulnerabilities, the code is reviewed manually. Every issue discovered is validated, and the code is inspected to overcome the limitations of the automated tools and techniques. Coding errors can be found using different approaches, but even when compared to sophisticated tools, manual code reviews have clearly proven their value in terms of precision and quality. Unfortunately, manual code reviews are also the most expensive to execute.