+   8. Switch to the display_discount.php file and add statements that format the numeric variables with the currency and percentage formats. Then, modify the last four echo statements so they display the formatted data, save the file, and run the application. Now, the application should display the formatted data.

+   9. Keep the application running and navigate to the index.html page if you’re not already there. In the Product Description textbox, enter `<b>Guitar</b>`, and in the Discount Percent textbox, enter `<i>10</i>`. Click the Calculate Discount button, and notice that the Product Description value is displayed in bold, and the Standard Discount value is displayed in italics.

+   10. Switch to the display_discount.php file and add the htmlspecialchars function to the echo statements for Product Description, List Price, and Standard Discount. Then save the file, run the application, and repeat step 9. Notice that this time, the HTML tags are displayed as HTML entities, rather than being implemented by the browser.

+   11. Switch to the display_discount.php file and fix the heading for the display_discount.php file so it says “Product Discount Calculator”. Then, test this change, and close the files.

# Exercise 2-2    Enhance the Future Value application

In this exercise, you’ll enhance the Future Value application by applying some of the skills that you’ve just learned.

# Test the Future Value application

+   1. Make sure the Apache server is running. Then, start your browser and run the application in this directory:
+   
+   ```text
+   xampp\htdocs\ex_starts\ch02_ex2
+   ```
+   
+   To do that, you can use the index of exercise starts that you bookmarked in exercise 1-2 or you can use this URL:
+   
+   ```text
+   http://localhost/ex_starts/ch02_ex2/
+   ```

+   2. Enter valid numbers in all three text boxes. For the first test run, keep these values simple like 100 for investment amount, 5 for yearly interest rate, and 10 for number of years. Then, click the Calculate button to display the results.

+   3. Click the Back button to return to the first page, enter invalid values in the first two text boxes, and click the Calculate button. Then, respond to the error message that’s displayed by entering valid data for the investment amount, re-entering invalid data for interest rate, and clicking the Calculate button. This time, you need to respond to the error message for the invalid interest rate entry.