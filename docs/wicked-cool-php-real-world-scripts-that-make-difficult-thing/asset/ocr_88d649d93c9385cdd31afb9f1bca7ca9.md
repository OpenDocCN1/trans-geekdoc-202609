Finish by assigning the title and displaying the template (see Figure 12-8 for the final result):

```
$smarty->assign("title", "blog: index");
$smarty->display("blog_index.tpl");
?>
```

![](bbox=[0.23, 0.19, 0.74, 0.375])

Figure 12-8: Blog entry index

# Hacking the Script

Blogs were made for hacking. There are many features that you can add to this system, and all of them build upon or expand your PHP knowledge. Here are a few sample ideas:

+   - **Archive** Once you start to have more than a few entries, you need to split up the index by pages. “#3: Creating Previous/Next Links” on page 7 can help you with that.
+   - **RSS feed** Apply your knowledge of how to create web services from “#3: Building a Web Service” on page 151 to this system, and you’ve syndicated the blog.
+   - **Login and administration** As it stands, anyone can add entries to a blog. You can prevent that by requiring a login to add entries. Furthermore, you can add multiple blogs by adding usernames to the blog tables.
+   - **CAPTCHA for comments** If you have a blog, you’re going to have spam comments. Eliminate them with the script that you saw in “#66: Creating a CAPTCHA (Security) Image” on page 129 or with Akismet.

Whatever you do, have fun with it!