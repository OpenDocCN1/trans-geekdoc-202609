# Writing High-Quality Code

If you've worked your way through the PHP book thus far, you have a good grounding in the techniques to write complex PHP Web applications. Congratulations! Before concluding the book, however, it's worth taking a look at how to write high-quality applications. The term “high-quality” is somewhat subjective, but for the purposes of this book it means that:

+   - Is easy to read, maintain, and extend
- Is secure — that is, protected from attacks
- Handles error conditions and problems in a robust and graceful way
- Is well tested

As your Web applications grow larger and more complex, the quality of your code becomes more and more important. A large code base can quickly become error-prone and difficult to work with strict quality standards aren't maintained. In this chapter you learn the following quality-control techniques:

+   - Splitting your code into manageable, reusable chunks
- Using a set of coding standards to keep your code easy to read
- Writing documentation to improve readability for other programmers who work on your code
- Validating input, well as encoding output, to mitigate the risk of security holes in your code
- Dealing with error conditions — that is, handling abnormal situations while your code is running
- Cleanly separating your application’s business logic from its user interface
- Using automated testing frameworks to improve the quality of your code