| Command | Response Codes |
| :--- | :--- |
| MAIL FROM | Success: 250<br>Failure: 552, 451, 452<br>Error: 500, 501, 421 |
| RCPT TO | Success: 250<br>Failure: 550, 551, 552, 553, 450, 451, 452<br>Error: 500, 501, 503, 421 |
| DATA | Success: 354<br>Failure: 451, 554<br>Error: 500, 501, 503, 421<br><br>After sending data:<br>Success: 250<br>Failure: 552, 554, 451, 452 |
| QUIT | Success: 221<br>Error: 500 |

As you may have guessed, these server response codes help you determine whether a particular action was successfully performed. Note that the DATA command needs to be checked twice; when entering the mail composing state and when composition ends with a single dot on a line by itself. The DATA command is successful only when a 250 response code is returned after entering the dot.

With this SMTP background under your belt, creating an SMTP mailer class is a snap. You can extend the existing My_Mail class inheriting all the properties and methods while adding a couple of additional properties and methods, and overriding the send() method with its own.

Here's the complete source code of the class.

# Extending My_Mail class

In order to use the My_Mail class, you need to include the script it is defined in.

```
<?php
// my_smtp_mail_class.php
include "./my_mail_class.php";
class My_Smtp_Mail extends My_Mail
{
```