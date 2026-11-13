# $_SERVER['HTTP_USER_AGENT']

Anyone who has built a Web page knows how important browser detection is. Some browsers will choke on fancy JavaScript, and others require very simple text. The user_agent string is your key to serving the right content to the right people. A typical user_agent string looks something like this:

Mozilla/4.0 (compatible; MSIE 5.01; Windows 98)

You can then parse this string to get what you are looking for.

You may be interested in PHP's get_browser() function. Theoretically, this function will determine the capabilities of your user's browser so you can find out if your script can safely serve out, for example, frames or JavaScript. The PHP manual has instructions for installation and use of get_browser(), but we do not recommend using it. Why? Using get_browser() you will be told that both Internet Explorer 5 for the PC and Netscape Navigator 4.01 for the Mac support CSS (Cascading Style Sheets) and JavaScript. But as anyone with client-side experience knows, writing DHTML that works on both of these browsers is a major task (and a major pain). The information you get from get_browser() can lead to a false sense of security. You're better off accessing $_SERVER['HTTP_USER_AGENT'] and making decisions based on the specific browser and platform.

# $_SERVER['REMOTE_ADDR']

The IP address of the user that sent the HTTP request. $_SERVER['REMOTE_ADDR'] is easily spoofed and doesn't necessarily provide information unique to a user. You might want to use it for tracking, but it should not be used to enforce security. On some servers – notably the default Apache installation shipped with Mac OS X – this is available as $_SERVER['HTTP_PC_REMOTE_ADDR'] instead.

# $_SERVER['REMOTE_HOST']

The host machine sending the request. This has a value only if your server is configured to do reverse DNS lookups, something that is commonly turned off for performance reasons. When I dial it up through my ISP (att.net), $_SERVER['REMOTE_HOST'] looks like this: 119.san-francisco-18-19rs.ca.dial-access.att.net.

# $_SERVER['SCRIPT_FILENAME']

Contains the filesystem's complete path to the file.

# Other Web server variables

As mentioned earlier, phpinfo() is your friend. We developed applications for this book on Unix systems running Apache Web servers. But, as PHP runs on a variety of operating systems and Web servers and MySQL runs on Windows as well as Unix, you should be aware of the different variables associated with whatever Web server and operating system you're running.