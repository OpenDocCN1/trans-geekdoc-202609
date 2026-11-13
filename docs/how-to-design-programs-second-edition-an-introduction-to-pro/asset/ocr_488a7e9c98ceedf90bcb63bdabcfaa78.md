those built from other sentences. For example, the `def` part tells us that a function definition is formed by using “(”, followed by the keyword `define`, followed by another “(”, followed by a sequence of at least two variables, followed by “)”, followed by an `expr`, and closed by a right parenthesis “)” that matches the very first one. Note how the leading keyword `define` distinguishes definitions from expressions.

Expressions (`expr`) come in six flavors: variables, constants, primitive applications, (function) applications, and two varieties of conditionals. While the first two are atomic sentences, the last four are compound sentences. Like `define`, the keyword `cond` distinguishes conditional expressions from applications.

Here are three examples of expressions: "all", `x`, and `(f x)`. The first one belongs to the class of strings and is therefore an expression. The second is a variable, and every variable is an expression. The third is a function application, because `f` and `x` are variables.

In contrast, these parenthesized sentences are not legal expressions: `(f define)`, `(cond x)`, and `((f 2) 10)`. The first one partially matches the shape of a function application but it uses `define` as if it were a variable. The second one fails to be a correct `cond` expression because it contains a variable as the second item and not a pair of expressions surrounded by parentheses. The last one is neither a conditional nor an application because the first part is an expression.

Finally, you may notice that the grammar does not mention white space: blank spaces, tabs, and newlines. BSL is a permissive language. As long as there is some white space between the elements of any sequence in a program, DrRacket can understand your BSL programs. Good programmers, however, may not like what you write. These programmers use white space to make their programs easily readable. Most importantly, they adopt a style that favors human readers over the software applications that process programs (such as DrRacket). They pick up this style from carefully reading code examples in books, paying attention to how they are formatted.

> *Keep in mind that two kinds of readers study your BSL programs: people and DrRacket.*

# **Exercise 116.** Take a look at the following sentences: