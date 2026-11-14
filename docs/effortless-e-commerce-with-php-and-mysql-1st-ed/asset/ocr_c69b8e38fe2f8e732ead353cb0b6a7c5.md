handler that displays appropriate messages to end users and reports detailed, technical messages only to you. You'll see specific code for doing this in the example chapters.

*nix is a common abbreviation for Unix and Unix-like operating systems, such as Linux.

If you're using a shared host, another recommendation I'd make is to change the session directory. By default, PHP will write all session data to a common, temporary directory, such as `/tmp` on *nix systems. But this directory is readable and writable by anyone on the server, meaning that any user on the server — and a shared host may have dozens — can read the session data stored therein. A better alternative is to create a writable directory within your own, private area of the server that only your site will use for the sessions.

My final PHP recommendation isn't a setting, but involves practices you won't see me do elsewhere, so I want it to be clear now. You should absolutely avoid using functions that execute code on the server, such as `system()` and `exec()`. Also, be careful when using any function that manipulates server files and directories, whether that means creating, opening, reading, or writing. When you must manipulate server files and directories, be 100 percent certain that you're using thoroughly validated data in these function calls, not unvalidated user-supplied data.

# Database Security

See the MySQL manual, or my book *MySQL: Visual QuickStart Guide, 2nd Edition* (Peachpit Press, 0-321-37573-4) for instructions on creating MySQL users.

Even if your Web site will not be storing the most dangerous customer information —their credit card data —the database needs to be thoroughly protected, as the breach of any customer information is a huge business liability.

The front line of database defense is MySQL's access privileges system. MySQL allows you to create specific users that have limited permissions on only particular databases. Users are identified by the combination of their name, password, and host (that is, which computer the user is on). To start, create unique, secure usernames with unique, extremely secure passwords. And, as with pretty much everything, it's really best to change those passwords regularly. Also, be certain to change the root user's password on a new MySQL installation.

Delete any databases whose name begins with "test," because MySQL allows any user to connect to them.

Next, every MySQL user should only be able to connect to MySQL from `localhost` or `127.0.0.1` (that is, from the same server). If MySQL is running on a machine separate from the Web server, you can create a MySQL user that has permission to connect only from that other server's IP address. An added benefit of restricting users to just `127.0.0.1` and specific IP addresses (if other IP addresses are absolutely necessary) is that you can then run MySQL with the `--skip-name-resolve` and `--skip-networking` options. This is more secure and will improve performance, because MySQL won't need to resolve host names.