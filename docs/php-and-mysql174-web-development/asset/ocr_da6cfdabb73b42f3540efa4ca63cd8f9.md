As you can see, the only logic in the do_html_header() function is to start the HTML document and add the appropriate title and heading to the page. The other functions used in login.php are similar. The function display_site_info() adds some general text about the site, display_login_form() displays the gray form shown in Listing 27.3, and do_html_footer() adds a standard HTML footer to the page.

The advantages of isolating or removing HTML from your main logic stream are discussed in Chapter 25, "Using PHP and MySQL for Large Projects." We use the function API approach here.

Looking at Figure 27.3, you can have three options: A user can register, login if he or she has already registered, or reset the user's password if he or she has forgotten it. To implement these modules, we move on to the next section, user authentication.

# Implementing User Authentication

There are four main elements to the user authentication module: registering users, logging in and logging out, changing passwords, and resetting passwords. In the following sections, we look at each of these elements in turn.

# Registering Users

To register a user, you need to get the user's details via a form and enter the user in the database.

When a user clicks on the Not member? link on the login.php page, the user is taken to a registration form produced by register_form.php. This script is shown in Listing 27.5.

Listing 27.5 register_form.php—This Form Gives the Opportunity to Register with PHPBookmark

```
<?php
require_once('bookmark_fns.php');
do_html_header('User Registration');
display_registration_form();
do_html_footer();
```

Again, you can see that this page is fairly simple and just calls functions from the output library in output_fns.php. The output of this script is shown in Listing 27.4.

The gray form on this page is output by the function display_registration_form(), contained in output_fns.php. When the user clicks on the Register button, the user is taken to the script register_new.php, shown in Listing 27.6.