6) In Windows Explorer, navigate to C:\php-[version_number]-Win32\ and verify that there is a folder inside called temp.
If that folder doesn't exist, create one.

![](bbox=[0.05, 0.145, 0.73, 0.505])

# RESTRICTING ACCESS TO PAGES

By now, you should have tested your registration and log-in pages, and they should work as expected. The only thing is, until you implement page restriction features to the pages you want to block access to, your registration and log-in framework is not very useful. In this task, you will add the server behaviors that prevent users from accessing pages, unless they've first logged in.

+   1) Open profiles.asp.
+   This is one of the pages that users must log in to see.

+   2) Click anywhere on the page, and insert a Restrict Access to Page server behavior, found in the User Authentication submenu of the Server Behaviors menu. In the Restrict Based On group, choose Username, Password, and Access Level.

This dialog not only lets you restrict access to the page; it also lets you restrict access to a page based on a user's access level.