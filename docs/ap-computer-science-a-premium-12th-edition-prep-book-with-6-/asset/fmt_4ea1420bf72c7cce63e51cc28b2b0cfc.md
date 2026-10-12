
# 练习题

## 问题 11
Let `list` be an `ArrayList<String>` containing only these elements.

![images](images/f386-02.jpg)

Which of the following statements will cause an error to occur?

I. `list.set(2, "6");`
II. `list.add(4, "Pat");`
III. `String s = list.get(4);`

(A) I only
(B) II only
(C) III only
(D) II and III only
(E) I, II, and III

## 问题 12
Consider the following static method.

![images](images/f386-03.jpg)

Which of the following could replace the body of `compute`, so that the new version returns the identical result as the original for all `n`?

(A) `return 4 * n;`
(B) `return 8 * n;`
(C) `return 64 * n;`
(D) `return (int) Math.pow(n, 4);`
(E) `return (int) Math.pow(n, 8);`

## 问题 13
Consider the following instance variable and method.

![images](images/f387-01.jpg)

Suppose the following statement is executed.

`int j = getValue();`

If the value returned in `j` is a positive integer, which of the following best describes the contents of `nums`?

(A) The only odd `int` in `nums` is at position `j`.
(B) All values in positions `0` through `j-1` are odd.
(C) All values in positions `0` through `j-1` are even.
(D) All values in positions `nums.length-1` down to `j+1` are odd.
(E) All values in positions `nums.length-1` down to `j+1` are even.

## 问题 14
Consider the following method.

![images](images/f387-03.jpg)

What will be returned by a call to `mystery(6)`?

(A) 6
(B) 11
(C) 12
(D) 27
(E) 30

## 问题 15
Consider the following code segment.

![images](images/f388-01.jpg)

You may assume that `value1`, `value2`, and `value3` are `int` values. Which of the following is sufficient to guarantee that `/* body of loop */` will never be executed?

(A) There is no statement in `/* body of loop */` that leads to termination.
(B) `num1 < num2`
(C) `num1 < num3`
(D) `num1 > num2 && num1 > num3`
(E) `num1 < num2 && num1 < num3`

## 问题 16
Consider the following two classes.

![images](images/f389-01.jpg)
![images](images/f389-02.jpg)
![images](images/f389-03.jpg)

Suppose the following declaration appears in a class other than `Performer` or `Singer`.

`Performer p = new Singer();`

What is printed as a result of the call `p.act();`?

(A) `rise bow aria encore`
(B) `rise bow act encore`
(C) `rise bow act`
(D) `bow act aria`
(E) `bow aria encore`

---

Use the program description below for Questions 17–19.

A car dealer needs a program that will maintain an inventory of cars on his lot. There are four types of cars: sedans, station wagons, electric cars, and SUVs. The model, year, color, and price need to be recorded for each car, plus any additional features for the different types of cars. The program must allow the dealer to

![images](images/sq1.jpg) Add a new car to the lot.
![images](images/sq1.jpg) Remove a car from the lot.
![images](images/sq1.jpg) Correct any data that have been entered.
![images](images/sq1.jpg) Display information for any car.

## 问题 17
The programmer decides to have these classes: `Car`, `Inventory`, `Sedan`, `SUV`, `ElectricCar`, and `StationWagon`. Which statement is true about the relationships between these classes and their attributes?

I. There are no inheritance relationships between these classes.
II. The `Inventory` class *has-a* list of `Car` objects.
III. The `Sedan`, `SUV`, `ElectricCar`, and `StationWagon` classes are independent of each other.

(A) I only
(B) II only
(C) III only
(D) I and II only
(E) II and III only

## 问题 18
Suppose that the programmer decides to have a `Car` class and an `Inventory` class. The `Inventory` class will maintain a list of all the cars on the lot. Here are some of the methods in the program.

![images](images/f390-01.jpg)

