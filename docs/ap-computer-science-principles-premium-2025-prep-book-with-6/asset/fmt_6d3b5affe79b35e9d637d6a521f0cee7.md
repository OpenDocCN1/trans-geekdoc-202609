
# My procedure takes in a 46-element list containing integers, as well as a string that indicates if the phrase will be encrypted or decrypted.

Each letter in the phrase matches with a corresponding key number.

- If the key number is even and encryption is selected, the letter is moved forward equal to the key number.
- If the key number is odd and encryption is selected, the letter is moved forward equal to the key number minus two.
- If the key number is even and decryption is selected, the letter is moved backward equal to the key number.
- If the key number is odd and decryption is selected, the letter is moved backward equal to the key number plus two.

The new word is then displayed on the screen.

## 7. Describe in detailed steps how the algorithm implemented in the identified procedure works.

Your explanation must be detailed enough for someone else to recreate it.

**Line 4:** The procedure `scrambleWord` takes in a phrase called “word” and a string called “enOrDe”.

**Line 5:** The empty list `tempList` is created.

**Lines 6–7:** A `for` loop is executed the same size as the length of `word` and appends each letter of the word as a character into the list `tempList`.

**Line 8:** An empty string called “result” is created.

**Line 9:** `x` is set to 0.

**Line 10:** A `for` loop is set up to iterate through the list `keyList`.

**Line 11:** If the value of `x` is less than the length of `word` and...

**Line 12:** If the current element of `keyList` is even and...

**Lines 13–14:** If `enOrDe` is set to encrypt, shift the character forward the `keyList` value and add it to `result`.

**Lines 15–16:** Else if `enOrDe` is set to decrypt, shift the character backwards the `keyList` value and add it to `result`.

**Line 17:** Else if the current element of `keyList` is odd and...

**Lines 18–19:** If `enOrDe` is set to encrypt, shift the character forward the `keyList` value − 2 and add it to `result`.

**Lines 20–21:** Else if `enOrDe` is set to decrypt, shift the character backwards the `keyList` value + 2 and add it to `result`.

**Line 22:** One is added to `x`.

**Line 23:** Go to line 11 until the `for` loop is complete.

**Line 24:** Displays the value of the translated word in `result`.

## 8. Describe two calls to the procedure identified in written response 3i.

Each call must pass a different argument(s) that causes a different segment of code in the algorithm to execute.

**First call:**
```
scrambleWord("Mississippi", "e")
```

**Second call:**
```
scrambleWord("Lmyzlxthvwk", "d")
```

**Describe what condition(s) is being tested by each call to the procedure.**

**Condition(s) tested by the first call:**
Encrypt the word “Mississippi” based on the stored key.

**Condition(s) tested by the second call:**
Decrypt the word “Lmyzlxthvwk” based on the stored key.

**Identify the result of each call.**

**Result of the first call:**
`Lmyzlxthvwk`

**Result of the second call:**
`Mississippi`

## 9. Identify the number of times the body of your iteration statement will execute.

The loop in my program will run for the length of the string, which in this case was 11 iterations.

## 10. Describe a condition or error that would cause your iteration statement to not terminate and cause an infinite loop.

If no such condition or error exists, explain how the loop could be modified to cause an infinite loop.

The loop used in my program is a “for-each” loop, which automatically commences at the first index and naturally terminates at the last index, guaranteeing the prevention of an infinite loop. However, if I were to switch to a “while” loop and configure it to continue until `len(word) == 0`, it would result in an infinite loop. This is because the total length of the “word” would never reach 0, inevitably leading to an infinite loop.

## 11. Outline a modification that would result in a runtime error.

Attempting to perform a division by zero would result in a runtime error. Modifying line 12 to `if (item / 0 == 0)` would also lead to a runtime error.

Moreover, using a variable or procedure that has not been defined would likewise trigger a runtime error. Consequently, changing line 28 from `scrambleWord(word, enOrDe)` to `mixUpWord(word, enOrDe)` would also result in a runtime error.

## 12. Outline a modification that would result in a logical error.

Altering the code on line 14 from `+ item` to `-item` would cause incorrect results and produce a logical error.

## 13. Outline a modification that would result in a syntax error.

Removing the indentation from line 11 would result in a syntax error. Additionally, leaving out the `:` at the end of the `for` statement in line 10 would lead to a syntax error.

## 14. Outline a modification that would result in an overflow error.

Experiencing an overflow error in Python can be quite challenging due to its dynamic typing, as values are not constrained to a fixed number of bits. However, if the data type of `x` were an 8-bit integer, the maximum value it could hold without triggering an overflow error would be 2^n – 1, which, in this specific instance, amounts to 255 (derived from 256 – 1). Consequently, any endeavor to store the number 278 in `x` would unquestionably result in an overflow error.

## 15. Elaborate on the role of procedural abstraction within your program.

Explain how the program’s structure would differ if it did not use a procedural abstraction, and discuss how employing the procedural abstraction has simplified the program’s complexity.

By encapsulating the algorithm within a procedure, I have significantly reduced the complexity of my program. This simplification allows me to reuse the algorithm at multiple points in my program without the need for redundant code. For example, when I need to scramble each letter in a word, I can simply call the procedure the length of the word times, which in this case was 11 times. Without this procedural approach, I would have to replicate the entire code 11 times instead of just once.

Furthermore, the use of procedures ensures that errors associated with the `scrambleWord` functionality are localized within the procedure itself. Without procedures, I would need to inspect the entire program to pinpoint the source of any errors related to this functionality.

## 16. Suppose you are provided with a procedure called `isEqual(value1, value2)`.

The procedure returns `true` if the two parameters, `value1` and `value2`, are equal in value and returns `false` otherwise. Using the list you identified in the List section of your Personalized Project Reference, explain in detailed steps an algorithm that uses `isEqual` to count the number of times a certain value appears in your list. Your explanation must be detailed enough for someone else to write the program code.

1. **Initialization**: Start by initializing the variable `total` with a value of 0.
2. **Iterate Through the List**: Commence the process of iterating through the `keyList` list.
3. **Counting Matches**: For each item in the list, assess if the `user` is compared to a number contained in the list. If a match is found, increase the `total` by one.
4. **Completion**: Once all items in the list have been iterated through, return the accumulated value of `total`.

---

# Full Create Performance Task—Sample Five

## Graphical-Based Language

This program can be used to calculate averages on tests. The program can calculate the average or can calculate the average with the lowest test score dropped.

### Part 1: Program Code

![Images](images/f104-01.jpg)

![Images](images/f104-02.jpg)

![Images](images/f105-01.jpg)

![Images](images/f105-02.jpg)

### Part 2: Program Video

Not shown

### Part 3: Code Segments for Your Personalized Project Reference

#### 3i. The first program code segment must be a student-developed procedure that:

- Defines the procedure’s name and return type (if necessary).
- Contains and uses one or more parameters that have an effect on the functionality of the procedure.
- Implements an algorithm that includes sequencing, selection, and iteration.

![Images](images/f106-01.jpg)
