# Core PHP Programming

left side to the right side. If Today contains the word Friday, the block of code surrounded by curly braces { and } is executed. In all other cases the block of code associated with the else statement is executed.

# Repeating Code

The last type of functionality in this brief introduction is looping. Looping allows you to repeat the execution of code. Listing 1.7 is an example of a for loop. The for statement expects three parameters separated by semicolons. The first parameter is executed once before the loop begins. It initializes a variable. The second parameter makes a test. This is usually a test against the variable named in the first parameter. The third parameter is executed every time the end of the loop is reached.

The for loop in Listing 1.7 will execute three times. The initialization code sets the variable count to be one. Then the testing code compares the value of count to three. Since one is less than or equal to three, the code inside the loop executes. Notice that the script prints the value of count. When you run this script you will find that count will progress from one to three. The reason is that the third part of the for statement is adding one to count each time through the loop. The ++ operator increments the variable immediately to its left.

The first time through the loop count is one, not two. This is because increment count does not occur until we reach the closing curly brace. After the third time through the loop, count will be incremented to four, but at that point four will not be less or equal to three, so the loop will end. Execution continues at the command following the loop code block.

# Listing 1.7 Today's Daily Affirmation