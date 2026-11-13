The moral of the story is that you should follow the procedure in "#25: Fetching Form Variables Consistently and Safely" on page 47 to access form data. It doesn't sound like it would happen often, but exploits for register_globals are second only to XSS attacks in PHP. Furthermore, global variables can lead to much subtler issues that *will* cause bugs later on in your code.

# Recommended Security Configuration Options

There are several PHP configuration settings that affect security features. Here are the ones that I use for production servers (see Chapter 2 for how to set them):

+   * register_globals set to off. See the previous discussion.
+   * safe_mode set to off. This parameter doesn't really make anything safe.
+   * error_reporting set to off: This is visible error reporting that sends a message to the user's browser if something goes wrong. For production servers, use error logging instead (see "#11: Suppressing All Error Messages" on page 24). Development servers can enable error logging as long as they're behind a firewall.
+   * Disable these functions: system(), exec(), passthru(), shell_exec(), proc_open(), and popen(). See "#17: Shutting Down Specific Functions" on page 27.
+   * open_basedir set for both the /tmp directory (so that session information can be stored) and the web root so that scripts cannot access files outside a selected area.
+   * expose_php set to off. This feature adds a PHP signature that includes the version number to the Apache headers. Why would you want to do that?
+   * allow_url_fopen set to off. This isn't strictly necessary if you're careful about how you access files in your code—that is, you validate all input parameters.
+   * allow_url_include set to off There's really no sane reason for anyone to want to access include files via HTTP.

In general, if you find code that wants to use these features, you shouldn't trust it. Be especially careful of anything that wants to use a function such as system()—it's almost certainly flawed.

With these settings now behind us, let's look at some specific attacks and the methods that will help you protect your server.

# #19: SQL Injection Attacks

Because the queries that PHP passes to MySQL databases are written in the powerful SQL programming language, you run the risk of someone attempting an _SQL injection attack_ by using MySQL in web query parameters. By inserting malicious SQL code fragments into form parameters, an attacker attempts to break into (or disable) your server.