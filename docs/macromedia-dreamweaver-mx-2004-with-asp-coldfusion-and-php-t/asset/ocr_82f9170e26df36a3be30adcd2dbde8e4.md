![](bbox=[0.06, 0.066, 0.447, 0.362])

The question is, how do we find out whose account has been used? To answer that, think about what data is available to the page. This page has a Restrict Access to Page behavior attached to it. This behavior checks for the presence of a session variable set when the user successfully logged in. If that variable exists, it checks to see if its user is in the admin group. In other words, for a user to be on this page, she or he must not only be logged in with an admin account, but also the page must already know which account. Since this information is already available to the page as a session variable, all you have to do is bind that value to the hidden field, and it will be written into the database along with the form.

2) Use the Bindings panel to add a new session variable binding. In the Session Variable dialog, enter MM_Username, and click OK.

MM_Username is the session variable that is set when the user logs in. It is created automatically when you use the Log In User server behavior.

One thing to remember about the Bindings panel: The bindings it lists are limited to ones that you enter. In other words, even though MM_Username has been available all along as a session variable, as a part of the Restrict Access to Page server behavior, it is not listed in the Bindings panel unless you explicitly put it there.

![](bbox=[0.06, 0.815, 0.42, 0.92])