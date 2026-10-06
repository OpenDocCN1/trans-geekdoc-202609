```
temp=->;
printf("%d->",temp->info);
top=top->link;
free(temp);
}
}
```

# Output

Select the choice of operation on Stack

+   1. Push
2. Pop
3. Display Stack
4. Exit
enter the choice of operation you want to do 1
enter the value you want to insert in Stack 2
enter the choice of operation you want to do 1
enter the value you want to insert in Stack 3
enter the choice of operation you want to do 1
enter the value you want to insert in Stack 4
enter the choice of operation you want to do 1
enter the value you want to insert in Stack 5
enter the choice of operation you want to do 3
5-> 4-> 3-> NULL

# 4.4 APPLICATIONS OF STACK

Various applications of stack are known. A classical application in a compiler design is the evaluation of arithmetic expression; here the compiler uses a stack to translate an arithmetic expression into its corresponding object code. Some machines are also known which built-in stack hardware called stack machine. Another important application of a stack is during the execution of recursive programs; some programming languages use stacks to run recursive programs. One important feature of any programming language is the binding of memory variables. Such binding is determined by the scope rules.

+   1. Checking the validity of an Arithmetic Expression
2. Polish Notation
3. Recursion
4. Tower of Hanoi