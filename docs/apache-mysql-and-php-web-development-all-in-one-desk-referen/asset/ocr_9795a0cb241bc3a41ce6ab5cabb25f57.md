# # Chapter 8: Ten Ways to Enhance a Web Site with Databases

# ## In This Chapter

+   - Programming an online user poll
+   - Adding a hit counter
+   - Performing advanced queries
+   - Creating databases that support transactions
+   - Building a forum or message board
+   - Creating a journal or daily note
+   - Building a distributed database
+   - Tracking usage information

In this final chapter in the MySQL minibook, I give you some suggestions on ways you can use MySQL to make a great Web site.

# ## Programming an Online User Poll

I like to put polls on my site that allow visitors to vote on various things. For some time, I’ve been running a poll asking people what C++ compiler they use.

I didn’t write the poll myself because I wanted to get it up immediately when I launched my site and didn’t have time to write one. However, I now realize that writing a poll isn’t that complex.

Here’s what you need to do to write a poll:

+   - Create a Web form whereby users can choose their answers to the poll.
+   - Create a PHP page that updates the results in a MySQL table.
+   - Write a PHP (or Perl or any other) program that reads the data in the results table and writes out an HTML page showing the results of the poll. If you’re using PHP, I recommend taking a look at Book V, Chapter 8, to discover ways that you can present data in the form of a bar graph.