# Chapter 4 Stack

+   7. If there is no input then go to step 2
8. If there is no more input, unstuck the remaining operators and add them
to output string
9. Reverse the output string.

# Evaluation of prefix Expression

PN is an expression in prefix notation

# Algorithm

Steps:

+   1. start

```
2. eval_prefix(PN)
3. append a left parenthesis '(' at the beginning of the prefix expression
4. set item = PN.reverseorderscan_ch() // the symbol from PN in
right to left
5. repeat steps 6 to 16 while item = '('
6. if item = operand
7. push(item)//operand is pushed into the stack
8. end of step 6 if structure
9. if item = operator
10. set a = pop() // a is the first operand of the current operator
11. set b = pop() // b is the second operand of the current operator
12. set op = item
13. set result = a op b
14. push(result)
15. end of step 9 if structure
16. set item = PN.reverseorderscan_ch()
17. end of step 5 loop
18. set result = pop())
19. write “result"
20. stop
```

# Example:

Suppose we want to convert: P+Q*R*(S*T^U+V)-W+X in prefix
form.

Reverse expression is: X+W-)V+U^T*S(*R*Q+P