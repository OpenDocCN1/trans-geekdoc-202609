# Exercise 9-2     Write code that works with numbers

In this exercise, you can write some PHP code that works with numbers.

# Open and test the application

+   1. Start the Chrome browser and run the application in the ex_starts/ch09_ex2 directory. This should display a page that allows you to enter three numbers and provides starting values for the three numbers.

+   2. Click on the Submit button. Note that this displays a message that includes the values of the three numbers but doesn’t include the values for the rest of the message.

# Write the code that processes the data entered by the user

+   3. Open the index.php file for this application and review the code. Note that it doesn’t process the data. Instead, it just displays the data on the form.

+   4. Open the number_tester.php file for this application and review the code. Note that the PHP code that displays the $message variable uses the nl2br function to convert new line characters to <br> tags.

+   5. Add the code that uses the data that’s entered into the text box controls to display a message that’s formatted like this:

```
Number 1: 78
Number 2: -105.33
Number 3: 0.0049

Number 2 ceiling: -105
Number 2 floor: -106
Number 3 rounded: 0.005

Min: -105.33
Max: 78

Random: 86
```

When formatting this message, use escape sequences to insert new line characters.

+   6. Make sure the user enters all three numbers and that these numbers are valid.

+   7. Make sure the rounded number is rounded to 3 decimal places.

+   8. Make sure the random number is a number between 1 and 100.

+   9. Test the application to make sure it works correctly with the default values and also with other values.