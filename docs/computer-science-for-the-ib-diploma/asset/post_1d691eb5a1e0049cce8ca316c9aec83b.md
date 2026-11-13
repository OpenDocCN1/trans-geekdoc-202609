
## Count-controlled loop flowchart

If n is the number of repetitions required, a FOR loop would look like this:

```java
for(int i = 0; i<n; i++) {
  //code to be repeated
}
```

```python
for i in range (0,n):
  #code to be repeated
```

In Java, i = 0 is the starting point of the repetition, so i is initialized to 0. i<n is the condition to be met so, when i is no longer smaller than n, the repetition will stop. As the variable i was initially 0 to avoid running the code to infinite, the value of i needs to be changed with every repetition. In this case, i is incremented (i++).

In Python, the range indicates the initial value of i (in this case, 0) and the ending value of i (in this case, n). Note here that the code will stop when i becomes n-1. For example, if n = 5, i will take the values of 0, 1, 2, 3, 4. There are five repetitions in total; when i reaches the value of 5, the repetition will stop and so the value won't be displayed.

In the example above, because the starting point is 0, which is the default value, the statement could have been written as for i in range (n) : and it would have had the same effect.

In both Java and Python, the starting point can be changed. Consider that you must display all the numbers between 1 and 100. To solve this problem, you can set the starting point to 1 and the ending point to 101, ensuring 100 is also included.

```java
for(int i = 1; i<101; i++) {
  System.out.println(i);
}
```

```python
for i in range (1,101):
  print(i)
```

The Java example could have used the less-than-or-equal-to sign in the condition to ensure the upper bound of 100 is included. Alternatively, the loop could have been maintained to iterate from 0 to 100, with the printing statement adjusted to display the value of i+1 instead.

```java
for(int i = 1; i<=100; i++) {
    System.out.println(i);
}
```

```python
for i in range (100):
    print (i+1)
```

Imagine wanting to display all the odd numbers between 1 and 100. A solution would be to keep the same structure as before, but to check whether or not the number is odd.

```java
for(int i = 1; i<=100; i++) {
    if (i%2 == 1) {
        System.out.println(i);
    }
}
```

```python
for i in range (1,100):
    if (i%2 == 1):
        print (i)
```

i%2==1 checks whether the remainder of division by 2 of the variable i is 1. In other words, if there is a remainder, the number is odd; if there is no remainder, the number is even. The same problem can be solved without the need to use an IF statement. A step can be included to change the incrementation so, instead of incrementing the value of i by 1, which is the default value, it increments it by a different value.

```java
for(int i = 1; i<=100; i=i+2) {
    System.out.println(i);
}
```

```python
for i in range (1,100,2):
    print (i)
```

In this situation, in Java, the increment was changed, so the value of i is increased by 2, and in Python a step was included: 2, to specify the same thing. So, the variable i will take the values: 1, 3, 5, ... 99. But what if you are requested to display the numbers from 100 to 1 instead?

```java
for(int i = 100; i>0; i=i-1) {
    System.out.println(i);
}
```

```python
for i in range (100,0,-1):
    print (i)
```

In Java, the starting point is set to 100, so that value is displayed first. The condition is changed, as you want to repeat as long as the value is greater than 0, and also the step is changed to decrement the value instead of incrementing it. i=i-1 could be written as i--.
In Python, the range is changed to start at 100. It should stop when it reaches 1 (0 is not touched) and the step is set to -1, so the number is decremented by 1.

## Pre-condition loop

```
i = 0
loop while
......
i = i + 1
end loop
```

## General structure

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_331_0.png)

- Termination condition: a condition in a loop that interrupts or stops the repetition.
- Validation: a process to ensure input data is sensible or reasonable.
- Verification: a process to ensure input data is accurately copied from one source to another.

## Pre-condition loop flowchart

A pre-condition (WHILE) loop is used when the number of repetitions is not known prior to the execution of the code. The code is expected to be repeated as long as a condition is met, or it evaluates to true.
When the condition is no longer met, called termination condition, the loop execution will stop. In a WHILE loop, the repetition might not run at all; this happens when the condition is never met. WHILE loops are loops that are often used for validation or verification purposes. For example, when the user is asked to enter a password twice, the computer will compare the two entries to check if they match (double entry verification). In this case, a loop would be used to repeat entering the password until the two inputs match.

