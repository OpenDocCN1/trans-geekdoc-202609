However, both HTTP GET and HTTP POST can send output to the Web browser in just the same way. It’s perfectly viable for an HTTP POST to result in output being sent to the Web browser — but what happens if you click Refresh (or press F5) on such a page? Figure 13-5 illustrates just that.

![](bbox=[0.305, 0.172, 0.595, 0.278])

# Figure 13-5 Error message when attempting to refresh the page

The dialog shown in Figure 13-5 is a royal pain, but it exists to protect users from themselves. Who is to say what would happen if the page were resubmitted? If this were an “add to cart” page, an item could be added to the shopping cart more than once. If it were a “pay for order” page, the order could be paid for more than once.

Using PRG, this dialog never appears. Every HTTP POST (no matter how trivial) results in a subsequent HTTP GET, initiated using a 302 redirect — in practice, something achieved using the header() function in PHP. This tells the browser to request a different page, rather than render any output. You can store whatever output of your page should be temporarily in the session, or even in a client-side cookie in a pinch. Just don’t render it to the browser, as sending even a single byte of HTML will make redirection impossible.

This whole process is virtually invisible to the end user, but it means that should the user refresh the page following an HTTP POST, it will, in fact, be the subsequent HTTP GET the user is refreshing, not the POST at all. This GET should be benign. It should simply render output in a matter-of-fact kind of way. The refresh, therefore, is of no great consequence.

For more information about this, use Google to search for “post-redirect-get,” or see http://en.wikipedia.org/wiki/Post/Redirect/Get.

# The Toolkit in the Wild

By this point in the chapter, you have built a mini toolkit that enables you to easily handle requests and constraints as part of using an MVC design pattern in your projects. You have also learned a simple method for using templates in native PHP.

The built-in constraints in the request object you have created here are relatively simple and, admittedly, could be quite easily implemented in raw PHP within your control page. Constraints really come into their own when they become complex, such as when they need to query a data source to determine validity. On occasions such as this, it may make sense to “genericize” your request object, and then extend it to form multiple request objects (perhaps one per page) that handle a different range of constraints in each case.

Later in this chapter, you’ll learn about Smarty — an entirely different way of doing templating.