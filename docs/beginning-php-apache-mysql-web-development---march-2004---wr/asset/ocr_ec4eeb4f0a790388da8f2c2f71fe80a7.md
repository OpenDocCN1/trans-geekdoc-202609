# Chapter 11

![](bbox=[0.068, 0.091, 0.831, 0.545])

Figure 11-2

# How It Works

When you request the page, Apache checks for .htaccess files in every folder from the Web site’s document root all the way down to the file that you are requesting. Apache then opens the file and interprets it. It does this by reading which directory to protect, according to your file path, and then by reading to whom to allow access. We give access to users only, as in the example of john, so no anonymous users will be allowed access. Anonymous users will see the screen previously in Figure 11-3.

Because no usernames or passwords are submitted with your initial request, Apache sends a message back to the browser, requesting you to enter a username and password to access this section of the site. Therefore, a dialog box is displayed, and you can submit the username and password by entering them there. Once these are accepted, you will be allowed to view the site. Also, your Web browser will remember to automatically submit this username and password when accessing the particular folder and throughout the directory tree for the rest of the browser session.