
# Code analyzers

Both automated tools and manual code review are used in code testing and analysis. The following sections look at some of the types of testing that code analysis could include, as shown in [Figure 19.5](#c19.xhtml#fig19_5):

![](images/Image31354.jpg)

**Figure 19.5:** Code Analyser

# Fuzzing

In order to evaluate how an application behaves, fuzz testing entails inserting erroneous or unexpected input (also known as faults) into it. It’s normally done with the help of a software program that automates the procedure. Environment variables, keyboard and mouse events, and API call sequences are all examples of inputs. The logic of the fuzzing process is depicted in [Figure 19.6](#c19.xhtml#fig19_6):

![](images/Image31362.jpg)

**Figure 19.6:** Fuzzing Process

To determine the susceptibility to a fault injection attack, two of the following methods of fuzzing can be used:

*   **Mutation fuzzing**: This type entails altering the current input values (blindly).
*   **Generation-based fuzzing**: This method entails creating inputs from scratch based on a specification or format.
*   Use fuzz testing to help uncover flaws and avoid fault injection attacks.
*   Follow proper coding and project management procedures.
*   Install firewalls at the application level.

Fuzzers are software tools that use a method called fuzzing to detect and exploit flaws in online applications. They work by inserting semi-random data into the program stack and then looking for problems. They are simple to use, but one of their drawbacks is that they are more likely to identify basic faults than the more sophisticated ones. `JBroFuzz` and `WSFuzzer` are two specialized tools recommended by OWASP, an organization dedicated to enhancing software security. `WSFuzzer` is primarily interested in HTTP-based SOAP services. A fuzzer could be used during the creation of a web application that will handle sensitive data, for example. The fuzzer will assist you in determining whether the program is processing error exceptions correctly.

Let’s imagine you have a web application that is still being tested, and you find that if you input your credentials incorrectly on the login page, the software crashes and you are greeted with a command prompt. If you wanted to explore the problem, you could use an online fuzzer to simulate the login screen. [Figure 19.7](#c19.xhtml#fig19_7) depicts a fuzzer named `Peach` with a mutator named `StringMutator` that changes the input on a regular basis. Some input to the tool can even cause a crash. `Peach` confirms the error by duplicating it. It sends extra information to a log, which you may analyze to figure out which string value caused the crash, as shown in [Figure 19.7](#c19.xhtml#fig19_7):

![](images/Image31369.jpg)

**Figure 19.7:** Peach Fuzzer Output

`Microsoft SDL File/Regex Fuzzer` consists of two components. The first is `File Fuzzer`, which creates random content in files, and the second is `Regex Fuzzer`, which tests regular expression-based routines. Although these tools are no longer accessible, Microsoft now offers a cloud-based fuzzing service. **Microsoft’s Security Risk Detection** (`MSRD`) solution employs artificial intelligence to automate the reasoning process used by security professionals to uncover problems, as well as cloud-based scalability. The user is guided through the fuzzing process by `Regex Fuzzer`.

# Static

Static testing is the process of evaluating or testing software while it is not in use. Code review is the most prevalent method of static analysis. The systematic analysis of the code for security and functional issues is known as code review. It can take many different forms, ranging from informal peer review to formal code review. There are two types of reviews as presented below.

*   **Formal evaluation**: This is a very detailed, line-by-line inspection that is frequently done by numerous people across several phases. This is the most time-consuming sort of code review, but it is also the most effective in terms of detecting bugs.
*   **Lightweight review**: Unlike a formal review, this style of code review is significantly more cursory. It is typically carried out as part of the development process. It can manifest itself in the following ways:
    *   **Pair programming**: Two coders work side by side, constantly verifying each other’s work.
    *   **Email**: When time allows, the code is emailed to colleagues for them to evaluate.
    *   **Over-the-shoulder**: Co-workers look over the code while the author explains why he or she did what they did.
    *   **Tool-assisted**: The most efficient technique is to use automated testing tools.

While code review is most commonly performed on internal programs, it may also be necessary for other situations. Assume you’re working with a third party to design a web application that will handle credit cards. Given the sensitive nature of the program, it’s not uncommon for you to seek a code review to assess the product’s security. Several tools should be utilized to test an application in many circumstances. For example, an online banking application that has had its source code updated should be subjected to both penetration testing and a code review of the important models to guarantee that no flaws exist.

# Dynamic

Dynamic testing is the process of testing software while it is in use. This testing can be done manually or with the help of automated testing software. Dynamic testing can be approached in the following two ways:

*   For websites and applications, **synthetic transaction monitoring**, a sort of proactive monitoring, is frequently favored. It gives visibility into the application’s availability and performance, alerting users to any possible issues before they notice a change in the app’s behavior. External agents are used to perform scripted transactions on an application. Synthetic transactions, for example, are used by `System Centre Operations Manager` to monitor databases, webpages, and TCP port utilization.
*   **Real user monitoring (`RUM`)** is a sort of passive monitoring that records and analyses every transaction made by a user of an application or website. Unlike synthetic monitoring, which tries to glean performance insights by testing simulated interactions on a regular basis, `RUM` eliminates the guesswork by showing you exactly how your users interact with the app.

# Misuse case testing

Misuse case testing, often known as negative testing, examines a program to ensure that it can manage unexpected behavior or invalid input. This testing is done to guarantee that an application does not crash and to improve the quality of the program by discovering its flaws. When organizations conduct misuse case testing, they should expect to identify issues. Testing for the following circumstances should be included in misuse testing:

*   All required fields must be filled out.
*   Fields that have a certain data type can only take data of that type.
*   Fields with a character limit only accept data that falls within that limit; fields with a set data range only take data that falls within that range.
*   Only valid data is accepted in fields.

# Test coverage analysis
