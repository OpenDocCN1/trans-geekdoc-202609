# Chapter 20. INTEGRATION WITH HTML

Sprinkling PHP within an HTML Document

Using the PHP to Output All HTML

Separating HTML from PHP

Creating <SELECT> Fields

Passing Arrays in Forms

By this time, you have learned the basics of PHP. You have a reference for the functions. And you've been introduced to some fundamental problems of programming. But all the examples I've seen here have pieces, snippets for the sake of illustration. This chapter will discuss how to integrate PHP into a Web site. It how to sprinkle PHP throughout the site, or to simply create a few PHP-driven pages. I will also discuss issues involved in using PHP to generate HTML.

# Sprinkling PHP within an HTML Document

The first and most obvious approach to using PHP is to build HTML files as you have always done, inserting PHP tags as if they were HTML tags. This could take the form of repeating HTML tags that replace with a call to a PHP function. It could take the form of a large block of PHP code that generates database output. Or it could be a script that processes a form submission. These are all situations where the impact of PHP on the site is slight. This is a good first step for those new to programming. You are able to insert the smallest amount of PHP code as a test. As your experience and confidence grow, so will your reliance on PHP.

Let's examine creating a function to replace repeating HTML. One great aspect of cascading style sheets is that they allow you to redefine how tags behave. Unfortunately, this technology is only available in the latest versions of Navigator and Internet Explorer. You can provide some functionality on the server side with PHP. Suppose we would like all of our headers to be in uppercase letters, size 7, and blue. The solution is to write a function that takes a string and prints it in the proper format.

In Listing 20.1 I've created a function called PrintTitle. This function wraps a given string in tags. In some cases the code is more readable than if I simply written it as static HTML, because each time there is a title, we call the call to the PrintTitle function. This may have more meaning than the collection of tags for which it stands. This is one of the benefits of functions in general: they wrap up functionality into a single name.