
The function of my program is to prompt the user to pick a number from 1 to 6. The program will fill the list called `diceRolls` with 60 random numbers from 1 to 6. If the user's number occurs more than 10 percent in the list, the program will return "Winner." If not, it will return "Loser."

### 35. Identify the input/output of the program.

The user provides an input, which is a number. If the input is found in the list more than 10 percent, the output is the word "Winner." If not, the output is the word "Loser."

### Algorithm Development

### 36. Identify the number of times the body of your iteration statement will execute.

The loop in my program will run for 60 iterations.

### 37. Describe a condition or error that would cause your iteration statement to not terminate and cause an infinite loop. If no such condition or error exists, explain how the loop could be modified to cause an infinite loop.

The loop utilized in my program is a "for-each" loop, which inherently prevents infinite loops. A "for-each" loop automatically initiates at the first index and concludes at the final index, ensuring that it cannot result in an infinite loop. However, if I change the loop from `FOR EACH item IN diceRolls` to `REPEAT UNTIL pick = diceRolls[count]` where `pick` is not contained in the words list, an infinite loop would occur.

### 38. Describe two calls to the procedure in the supplied program. Each call must pass a different argument(s) that causes a different segment of code in the algorithm to execute, and describe what conditions are being tested and the result of each call.

Assume that `diceRolls` contains the numbers (1, 1, 3, 5, 6, 4), and `pick` contains the number 1. The first call would be . . . .

![Images](images/f068-01.jpg)

Assume that `diceRolls` contains the numbers (1, 1, 3, 5, 6, 4), and `pick` contains the number 5. The second call would be . . . .

![Images](images/f068-02.jpg)

The first call would test to see if "1" is contained in the `diceRolls` list more than 10 percent.

The second call would test to see if "5" is contained in the `diceRolls` list more than 10 percent.

The results of the first call are "Winner" will be displayed.

The results of the second call are "Loser" will be displayed.

### 39. Describe what the data contained in the list represents in your program.

My list holds 60 random numbers from 1 to 6, which represent 60 dice rolls.

### Errors and Testing

### 40. Outline a modification that would result in a runtime error.

Entering a letter instead of a number would trigger a runtime error because the program wouldn't be able to compare a letter for equality with a number.

### 41. Outline a modification that would result in a logical error.

Altering the condition from `IF total > 10` to `IF total > 50` would lead to the program returning "Winner" only if the `pick` occurred in the list more than 50 percent of the time, rather than the initial 10 percent. This change would introduce a logical error in the program's behavior.

### 42. Outline a modification that would result in a syntax error.

Setting the initial value of `total` as `total = 1` rather than `total ← 1` in the code would result in a syntax error.

### 43. Outline a modification that would result in an overflow error.

If the data type of `total` were an 8-bit integer, the maximum value it could hold without triggering an overflow error would be 2^n − 1, which, in this specific case, is 256 − 1, equal to 255. Consequently, attempting to store the number 278 in `total` would result in an overflow error.

### 44. Describe the procedure used to test for correctness of your algorithm.

When testing with the scenario where `diceRolls` contained fifteen 1's and `pick` is equal to 1, the expected outcome is "Winner," and indeed, it was.

In another test case, when testing with the scenario where `diceRolls` contained seven 1's and `pick` is equal to 1, the expected outcome is "Loser," and indeed, it was.

### Data and Procedural Abstraction

### 45. Elaborate on the role of the list within your program. Explain how the program's structure would differ if it did not use a list, and discuss how employing the list has simplified the program's complexity.

In my program, I employed a list named "diceRolls," which comprises 60 numbers representing 60 random dice rolls from one to six. These numbers are stored in the list with indices ranging from 1 to 60. Utilizing this list allowed me to minimize the number of variables I needed to create, as I only had to name one variable, `diceRolls`, instead of having to define 60 individual variables for each planet. This reduction in code complexity, achieved by using a single variable to represent the list, significantly lowered the likelihood of errors in my program.

Moreover, through the utilization of my `diceRolls` list, I could efficiently examine and verify if the user's input matched 10 percent of the numbers contained in the list by employing a `for` loop in conjunction with just one `if` statement. Without employing a list, testing for equality among all 60 rolls would necessitate the creation of 60 distinct `if` statements. This simplification of code complexity, facilitated by the use of a singular variable representing the list, considerably diminished the probability of errors in my program.

### 46. Elaborate on the role of procedural abstraction within your program. Explain how the program's structure would differ if it did not use a procedural abstraction, and discuss how employing the procedural abstraction has simplified the program's complexity.

By encapsulating the algorithm responsible for checking the presence of a word in a list within a procedure, I have significantly streamlined the complexity of my program. This simplification allows me to reuse the algorithm at multiple points in my program without the need for redundant code. For example, when I need to verify the presence of five words in my list, I can simply call the procedure five times. Without this procedural approach, I would be compelled to write 20 lines of code, as opposed to just five.

Furthermore, the utilization of procedures ensures that any errors associated with word presence checks are confined within the procedure itself. In the absence of procedures, identifying the source of errors related to this functionality would require a comprehensive examination of the entire program.

### 47. Suppose you are provided with a procedure called `isEqual(value1, value2)`. The procedure returns true if the two parameters, `value1` and `value2`, are equal in value and returns false otherwise. Using the list you identified in the List section of your Personalized Project Reference, explain in detailed steps an algorithm that uses `isEqual` to count the number of times a certain value appears in your list. Your explanation must be detailed enough for someone else to write the program code.

1. Set the initial value of `total` to 0.
2. Set the initial value of `count` to 1.
3. Begin iterating through the `diceRolls` list.
4. For each item in the list, check if `value2` is equal to `item`, where `item` varies from 1 to 6, and if a match is found, increase `total` by one.
5. Once all items in the list have been iterated through, return the cumulative `total` value.

![Images](images/f071-01.jpg)

### Answer questions 48–62 based on the following procedure.

**Note:** Like the AP exam, the list used in the below code segment will start at index 1.

The purpose of the provided procedure is to compute the charging costs, which are determined by the hour(s) during which the charging takes place. The "rates" table contains a list of 24 one-hour periods, numbered from 1 to 24, along with the associated hourly cost for each period. This procedure is designed to calculate the cumulative charging cost based on the specified starting time and the duration in hours.

![Images](images/f072-01.jpg)

### Program Design, Function, and Purpose
