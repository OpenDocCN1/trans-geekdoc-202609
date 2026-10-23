would, for example, turn an AST node representing 1 + 2 into an object.Integer{Value: 3}. With that, the life cycle of Monkey code would be complete and the result printed to the REPL.

This chain of transformations – from strings to tokens, from tokens to a tree and from a tree to object.Object – is visible from start to end in the main loop of the Monkey REPL we built:

```
// repl/repl.go

package repl

func Start(in io.Reader, out io.Writer) {
    scanner := bufio.NewScanner(in)
    env := object.NewEnvironment()

    for {
        fmt.Printf(PROMPT)
        scanned := scanner.Scan()
        if !scanned {
            return
        }

        line := scanner.Text()
        l := lexer.New(line)
        p := parser.New(l)

        program := p.ParseProgram()
        if len(p.Errors()) != 0 {
            printParserErrors(out, p.Errors())
            continue
        }

        evaluated := evaluator.Eval(program, env)
        if evaluated != nil {
            io.WriteString(out, evaluated.Inspect())
            io.WriteString(out, "\n")
        }
    }
}
```

That’s where we left Monkey at the end of the previous book.

And then, half a year later, the The Lost Chapter: A Macro System For Monkey resurfaced and told readers how to get Monkey to program itself with macros. In this book, though, The Lost Chapter and its macro system won’t make an appearance. In fact, it’s as if the The Lost Chapter was never found and we’re back at the end of Writing An Interpreter In Go. That’s good, though, because we did a great job implementing our interpreter.