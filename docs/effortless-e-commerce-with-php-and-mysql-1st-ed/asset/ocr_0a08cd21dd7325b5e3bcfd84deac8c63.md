tip

If MySQL is running with the --log-long-format feature enabled, the database will write to the log any queries that aren't using indexes.

A final consideration in your database design, which gets less attention, is the storage engine (or table type) in use. One of MySQL's strengths is its support for multiple storage engines, meaning you can select the one whose features best match your needs. For example, you can create MySQL tables in memory, which will perform exceptionally well but provide no data permanence. The two most common MySQL storage engines are InnoDB and MyISAM. The former is the default type for Windows computers and the latter is the default for all other operating systems. MyISAM is an excellent, all-purpose storage engine that also supports FULLTEXT indexes, useful in searches. The InnoDB engine doesn't support FULLTEXT but can handle transactions, an excellent fail-safe in sensitive situations.

If you have administrative-level control over your database, there are a number of configurations that impact MySQL's performance. To start, there is back_log, key_buffer_size, max_connections, and thread_cache_size. You can use a configuration file to change these settings from their defaults to values more appropriate to your server and site. See the MySQL manual for more information for the version of MySQL that your server is running—assuming that you have that kind of control over your server, of course.

Should you get to a point where your site is so active that multiple servers are appropriate, you can consider replicating the database. Database replication stores the same data on more than one server. By doing so you'll get improved security, reliability (should one server fail, the data still lives on elsewhere), and performance.

# YOUR DEVELOPMENT TOOLS

What software you use on your computer to develop an e-commerce site is such a big and personal topic that I don't offer any recommendations on that front (at the very least because I primarily use a Mac and therefore couldn't recommended any development programs on Windows). If you don't already have a text editor or IDE that you like, again look online and get actual recommendations from people in order to select one. As with everything, your budget comes into play, although there are lots of excellent choices available at little to no cost.

Along with the programming software, you should consider project management tools, such as applications for organizing projects and taking notes. You may also need to use some accounting software, depending upon whether the e-commerce site is yours or not.