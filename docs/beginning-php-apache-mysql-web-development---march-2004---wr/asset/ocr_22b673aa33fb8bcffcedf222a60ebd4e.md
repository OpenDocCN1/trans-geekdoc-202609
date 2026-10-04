# Handling and Avoiding Errors

You will probably be spending a fair amount of time contemplating errors in your code, as do most Web developers when they start programming. No matter how good you are, how good your code, how long you have been coding, or how hard you try, you will encounter times you have errors in your code.

It is of the utmost importance that you know how to handle your errors and debug your own code. Being able to efficiently and properly debug your code is an invaluable time-saver; and in Web development, Time \$money!

Luckily, PHP comes with a full-featured API (Applications Programming Interface) that provides you with many ways to trap and resolve those unwanted errors. PHP also allows you to use the API to capture the errors and create your own custom function orders or pages. These features seem to be useful when debugging your code and notifying your Webmaster about errors that seem to be happening to your applications as users are running. Not only can you use PHP code to trap and customize them; you can use the Apache Web Server to help do this.

# How the Apache Web Server Deals with Errors

Apache has a directive, the ErrorDocument, that you can configure in the http.conf file to create custom error pages with PHP visitors to your site won't see the boring server-created error pages. There are limitless possibilities when creating these custom messages. As with the PHP error-catching pages, you can have the ErrorDocument call PHP to do whatever you would like them to—from simply displaying a friendly error message to the user to e-mailing a system administrator to notify him or her of the failure.

Now, unlike PHP error pages, the Apache ErrorDocument pages are used more for instances of missing pages (that is, a "Page Not Found" error or Forbidden access error pages and other