In each of the following, a class and a method are given. Which is the least suitable choice of class to be responsible for the given method?

(A) `Car`, `setColor`
(B) `Car`, `removeCar`
(C) `Car`, `getPrice`
(D) `Car`, `displayCar`
(E) `Inventory`, `displayAllCars`

## 问题 19
Suppose `Car` is a superclass and `Sedan`, `StationWagon`, `ElectricCar`, and `SUV` are subclasses of `Car`. Which of the following is the most likely method of the `Car` class to be overridden by at least one of the subclasses (`Sedan`, `StationWagon`, `ElectricCar`, or `SUV`)?

![images](images/f391-01.jpg)

## 问题 20
Consider the following segment of code.

![images](images/f391-02.jpg)

What will be the result of executing the above segment?

(A) A syntax error will occur.
(B) String `s` will be the empty string.
(C) String `s` will contain `"flag"`.
(D) String `s` will contain `"conf"`.
(E) String `s` will contain `"con"`.

## 问题 21
A two-dimensional matrix `mat` with at least one row is initialized and will be traversed using a row-major (row-by-row, left-to-right) traversal. Which represents the last element accessed?

(A) `mat[mat.length][mat[0].length]`
(B) `mat[mat[0].length][mat.length]`
(C) `mat[mat.length - 1][mat[0].length - 1]`
(D) `mat[mat[0].length - 1][mat.length - 1]`
(E) `mat[mat.length - 1][mat.length - 1]`

## 问题 22
A class of 30 students rated their computer science teacher on a scale of 1 to 10 (1 means awful and 10 means outstanding). The `responses` array is a 30-element integer array of the student responses. An 11-element array `freq` will count the number of occurrences of each response. For example, `freq[6]` will count the number of students who responded 6. The quantity `freq[0]` will not be used.

Here is a program that counts the students' responses and outputs the results.

![images](images/f392-01.jpg)

Suppose the last entry in the initializer list for the `responses` array was incorrectly typed as `12` instead of `2`. What would be the result of running the program?

(A) A rating of 12 would be listed with a frequency of 1 in the output table.
(B) A rating of 1 would be listed with a frequency of 12 in the output table.
(C) An `ArrayIndexOutOfBoundsException` would be thrown.
(D) A `StringIndexOutOfBoundsException` would be thrown.
(E) A `NullPointerException` would be thrown.

---

Questions 23–25 are based on the three classes below.

![images](images/f393-01.jpg)
![images](images/f393-02.jpg)
![images](images/f393-03.jpg)

## 问题 23
The `computePay` method in the `Consultant` class redefines the `computePay` method of the `Employee` class to add a bonus to the salary after subtracting the tax withheld. Which represents correct `/* implementation code */` of `computePay` for `Consultant`?

I. `return super.computePay() + BONUS;`
II. `super.computePay();`  
   `return getSalary() + BONUS;`
III. `return getSalary() - getTax() + BONUS;`

(A) I only
(B) II only
(C) III only
(D) I and III only
(E) I and II only

## 问题 24
Consider these valid declarations in a client program.

![images](images/f394-02.jpg)

Which of the following method calls will cause an error?

(A) `double x = e.computePay();`
(B) `double y = p.computePay();`
(C) `String n = c.getName();`
(D) `int num = p.getEmployeeNum();`
(E) `double g = p.getPayFraction();`

## 问题 25
Consider the `writePayInfo` method.

![images](images/f395-01.jpg)

The following piece of code invokes this method.

![images](images/f395-02.jpg)

What will happen when this code is executed?

(A) A `NullPointerException` will be thrown.
(B) An `ArrayIndexOutOfBoundsException` will be thrown.
(C) A compile-time error will occur, with the message that the `getName` method is not in the `Consultant` class.
(D) A compile-time error will occur, with the message that an instance of an `Employee` object cannot be created.
(E) A list of employees' names and corresponding pay will be written to the screen.
