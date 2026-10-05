# Fundamentals of the q Programming Language

1 2 3~1 2

0b

# 1.3.2 Arithmetic Operations and Right-to-Left Evaluation: Introduction to q Philosophy

Before we dive into the world of big data analytics and machine learning, we should at least be confident that we know how to sum up or multiply two numbers. Feeling courageous, we attempt to do both:

```
10*100+1000
```

Wait! The answer should be 2000 under the usual mathematical conventions. q thinks otherwise, though. In its quest for efficiency, speed and less program noise – aka “We Don’t Need Stinkin ‘Brackets’” (Brorror, 2015) – q follows a simple parsing rule: Expressions are evaluated right-to-left, and all operators have the same priority. This may look bizarre to a newbie but results in simplicity, since there is only one rule. One may disagree with this decision, but nothing can be done about it. It makes the parsing of statements simpler and faster. As a result, the following two expressions yield different results:

```
v:1 2 3
neg[v]+3
```

```
2 1 0
```

```
neg v+3
```

```
-4 -5 -6
```

Our initial example can be written as:

```
1000+10*100
```

We have explicitly stated that we want to first evaluate 10*100 and then add 1000. Even though this decomposition may seem obvious, thinking in terms of the operator precedence commonly used in other programming languages, such as Python, Java, and C++ may result in trivial but hard to detect errors until our brains get used to the q way.

We could have achieved the desired result of 2000 by using brackets in our initial example:

```
(10*100)+1000
```