```java
String password, pass;
password = "apple";
System.out.println("Re-enter the password:");
pass = read.nextLine();
while (! password.equals(pass)) {
    System.out.println("Re-enter the password:");
    pass = read.nextLine();
}
System.out.println("The two passwords matched");
```

In this case, .equals is used to compare the value stored in password with the one stored in pass, as those two values are of type string. If the two values were numbers, then == would be used for comparison. The ! is a negation, therefore, in this case, it is checking if the two values are not the same, and the user is asked to re-enter the password until the two values match. The output at the end will be displayed only after the loop is exited. If the second password never matches the first, the code inside the loop will continuously repeat.

Any FOR loop can be rewritten as a WHILE loop. Considering our example that displays all the numbers between 1 and 100, using a WHILE loop the code would look like this:

### Java
```java
int i = 1;
while(i<101) {
    System.out.println(i);
    i = i+1;
}
```

### Python
```python
i = 1
while (i<101) :
    print(i)
    i=i+1
```

In the example above, the loop will repeat as long as i is smaller than 101. The termination condition will be that i>=101. The role of the incrementation is to change the value of i, so the loop will stop at one moment. Otherwise, without that statement, the loop would run to infinite.

## Post-condition loop

```
i = 0
repeat
......
i = i + 1
until i >= n
```

## General structure

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_333_0.png)

## Post-condition loop flowchart

In the post-condition (REPEAT-UNTIL) loop, the condition is checked at the end. In this case, the code inside the loop will execute at least once.

Both in Java and Python, post-condition loop structures are written using WHILE loops.

```java
int i = 1;
do {
   System.out.println(i);
   i = i+1;
} while(i<=100);
```

```python
i = 1
while(True) :
   print(i)
   i=i+1
   if i>100:
      break
```

In the example above, the variable i is initially set to 1. This value is displayed and then incremented. This happens no matter what the condition evaluates to. If the condition evaluates to true, the loop is repeated; if the condition evaluates to false, the repetition stops.

## REVIEW QUESTIONS

- 1 Define the term "loop".
- 2 Explain why it is useful to use loops in coding.
- 3 Explain the difference between a pre-condition and a post-condition loop.
- 4 Identify a situation when you would use a count-controlled loop.
- 5 Define the term "termination condition".
- 6 Explain why it is important to avoid infinite loops.
- 7 Identify a situation where an infinite loop could occur.

## PROGRAMMING EXERCISES

- 1 Construct a program that allows the user to enter a number. Output all numbers between 1 and that number.
- 2 Construct code that requires the user to enter a number and a word. Display each letter in the word on a separate line. Repeat the process the user's number of times.
- 3 Construct code that asks the user to input ten numbers. Calculate and display the sum of all even numbers entered.
- 4 Construct a program that creates a variable and initializes it to the value 7. Ask the user to guess a number between 1 and 20. If the user guesses the value 7, output the number of attempts. Do not allow the user to try to guess the number more than three times. If the user doesn't guess the number after three attempts, output the message: "The game is locked. Try again later!"
- 5 Construct a program that asks the user whether they want an apple. Repeat the question until their answer is yes. At the end, output the message: "Apples are delicious, aren't they? Let's have one!"

## ACTIVITY

- 1 What loop did you use to solve question 1? Could you replace that loop with another one? How would you do that?
- 2 Did the program you constructed to solve question 2 handle user input correctly? Can you think of an easier way to extract each letter from a given word?
- 3 Did your program for question 3 extract the even numbers correctly? What change would calculate the sum of all the odd numbers instead?
- 4 Why do you think a FOR loop is not appropriate for solving question 4?
- 5 What termination condition did you use for question 5?

## Top tip!

When you are asked to identify the type of loop exemplified in a piece of code, refer to them as count-controlled, pre-condition or post-condition loops. For example, saying it is a FOR loop instead of a "count-controlled" loop is not enough, as it is not clear that you know what type of loop a FOR loop is.

## Key information

FOR loops are called "count-controlled" loops, WHILE loops are called "pre-condition" loops and REPEAT-UNTIL loops are called "post-condition" loops.

Count-controlled loops are used when the number of repetitions is known prior to the execution of the code. Pre-condition loops might not be executed at all (if the condition is not met). Post-condition loops will execute at least once, even if the condition is never met.
