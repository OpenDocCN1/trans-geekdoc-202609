![](bbox=[0.112, 0.091, 0.804, 0.451])

Figure 19-6: Drop-down list in the Customer Contact Report t

Now, with two stories under your belt, you can take a decadent 10-minute break before heading off to get Wendy, Wade, Edwina, and Harold using the application. You'll need the rest.

# Re-estimating

The good news is that Wendy, Wade, Harold, and Edwina love the application; but they are only human, and they have brought up some quite reasonable requests:

+   - Include a Logout button.
+   - Don't allow access to `customer-contacts.php` without first logging in.
+   - Changing the week should bring up a previously saved week.
+   - In the Customer Contact screen, also track the following: number of shop calls, number of engineer calls, number of distributor calls, approximate mileage, territory worked, and territory comments on a *per week* basis.
+   - The number of contacts may occasionally change. Can that be configurable?

Doing some quick estimates, you figure the new tasks as follows:

+   - Include a Logout button: 1/2 point
+   - Don't allow access to `customer-contacts.php` without first logging in: (bug) 1/2 point