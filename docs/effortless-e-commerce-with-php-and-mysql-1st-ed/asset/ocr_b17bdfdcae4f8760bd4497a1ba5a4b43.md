# 5 MANAGING SITE CONTENT

If you’re reading this book in order—and I certainly hope you are— then you’ve got a site where users can register, log in, change their password, and log out, but there’s nothing for them to look at! On the other hand, they haven’t paid anything yet either, so...

In this chapter, you’ll create the content management side of the equation, with two kinds of content: HTML pages and PDFs. I’ll tell you how to write the code for creating and displaying the content.

But first, you’ll need to create an administrative user.

# CREATING AN ADMINISTRATOR

Even though administrators will use the same login system and the same underlying users table as regular users, for security reasons, you cannot create an administrator through the site itself. By making that decision, no possible flaw in the site could result in administrators being created. And since administration accounts won’t be created often, it makes sense not to implement that feature anyway. But you still need at least one administrator, so let’s do that now.

+   1. Register the administrator using the same registration page.