```
{
  switch(a) {
    case '^':
      return 3;
      break;
    case '/':
    case '*':
      return 2;
      break;
    case '+':
    case '-':
      return 1;
      break;
    default:
      return 0;
  }
}
```

# Output

Convert Infix to Prefix Expression
Enter infix expression:- a+b-c*/d
Prefix Expression:- -+ab/*cde

+   c. **Convert infix expression into prefix expression in a tabular form**
The steps involved to convert the infix expression into prefix expression
1. Reverse the input string.
2. Examine the next element in the input
3. If it is operator, add it to output string
4. If it is closing parenthesis, push it on stack
5. If it is operator, then
   (a) If stack is empty, push operator on stack
   (b) If the top of the stack is closing parenthesis, push operator on stack
   (c) If it has same or higher priority than the top of stack, push operator on stack
   (d) Else pop the operator from the stack and add it to output string
6. If it is an opening parenthesis, pop operators from stack and add them to output string until a closing parenthesis is encountered. Pop and discard the closing parenthesis