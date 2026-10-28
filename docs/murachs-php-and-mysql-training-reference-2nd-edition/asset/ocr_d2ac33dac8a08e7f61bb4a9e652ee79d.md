+   4. Use your editor to open the `database.php` file and the `products.php` file in the model directory. Then, review the code. Note how the PDO exceptions are handled.

+   5. Modify the first `SELECT` statement in the `products.php` file so it refers to the “product” table instead of the “products” table. Then, test the error handling by running the application. It should display the error message to the user.

+   6. Fix the `SELECT` statement, so the application works correctly again.

# ## Add a Category Manager section

Now, you’ll add a page to the Product Manager application that lets you add or delete categories. This is similar to what exercise 4-1 and exercise 5-1 asked you to do. So if you did those exercises, you may be able to reuse some of your code in this exercise.

![](bbox=[0.137, 0.331, 0.872, 0.67])

+   7. Open the `admin/product/product_list.php` file for this application. Then, add a “List Categories” link to the bottom of the Product List page.

+   8. Create a Category List page in the `admin/product` directory named `category_list` that displays the category data in a table as shown above. Here, the first column displays the names of all categories, and the second column displays a Delete button that allows the user to delete the category. If you give this table an id of “category_table”, the `main.css` file for this exercise should format it as shown above.

+   9. After the table, add a form that lets the user add a category. Use a text box for the name of the category and a submit button to add the category to the database. If you give this form an id of “add_category_form”, the `main.css` file for this exercise should format it as shown above.