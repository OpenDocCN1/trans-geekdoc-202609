# # Propagating Sessions

There are two ways to propagate sessions:

+   - Through URLs
+   - Through cookies

# # URLs

When writing sessions, keep in mind the security issues involved.

For instance, a user at a public terminal may look over the shoulder of another and grab the session string; thus taking over the other user's session and possibly compromising information such as credit card numbers, addresses, phone numbers, or other sensitive subjects. Additionally, propagating a SID in the URL that is impossible to copy without the user being away for a long time, makes the URL look quite ugly and can cause confusion among computer-illiterate users.

Thus, it is not always in our best interests to propagate sessions through the URL. Now, all browsers have some method of cookie support and accept or at least prompt for cookies.

When considering those browsers that are generally not HTML 4.0 or JavaScript compatible, usually, explaining to the users that cookies are a necessity for their site, and that their security is a top concern, will get cookies turned on.

# # Security Issues

If we are unable to use cookies with our site and must propagate sessions through the URL, there are a few ways to add security to the site, thus preventing session takeovers.

For instance, the following code snippet will register the user's IP address if they've just logged in. If a different IP is detected, the session will disallow the new IP:

```
if (!session_is_registered("$ipAddr")) {
    $ipAddr = $REMOTE_ADDR;
    session_register("ipAddr");
}

if ($ipAddr != $REMOTE_ADDR) {
    echo("Hijacked Session!");
}
```

Unfortunately, computers behind a firewall and computers running behind a proxy server do not have unique IP addresses, and all would appear with the same address as the computer that is actually connected to the outside.

There is no easy way around this. Some proxy servers send an HTTP header called X_FORWARDED_FOR, which will contain the end-user address. The following snippet will get the right address for any user and computer behind a proxy: