
## 68

The question below uses a robot in a grid of squares. The robot is represented by the triangle, which is initially in the top-left square of the grid and facing toward the top of the grid.

![Images](images/f0416-01.jpg)

Code for the procedure `Mystery` is shown below. Assume that the parameter `p` has been assigned a positive integer value (e.g., 1, 2, 3, . . .).

![Images](images/f0416-02.jpg)

Which of the following shows possible results of running the code segment with any value of `p ≥ 0 AND p < 2`? **Select two answers.**

(A) ![Images](images/f0416-03.jpg)

(B) ![Images](images/f0416-04.jpg)

(C) ![Images](images/f0416-05.jpg)

(D) Error. The robot leaves the grid.

## 69

A theme park wants to create a simulation to determine how long it should expect the wait time to be at its most popular ride. Which of the following characteristics for the virtual patrons would be most useful? **Select two answers.**

(A) Ride preference—denotes whether a patron prefers roller coasters, other thrill rides, gentle rides, or no rides

(B) Walking preference—denotes how far a patron is willing to walk in between rides

(C) Food preference—denotes the type of food that a patron prefers to eat (e.g., chicken, burgers, salads)

(D) Ticket type—denotes whether the patron has a single-day pass, a multiday pass, or an annual pass

## 70

A robot is shown in the lower-left corner of a grid and is pointing up.

![Images](images/f0417-01.jpg)

![Images](images/p0417-01.jpg)

What procedure will result in the robot landing on the star? **Select two answers**.

(A) `moveAndSpin(4, 1)`
`moveAndSpin(6, 0)`

(B) `moveAndSpin(0, 1)`
`moveAndSpin(6, 3)`
`moveAndSpin(4, 0)`

(C) `moveAndSpin(7, 3)`

(D) `moveAndSpin(0, 7)`

## Answers Explained

### 1

**(C)**

Step 1: `num = 1`

Step 2: Enter the repeat until:

![Images](images/t0419-01.jpg)

The program will display the values 3 9.

(A) Although `num` has all the values 1 3 5 7 9 11, it will display only if `num MOD 3` equals 0. Only 3 and 9 `MOD 3` equal 0.

(B) Here, `1 MOD 3` equals 1, which would make the “If” statement false so 1 will not display; `5 MOD 3` equals 2, which would make the “If” statement false so 5 will not display; and `7 MOD 3` equals 1, which would make the “If” statement false so 7 will not display.

(C) Here, `9 MOD 3` is equal to 0 and will display. However, 3 is missing, so this answer is not correct.

### 2

**(D)**

`petList is initialized containing the value Dog`

`petList[Dog]`

- The value Cat is added to the end of `petList`
- `petList[Dog Cat]`
- The value Fish is added to the end of `petList`
- `petList[Dog Cat Fish]`

The value Golden Bandicoot is added at position 2 of `petList` and shifts all values after position 2 to the right.

- `petList [Dog Golden Bandicoot Cat Fish]`

The value in position 1 of `petList` is removed, and all values to the right of position 1 are shifted to the left: `petList[Golden Bandicoot Cat Fish]`

Each item in `petList` is displayed, resulting in `[Golden Bandicoot Cat Fish]`.

### 3

**(C)** Only I and II are true.

I. ![Images](images/t0420-01.jpg)

II. ![Images](images/t0420-02.jpg)

III. Logically I, II, and III should all work. However, `IF(score ≥ 80 AND ≤ 89)` is incorrect syntax and therefore results in an error. Correct syntax would be `IF(score ≥ 80 AND score ≤ 89)`.

### 4

**(C)**

![Images](images/t0420-03.jpg)

Determine the minimum number of bits to hold the number 254:

![Images](images/e0420-01.jpg)

It takes 8 bits to hold the number 255.

Three colors would require 8 bits × 3 = 24 bits.

### 5

**(A)** The internet uses fiber-optic cables that transmit data as “on” or “off,” which is represented in binary as 0 or 1.

(B) Due to the fault-tolerant nature of the internet, packets travel in different directions through the internet. Since packets travel in different directions, they arrive at their destination in a different order than that in which they were sent.

