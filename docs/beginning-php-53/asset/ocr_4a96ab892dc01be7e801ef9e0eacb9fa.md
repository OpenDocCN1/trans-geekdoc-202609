![](bbox=[0.392, 0.0, 0.645, 0.2])

# # Alternatives to MySQL

In Chapters 12 through 14 you learned how to access MySQL databases from within your PHP applications. MySQL is often a great choice if you’re writing PHP scripts, because it’s freely available, cross-platform, and is installed by default on most PHP-supported Web servers.

However, MySQL isn’t for everyone, and in some scenarios it’s preferable to use an alternative database engine. This appendix takes a brief look at some of the more popular alternatives on the market. Most of these can work with the PDO extension that is described in Chapters 12 through 14, so if you do want to try a different database engine most of the content and examples in those chapters will still apply.

# ## SQLite

If you asked the average developer what is the most popular SQL database engine in use today, they’d probably think of MySQL, Oracle, or SQL Server. In fact the answer is probably SQLite (see `http://www.sqlite.org/mostdeployed.html` for the breakdown). The reason for this (apart from the fact that it’s very good) is that it’s an embedded database engine. This means that it’s bundled inside every copy of every application that uses it, from Firefox through to Skype and various mobile platforms including Symbian and iPhone. Contrast this with, say, MySQL, which consists of a separate server application, along with client libraries to talk to the server.

Another nice thing about SQLite is that its code is in the public domain, meaning that anyone can use and modify the code as they see fit.

These days SQLite is bundled with the PHP engine, which means you don’t have to install anything extra to start using it. It’s very fast, supports nearly every standard SQL command, and has some rather special tricks up its sleeve. It’s also relatively simple (because it doesn’t have a client-server architecture) and very reliable. In a nutshell, it’s well worth checking out.