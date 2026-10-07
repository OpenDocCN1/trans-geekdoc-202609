# Cookies or sessions?

Cookies are the optimal method for maintaining data with PHP, and it is extremely simple to store the data with the set_cookie() function. Cookies are perhaps easier to use sessions.

Unfortunately, cookies require the co-operation of the user's browser in allowing cookies to be stored on the client system. As concerns about privacy and security become heightened with increasing fear of computer viruses, more users than ever are becoming reluctant to allow cookies on their systems. This prevents you from using cookies to store data for PHP routines.

Some of the newly emerging mobile devices that can access the Internet may not even have the capacity to store cookies.

On the other hand, storing data in session variables does not rely upon the user's browser settings, so is far more reliable than using cookies. You just have to remember to append the SID session identifier onto each URL in hyperlinks, and to call the session_start() function at the beginning of each page.

Changing the PHP configuration can even remove the need to call session_start() manually on each page. In the session block of the phpinfo.php page is a directive "session.auto_start" that by default is set to off on installation.

Open the php.ini file in a text editor and find the entry for session.auto_start. Change its value from 0 to 1 to turn this feature on. Now PHP will automatically perform the tasks of the session_start() function whenever a page gets loaded.

With session.auto_start set to on, each of the three calls to the session_start() function in the last example can be removed – and the preference data is still maintained as the user navigates between the pages.

Overall it may be better to use sessions rather than cookies, especially to store critical data, such as the selected shopping cart items on an e-commerce website.

Sessions ensure that stored data will be available across the entire website, even in those browsers where cookies are not enabled, but this will use more resources to store the data.

![](bbox=[0.045, 0.596, 0.235, 0.696])