
![](img/3d5da05d64722faaa72fdc4daca105f9_206_0.png)
![](img/3d5da05d64722faaa72fdc4daca105f9_206_1.png)
![](img/3d5da05d64722faaa72fdc4daca105f9_206_2.png)
![](img/3d5da05d64722faaa72fdc4daca105f9_206_3.png)

For n = 3:

+   1. X→Y
2. X→T
3. Y→T
4. X→Y
5. T→X
6. T→Y
7. X→Y

![](img/3d5da05d64722faaa72fdc4daca105f9_206_4.png)

![](img/3d5da05d64722faaa72fdc4daca105f9_207_0.png)

# The formula for finding the number of steps it takes to transfer n disk from X to Y is 2^n-1

| Number of disks (n) | Number of moves |
| --- | --- |
| 1 | 2^1-1 = 2-1 = 1 |
| 2 | 2^2-1 = 4-1 = 3 |
| 3 | 2^3-1 = 8-1 = 7 |
| 4 | 2^4-1 = 16-1 = 15 |

# POINTS TO REMEMBER

+   1. A stack is a linear data structure in which elements are added and remove only from one end, which is called the top. Hence, a stack is called a LIFO data structure as the element is inserted last is the first one to be taken.

+   2. In the computer's memory, stacks can be implemented using either linked lists or single arrays.

+   3. Infix, prefix, and postfix notations are different but equivalent notations of writing algebraic expressions.

+   4. In postfix notation, operators are placed after the operands, whereas in prefix notation, operators are placed before the operands.

+   5. Postfix notations expression that is scanned from left to right. If the character is an operand, it is pushed onto the stack. Else, if it is an operator, the top two values are popped from the stack and the operator is applied on these values. The result is pushed onto the stack.

+   6. Multiple stacks means to have more than one stack in the same array of sufficient size.

# MULTIPLE CHOICE QUESTIONS

+   1. Stack is a
(a) LIFO (b) FIFO
(c) FILO (d) LIFO

+   2. Which function places an element on the stack?
(a) Pop() (b) Push()
(c) Peek() (d) Iempty()

# Chapter 4 Stack

+   3. Disks piled up one above the other represent a
(a) Stack (b) Queue
(c) Linked list (d) array

+   4. Reverse polish notation is the other name of
(a) Infix expression (b) Prefix expression
(c) Postfix expression (d) Algebraic expression

# TRUE OF FALSE

+   1. Pop () is used to add an element on the top of the stack.
2. Postfix operation does not allow the rules of operator precedence.
3. Recursive follows a divide-and-conquer technique to solve problems.
4. Using a recursive function takes more memory and time to execute.
5. Recursion is more of a bottom-up approach to solving.
6. An indirect recursive function if it contains a call to another function which ultimately calls it.
7. The peeks operation displays the topmost value and deletes it from the stack.
8. In a stack, the element that was inserted last is the first one to be taken out.
9. Underflow occurs when top=max-1.
10. Overflow can never occur in case of multiple stacks.

# FILL IN THE BLANKS

+   1. ________ is used to convert an infix expression into a postfix expression.
2. ________ is used in a non-recursive implementation of an algorithm.
3. The storage requirement of a linked stack with n elements is ________.
4. Underflow takes when ________.
5. The order of evaluation of a postfix expression is from ________.
6. Whenever there is a pending operation to be performed, the function becomes recursive.
7. A function is said to be ________ recursive if it explicitly calls itself.

# EXERCISES

+   1. What do you understand by stack overflow and underflow?
2. How does a stack implement using linked list?
3. How does a stack implement using array?

4. The following sequence of operation is done on an empty stack: PUSH ‘S’, PUSH ‘S’, PUSH ‘T’, PUSH ‘U’, POP, PUSH ‘A’, PUSH ‘L’, PUSH ‘G’, POP, PUSH ‘C’, PUSH ‘A’, PUSH ‘B’, POP, POP. Show the stack configuration after each operation?

5. Convert the following infix expression to postfix expression:

+   (a) A–B + C
(b) A * B + C / D
(c) (A - B) + C * D / E - C
(d) (A * B) + (C / D) - (D + E)
(e) ((A - B) + D / ((E + F) * G))
(f) 14 / 7 * 3 - 4 + 9 / 2

6. Convert the following infix expression to prefix expression:

+   (a) A–B + C
(b) A * B + C / D
(c) (A - B) + C * D / E - C
(d) (A * B) + (C / D) - (D + E)
(e) ((A - B) + D / ((E + F) * G))
(f) 14 / 7 * 3 - 4 + 9 / 2

7. Differentiate between an iterative function and a recursive function?

8. Explain the Tower of Hanoi problem?

# REFERENCES

+   1. Bruno, JL and T. Lassagne, The generation of optimal code for an attack machine, 1975.
+   2. Donald Knuth, The Art of Programming, Vol. 2, 1984.
+   3. Forsythe, A., Computer Science: A Course, John Wiley, 1986.
+   4. Harrison, M., Data Structures, Addison-Wesley, 1985.
+   5. Seth, J., The generation of optimal code for an attack machine, Journal of ACM, 1970.

# 5 Queues

## 5.1 INTRODUCTION

Queues arise naturally in problems. The most common occurrence of queue is standing in mall, ticket counter, etc. The first person in will be the first out. Thus, queue is also called First-In-First-Out (FIFO).

## 5.2 REPRESENTATION OF QUEUES

Queues, being linear data structure, can be represented by using arrays and linked lists.

### 1. Queue Using Array

Array is data structure that stores a fixed number of. One of the major limitations of array is that its size keeps fixed. Thus, if queue is implemented using arrays, we must be sure that the exact number of elements we want to store.

#### Operation on Queue using Array

(a) Insertion (Rear)
(b) Deletion (Front)

# Algorithm for queue insertion

Steps:
1. start
2. check overflow condition
if rear=max-1 then
write “OVERFLOW” and then
stop
3. read data
4. if front=0 then
5. queue[rear]=data
6. rear=rear+1
7. stop

# Algorithm for queue deletion

Steps:
1. start
2. check underflow condition
if Front==1 then
write "UNDERFLOW" and then
stop
3. if rear=front then
4. queue[front]=-1
5. front=0
6. front=front+1
7. stop

# Program: write a program to implement a queue array

```c
#include<stdio.h>
#define MAX 7
void insert(int);
int del();
int queue[MAX], rear=0, front=0;
void display();
void main()
{
int choice, token;
printf("\n1.Insert");
printf("\n2.Delete");
printf("\n3.show or display");
while(1)
{
printf("\nenter your choice for the operation: ");
scanf("%d",&choice);
switch(choice)
```
