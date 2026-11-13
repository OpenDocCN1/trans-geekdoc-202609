**Concatenation:** joining strings together.

# # Concatenation

Concatenation refers to joining two or more string values together. Both Java and Python allow several ways to achieve concatenation. One of them is with the + operator, which will join the two strings together.

```
```Java
String part1 = "Computer Science is fun";
String part2 = ", isn't it?";
String text = part1 + part2;
System.out.println(text);
```
```

```
```Python
part1 = "Computer Science is fun"
part2 = ", isn't it?"
text = part1 + part2
print(text)
```
```

Another function that can be used in Java to concatenate two strings is the function concat:

```
```Java
String part1 = "Computer Science is fun";
String part2 = ", isn't it?";
String text = part1.concat(part2);
System.out.println(text);
```
```

Note that concatenation is a technique that is applied to a series of string variables, rather than a combination of strings and integers or decimals. If there is a need to concatenate a combination of strings and integers, the + operator can be used in Java, or the integer or decimal value can be converted to a string prior to the concatenation taking place. In Python, the interpolation operator (%), the str function, str.format or f-strings can be used for this purpose.

```
```Java
String exam = "Computer Science";
int grade = 9;
System.out.println("Your " + exam + " exam score is " + grade);
```
```

```
```Python: Use of interpolation operator
exam = "Computer Science"
grade = 9
print ("%s%s%s" % ('Your ', exam, " exam score is ", grade))
```
```