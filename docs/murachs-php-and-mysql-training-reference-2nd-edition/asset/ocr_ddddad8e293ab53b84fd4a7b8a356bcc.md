# Exercise 12-1 Modify the Shopping Cart application

In this exercise, you can modify and enhance the Shopping Cart application.

# Open and test the application

+   1. Run the application that’s stored in the ex_starts/ch12_ex1 directory.
+   2. Test this application by adding several items to the cart. Then, exit the browser, restart it, and view the cart. Since this application uses a persistent session cookie, this should display any items that were previously in the cart.
+   3. Open the index.php file for this application and review the code. Note that this code configures the cookie for the session so it persists for 2 weeks.

# Use a session cookie

+   4. Modify the code that configures the cookie for the session so the session uses a session cookie.
+   5. Test this change to make sure it works correctly. You should be able to remove all items from your cart by exiting the browser. (When you exit the browser, don’t save any open tabs. Otherwise, your browser may remember the cookie for the session and the items won’t be removed from the cart.)

# Use a persistent cookie that lasts for 3 years

+   6. Modify the code that configures the cookie for the session so the session persists for 3 years.
+   7. Add code that displays the session ID on both pages of the application.
+   8. Test these changes. The session ID should remain the same even if you exit and restart the browser.
+   9. Add a link to the Cart page that says “End Session and Delete Cookie”. Then, add code that processes this link by clearing all session data from memory, cleaning up the session ID, and deleting the cookie for the session.
+   10. Test this change. When you click the “Empty Cart” link, the items should be removed from the cart, but the session ID should stay the same. When you click the “End Session” link, the items should be removed from the cart, and the session ID should be cleared. Then, if you add an item to the cart, the Cart page should display a new session ID.