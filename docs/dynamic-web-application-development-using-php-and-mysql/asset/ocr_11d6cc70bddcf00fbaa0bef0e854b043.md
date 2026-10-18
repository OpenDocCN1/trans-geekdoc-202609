accompanying script into a single file. We examine each of the form field types and illustrate how the data from each of them can be accessed. We conclude the chapter by examining form validation and how to retain data on a form so that the user doesn't have to retype it.

# 10.1 PHP and form interaction

As previously mentioned, PHP can use forms to allow a script to interact with the user. But how does this work and why would we want to do this? Well, in Chapter 9, we set a few exercises where user interaction would have allowed us to produce a far more interesting and useful script. Consider the Arabic to Roman date conversion problem. Because we were unable to interact with the script we were unable to alter the date that we wished to convert without modifying the original script. While this is slightly annoying in a development environment, it has far more serious consequences for any scripts we may wish to make available online to the Web community.

Consider the security implications that would surround allowing everyone access to your server to make changes to your PHP scripts! Apart from allowing access to the inner workings of your code (which you may not wish to do for confidentiality reasons), you would have to trust everyone who modified your script to do this properly and in an orderly fashion. Basically, this is not going to work and so a mechanism to allow users to specify the data that they wish to input to the script needs to be implemented and this is where forms come in.

By using an XHTML form, we can provide an interface (the form itself) to allow, for example, a user to enter the date they wish to convert. This date can then be transferred

**FIGURE 10.1** Using forms to interact with PHP

![](bbox=[0.187, 0.555, 0.918, 0.945])