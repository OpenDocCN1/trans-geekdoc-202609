columns of output are limited to three columns when the output is directed back to the three stacks.

# ## B.3 POSTFIX

Words that process data operate in postfix mode, such as:

```
`operand1 operand2 operation`
```

Or:

```
`data data word`
```

Data can be the output of a preceding word and a word in this series may, itself, produce data for the next word. In this way words may be used as arguments for subsequently postfixed words.

# ## B.4 WORDS AS ARGUMENTS

The arguments for a word can have the following form:

+   * Numbers, characters, strings, functions (words).
+   * Self-reference (recursion): A word that refers to itself.
+   * Tick word: A word stored as data on the data stack.
+   * Lambda expression: A nameless function containing functional words and/or data.
+   * Captured word: A word inside the { scope } or definition of another word.
+   * Pipe: Bypass the data stack with one word's output being the next word's input. The output could be a