# Preserving State With Query Strings, Cookies, and Sessions

Most of the PHP scripts you created in previous chapters are very much one-shot affairs. Each time they run, they start with a "clean slate" of variables and other data. This is because each request that a browser makes to a Web server is independent of any previous requests. When a Web server receives a request to run a PHP script, it loads the script into its memory, runs it, then removes all trace of it from memory.

However, most of the Web applications you use today have a need to store data between browser requests. For example, a shopping cart needs to remember which items you have added to your cart, and a forum application needs to remember your identity when you post a message in the forum.

In other words, there is a need to preserve the current state of a user's interaction with an application from the next.

You've already looked at a simple example of storing data in the previous chapter, when you used hidden form fields to store previously entered data at each step of a three-stage registration form. Although filling in the registration involved three separate browser requests — therefore three separate runs of the PHP script — the script was able to "remember" the state of the registration process by storing it in the themselves.

Although this approach works perfectly for simple cases, it has a few disadvantages. For example, it's a slow to store large amounts of data, because all the data has to be carried backward and forward from browser to server during each request. What's more, it's pretty insecure, because it's almost trivial for a mischievous user to change the data stored in the form at will. In addition, if you need to store large numbers of variables between requests, as well as complex variables such as arrays and objects, the hidden form field approach can start to get quite cumbersome.