(C) There is no central governing body that controls the design of the internet.

(D) The Digital Millennium Copyright Act does not relate to the internet naming convention.

### 6

**(D)**

| count | LENGTH[nums] − count | DISPLAY |
| :--- | :--- | :--- |
| 1 | 4 | 10 |
| 2 | 3 | 7 |
| 3 | 2 | 4 |
| 4 | 1 | 1 |
| 5 | 0 | error |

The procedure is trying to access index 0. The language used on this AP exam starts on index 1. So 0 is out of bounds and will result in an error.

### 7

**(D)** There are ten numbers between 5 and 14 inclusive: 5, 6, 7, 8, 9, 10, 11, 12, 13, 14. For the condition to evaluate to true 60% of the time, six of the ten numbers must be included: 5, 6, 7, 8, 9, 10. Since `x ≤ 10` would include six numbers, it would result in being true 60% of the time.

(A) `x < 6` would include only one number and would result in being true 10% of the time.

(B) `x ≥ 6` would include nine numbers and would result in being true 90% of the time.

(C) `x > 10` would include four numbers and would result in being true 40% of the time.

### 8

**(B)** The program states that `num` can be 1, 2, 3, 4, 5, 6, 7, 8, 9, or 10. Of those numbers, 1, 2, 3, and 4 are less than 5. Of those, only 2 and 4 are also even. Two out of ten numbers equals 20%.

(A) Ten percent (10%) would be one out of ten numbers.

(C) Forty percent (40%) would be four out of ten numbers.

(D) Fifty percent (50%) would be five out of ten numbers.

### 9

**(C)** A list can directly access elements by index. In this AP exam, indexes start at 1. Accessing index 2 will result in displaying the number 3. In this example, `list[1]` would access 11, `list[2]` is 3, `list[3]` is 5, and `list[4]` is 6.

### 10

**(B)**

Step 1: Start the program.

Step 2: Set `num = 4`.

Step 3: Is `4 > 2` evaluates to true.

Step 4: Display 4.

Step 5: Is `4 > 7` evaluates to false.

Step 6: Set `num = 5`.

Step 7: Is `5 > 7` evaluates to false.

Step 8: Set `num = 6`.

Step 9: Is `6 > 7` evaluates to false.

Step 10: Set `num = 7`.

Step 11: Is `7 > 7` evaluates to false.

Step 12: Set `num = 8`.

Step 13: Is `8 > 7` evaluates to true.

Step 14: Display 8.

Step 15: End the program.

### 11

**(B)** The “speedup” of a parallel solution is measured in the time it took to complete the task sequentially divided by the time it took to complete the task when done in parallel.

`Speedup = sequential run time / parallel run time`

`Speedup = 4,000 / 400 = 10`

### 12

**(B)** It is extremely difficult to determine the credibility of a source. The author, publisher, and sponsorship reputations are all factors. However at the time of writing this book, all of these can be easily faked. So although the correct answer is (B), it is still a gray area.

### 13

**(A)** When solving a swap, for organization substitute sample numbers for the variables.

In this case, the author picked the numbers 5 and 13. However, the numbers could have been of any value.

| a | b |
| :--- | :--- |
| 5 | 13 |

If the swap is successful, the values will be swapped.

| a | b |
| :--- | :--- |
| 13 | 5 |

**(A) Correct.** Taking sample values of `a = 5` and `b = 13` results in:

| temp | a | b |
| :--- | :--- | :--- |
| 5 | 5 | 13 |
| | 13 | 5 |

**(B)** Taking sample values of `a = 5` and `b = 13` results in:

| temp | a | b |
| :--- | :--- | :--- |
| | 5 | 5 |
| | 5 | 0 |

**(C)** Taking sample values of `a = 5` and `b = 13` results in:

| temp | a | b |
| :--- | :--- | :--- |
| 5 | 5 | 13 |
| | 5 | 5 |

**(D)** Taking sample values of `a = 5` and `b = 13` results in:

| temp | a | b |
| :--- | :--- | :--- |
| | 5 | 13 |
| 0 | 0 | 0 |
