These four pages are fairly simple. In each case, `common.inc.php` is included to load all the common code and class files. Then, the `checkLogin()` function in `common.inc.php` is called to verify that the user trying to view the page is in fact logged in as a member. Remember that, if the user isn't logged in, `checkLogin()` redirects to the login page and exits the application.

After calling `checkLogin()`, each script displays the XHTML page header by calling `displayPageHeader()`, then outputs the page content, and finally outputs the page footer with `displayPageFooter()`.

Notice that `index.php` also retrieves the logged-in member’s first name with `$_SESSION["member"]->getValue( "firstName" )` and displays it. The logged-in member is stored in the PHP session, so the member’s details are accessible from any script in the application. `index.php` also includes a Logout menu option that simply links to the `logout.php` script you created earlier.

# Testing the Members' Area

To try out your new password-protected members’ area, try visiting the `book_club/members/index.php` page in your Web browser. If you’re not logged in, you’ll be redirected to the login form (Figure 14-2). Enter a username (for example, “sparky”) and password (such as “mypass”) for a member stored in your `members` table, and click the Login button. If you entered the correct details, you should see the thank-you page appear, with a link to take you to the members’ area. Click the link to view the members’ area homepage, `index.php`, as shown in Figure 14-3.

![](bbox=[0.16, 0.52, 0.76, 0.76])

Figure 14-2