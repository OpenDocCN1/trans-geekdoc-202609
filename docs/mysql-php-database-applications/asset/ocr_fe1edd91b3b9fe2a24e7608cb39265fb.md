```
)
)
)
```

The final portion of this page simply prints the form in which the user will enter
his or her email. There's really no need to show that here.

# Summary

The survey application involves quite a bit of code, but it isn't anything that you
shouldn't be able to figure out with some close scrutiny of the files and the comments.
Take a look at the complex_results.php page and its includes (age_results.php,
state_results.php, and country_results.php) for a look at how MySQL aggregate
functions can come in handy.

This application contains much more complexity than the guestbook. In it is a
real database schema complete with related tables. In the course of the application
we need to make use of queries that contain MySQL functions. (See Appendix J for
more information on MySQL functions.)

Another notable item seen in this chapter is the function set we've created for
creating common HTML elements. Whether you want to make use of such functions
or not is up to you. You may prefer typing out individual form elements, tables, and
the like. But you will be seeing these functions used in the remainder of this book.