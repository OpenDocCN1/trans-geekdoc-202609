
# 16. Algorithm Using `isEqual` Procedure

Suppose you are provided with a procedure called `isEqual(value1, value2)`. The procedure returns `true` if the two parameters, `value1` and `value2`, are equal in value and returns `false` otherwise. Using the list you identified in the List section of your Personalized Project Reference, explain in detailed steps an algorithm that uses `isEqual` to count the number of times a certain value appears in your list. Your explanation must be detailed enough for someone else to write the program code.

1. **Initialization**: Start by initializing the variable `total` with a value of 0.
2. **Iterate Through the List**: Commence the process of iterating through the `diceRollList` list.
3. **Counting Matches**: For each item in the list, assess if the `user` is equal to `luckyNumber` using `isEqual(item, luckyNumber)`. If a match is found, increase the `total` by one.
4. **Completion**: Once all items in the list have been iterated through, return the accumulated value of `total`.

![Images](images/f090-01.jpg)

# Full Create Performance Task—Sample Three

## Part 1: Program Code

![Images](images/f091-01.jpg)

## Part 2: Program Video

Not shown

## Part 3: Code Segments for Your Personalized Project Reference

### 3i. Procedure Definition
The first program code segment must be a student-developed procedure that:
- Defines the procedure's name and return type (if necessary).
- Contains and uses one or more parameters that have an effect on the functionality of the procedure.
- Implements an algorithm that includes sequencing, selection, and iteration.

![Images](images/f092-01.jpg)

### 3ii. Procedure Call
The second program code segment must show where your student-developed procedure is being called in your program.

![Images](images/f092-02.jpg)

## List: Capture and paste two program code segments you developed during the administration of this task that contain a list (or other collection type) being used to manage complexity in your program.

### 3i. Data Storage
The first program code segment must show how data have been stored in the list.

![Images](images/f092-03.jpg)

### 3ii. Data Usage
The second program code segment must show the data in the same list being used, such as creating new data from the existing data or accessing multiple elements in the list, as part of fulfilling the program's purpose.

![Images](images/f092-04.jpg)

### Possible Test Day Questions

#### 1. Describe the overall purpose of the program.
The purpose of my program is to entertain the user while teaching them statistics.

#### 2. Describe what functionality of the program is demonstrated in the video.
The program asks the user how many numbers they want to play with. The user then guesses a number. If that number is contained in the list, the number is removed from the list, and the user scores 10 points. If the user guesses a number that is not contained in the list, the game is over, and the total points won is displayed. The game continues until the user guesses a number not contained in the list.

#### 3. Describe the input and output of the program demonstrated in the video.
1. The user is prompted to enter how many numbers they want to play with. The user inputs 16.
2. The user is prompted to pick a number. The user inputs 3. The program outputs to the screen 2.
3. The user is prompted to pick a number. The user inputs 6. The program outputs to the screen 3.
4. The user is prompted to pick a number. The user inputs 6. The program outputs to the screen the following:
   - -1
   - Game Over.
   - Your score is 20

#### 4. Describe what the data contained in the list represent in your program.
The data in my list are random integers from 0 to 10 that represent the numbers used for the guessing game.

#### 5. Explain how the selected list manages complexity in your program code by explaining why your program code could not be written, or how it would be written differently, if you did not use the list.
By using my list `listOfNumbers`, I only had to name one variable—the list itself.

If I did not use my list, I would have to create and name all 16 integers contained in the list. My list called `listOfNumbers` reduced the level of complexity by reducing the amount of code I needed to write. By reducing the amount of code needed, it reduced the chances for errors.

Using my list called `listOfNumbers` allowed me to access the numbers in the list by index. If I did not use the list, I would have to access the numbers by their names. Combining the index with a `for` loop allowed me to test each element using one `if` statement. If I did not use a list, I would need to use 16 `if` statements. By reducing the amount of code needed, it reduced the chances for errors.

By using my list `listOfNumbers`, if I wanted to change the size of the list from 16 to 2000, no additional code would be required. If I did not use a list, I would have to name an additional 1984 variables. By reducing the required code, I reduced the chances for errors, thus reducing the level of complexity of my program.

#### 6. Describe, in general, what the identified procedure does and how it contributes to the overall functionality of the program.
My procedure takes in a list of random numbers and a number guessed by the user.

The procedure returns the number of times the number appears in the list. If the number is not found, `-1` is returned. All occurrences of the guessed number are cleared from the list after being counted.

#### 7. Describe in detailed steps how the algorithm implemented in the identified procedure works. Your explanation must be detailed enough for someone else to recreate it.
- **Line 9**: The procedure `playGame` takes in a list of numbers and a number guessed by the user.
- **Line 10**: The variable `total` is set to 0.
- **Lines 11–14**: The list `listOfNumbers` is iterated, and if the guessed number is in the list, it is removed, and one is added to `total`.
- **Lines 15–16**: If `total` is still equal to 0, `-1` is returned.
- **Lines 17–18**: In all other cases, the total number of times the guessed number was found in the list is returned.

#### 8. Describe two calls to the procedure identified in written response 3i. Each call must pass a different argument(s) that causes a different segment of code in the algorithm to execute.

**First call:**
Assume `listOfNumbers` contains `[1, 1, 3, 5, 6, 7]`, and the guess is 1.
The call would be `playGame(listOfNumbers, 1)`.

**Second call:**
Assume `listOfNumbers` contains `[1, 1, 3, 5, 6, 7]`, and the guess is 4.
The call would be `playGame(listOfNumbers, 4)`.

**Describe what condition(s) is being tested by each call to the procedure.**

**Condition(s) tested by the first call:**
Is 1 contained in the list? If yes, how many times?

**Condition(s) tested by the second call:**
Is 4 contained in the list? If yes, how many times?

**Identify the result of each call**

**Result of the first call:**
The number 2 is returned.

**Result of the second call:**
The number -1 is returned.

#### 9. Identify the number of times the body of your iteration statement will execute.
The loop in my program will run for an inputted value which, in this case, was 16 iterations.

#### 10. Describe a condition or error that would cause your iteration statement to not terminate and cause an infinite loop. If no such condition or error exists, explain how the loop could be modified to cause an infinite loop.
Replacing line 13 of the procedure with `listOfNumbers.append(item)` would trigger an infinite loop due to the continuous expansion of the list, preventing the `for-each` loop from ever concluding.

Additionally, the loop employed in my program is a `for-each` loop, which inherently initiates at the first index and naturally concludes at the last index, ensuring the avoidance of an infinite loop. However, if I were to switch to a `while` loop and set it to continue until `total` is equal to -1, it would result in an infinite loop. This is because the total length of the list can never be a negative number, inevitably leading to an infinite loop.

#### 11. Outline a modification that would result in a runtime error.
