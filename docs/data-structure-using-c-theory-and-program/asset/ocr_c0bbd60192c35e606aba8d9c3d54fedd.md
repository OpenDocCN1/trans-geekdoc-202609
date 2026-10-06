Chapter 4 Stack

*-P/QR-*STU

# Algorithm

Arithmetic Expression in infix notation. Two stacks are used, push(stkl, x) means adding an item x to stack stk1, pop(stkl) means removing the top most element from the stack stk1.

Steps:

+   1. start

+   2. infix_to_prefix(Arithmetic Expression)

+   3. initially added a left parenthesis '(' at the beginning of the infix expression Arithmetic Expression.

+   4. push(stkl, ')' )

+   5. set item = Arithmetic Expression.reorderscan_ch() //scan the symbol from Arithmetic Expression in right to left

+   6. repeat steps 7 to 28 while stk1 is not empty

+   7. if item = operand

+   8. push(stk2, item)

+   9. end of step 7 if structure

+   10. if item = '’

+   11. push(stkl1,item)

+   12. end of step 10 if structure

+   13. if item = operator

+   14. set x = pop(stk1)

+   15. if precedence(x)>precedence(item)

+   16. repeat steps 17 and 18 while precedence (x)> precedence(item)

+   17. push(stk2, x)

+   18. set x = pop(stk1)

+   19. end of step 16 while loop

+   20. end of step 15 if structure

+   21. push(stk1, x)

+   22. push(stk1, item)

+   23. end of step 13 if structure

+   24. if item = ‘‘

+   25. set x = pop(stk1)

+   26. repeat steps 27 and 28 while x ≠ '’

+   27. push(stk2, x)

+   28. set x = pop(stk1)

181