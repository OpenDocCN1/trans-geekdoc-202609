For example, in the recursive count-down function below,
recursion terminates when n becomes zero.

The base and general cases can be expressed as:

Base case: t(0) = 0

General case: t(n) = 1 + t(n - 1) for n > 0

Given those conditional cases with n = 3, the recurrence
relation of a countdown function could be solved as:

t(3) = 1 + t(n - 1) or 1 + 2 = 3
t(2) = 1 + t(n - 1) or 1 + 1 = 2
t(1) = 1 + t(n - 1) or 1 + 0 = 1

As you can see, t(n) = n for all n > 0. This is still true if we
substitute n - 1 for t(n - 1), for all n > 0. That is, by inductive
reasoning we accept as true that
t(n) = base case + general case.

# 11.5 TRACKING RECURSION USING A STACK

To execute a recursive function, a programming language is
generally expected to first generate one or more stack data
structures in memory that consist of operations and data. The
area of the stack for a particular function call is termed a stack
frame or activation record. Once this stack is loaded into
memory, it is then executed.

Table 11.1 illustrates such a call sequence for a recursive
function that counts down, displaying the numbers 9 to 1 with
each recursive call.