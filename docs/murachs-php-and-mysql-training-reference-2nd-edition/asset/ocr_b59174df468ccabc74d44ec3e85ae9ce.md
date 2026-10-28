# # The Product Discount application

Now that you know the basic skills for coding PHP applications, it’s worth taking the time to give the Product Discount application of chapter 1 another look. As you will see, it only requires the skills you’ve learned so far.

# ## The user interface

Figure 2-12 presents the user interface for the Product Discount application. The first page is a static web page that’s stored in the index.html file. The second page is a dynamic web page that’s stored in the display_discount.php file.

# ## The form in the HTML file

Figure 2-12 presents the code for the HTML file that relates to the PHP for this application. Here, you can see the HTML for a form and three text boxes. When the user clicks on the Calculate Discount button, the form is submitted to the server via the POST method and the file named display_discount.php is requested. The data in the three text boxes is also sent along with the HTTP request.