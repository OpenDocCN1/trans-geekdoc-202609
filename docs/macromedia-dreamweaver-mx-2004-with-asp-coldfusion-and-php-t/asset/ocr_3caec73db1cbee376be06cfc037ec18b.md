If you are using ColdFusion, most likely you did not enter the correct Internet or IP address of your outgoing SMTP mail server.

+   7) Close messageSent.asp.

Now that you have the messaging itself working, you need to make it useful, by putting meaningful content into the message. To do that, you'll use a form to collect the message data from the user, and then you'll send that data to the mail object, which in turn will send it (ostensibly) to Newland Tours staff.

# CREATING THE WEB FORM

In this task, you will create a form to collect data from the user, and you will send that data to messageSent.asp. Before you continue and start reading through the steps, test your knowledge. How do you send data to messageSent.asp? Should you use GET or POST? What fields should the form contain?

+   1) Open contact.asp. Change the table on the page containing the mailing, phone, and email information so it appears as in the screenshot. Also, change the first body paragraph so it reflects the new page structure.

One benefit of placing your email address in server-side code is that spammers have no access to it. If you put your email address on the page, as in the current version of the site, spammers' automated email address harvesting tools have easy access to it and can (and will) add it to their lists. By switching to a mail-based form, you keep your email address more private.

![](bbox=[0.07, 0.56, 0.745, 0.77])