# 11

# # User Logins, Profiles, and Personalization

In this chapter, you learn to manipulate Web pages with user logins, profiles, and personalization using PHP's session and cookie functions. You create a useful login and personalization application that you can use in conjunction with the applications you have created thus far.

Session and cookie functions are two of the most fundamental, important, and useful functions you will encounter in the PHP programming language. Not noticed about the value of these yet? Think about it way: You wouldn't just anyone guessing where you have your important files and missing with information to change your Web site in any he or she wanted, would you? Well, with htaccess, and better yet, PHP sessions, you can combat hackers or the general public from "stumbling" onto your sensitive files and directories.

Specifically, we will be showing you to:

+   - Restrict access to files/directories via htaccess
- Use PHP to accomplish the same function as htaccess, but with more control and functionality
- Store user and admin information in a database to utilize database-driven logins
- Create a registration system with required and optional fields for users to sign up
- Take a quick look at cookies to keep login information between sessions
- Create a navigation system dependent on whether or not a user has logged in

# # The Easiest Way to Protect Your Files

Using htaccess is a simple and quick solution to restricting access to files or directory structures. Some Web sites contain sensitive information that you don't want the public to access. Perhaps you have an administration section where administrators change the content of the public site, such as in a news or upcoming events section; you don't just want anybody to change that content.