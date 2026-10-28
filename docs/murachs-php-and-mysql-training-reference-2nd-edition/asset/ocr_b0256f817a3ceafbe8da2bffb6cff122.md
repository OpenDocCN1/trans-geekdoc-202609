# A helper function for sending an email

Figure 22-4 presents the code for a helper function named send_email that you can use to make it easier to create and send an email message. This function validates the email addresses that are passed to it, connects to the SMTP server, and sends the email.

This code in this file starts by loading two files. The first file (Mail.php) is the PEAR Mail package. The second file (RFC822.php) is another PHP file. It provides a method named parseAddressList that validates a list of email addresses where each email address may be in this format:

```
```text
Full Name <username@example.com>
```
```

This method is used by the valid_email function that’s in part 2 of this figure.

The send_email function accepts five parameters. Here, the first four parameters are required: the From address, the To address, the subject line, and the body of the email. However, the fifth parameter is optional. This parameter specifies whether the body of the email is formatted with HTML tags. By default, this parameter is set to FALSE so the body of the message isn’t formatted with HTML tags.

This function begins by checking whether the From and To addresses are valid. To do that, it uses the valid_email function that’s in part 2. If an email address isn’t valid, this code throws an Exception object that contains an appropriate error message.

After validating the email addresses, this function sets the parameters for an SMTP server. When you use this code, you need to modify the $smtp array elements to match the values for your own SMTP server. If you don’t change the values, the code won’t work.

Once the parameters are set, the Mail::factory method is used to create a mailer object. Then, it uses the PEAR::isError method to check whether this method returned a PEAR_Error object. If it did, this code throws an exception that indicates that the code couldn’t create the mailer object.

After creating the mailer object, this code creates an array named $recipients. This array stores the addresses for all recipients of the email. For this function, this array only contains a single recipient, the To address. If necessary, though, you could create an enhanced version of this function that allows for multiple To, Cc, or Bcc addresses.

After creating the recipients list, this code sets the HTTP headers. Here, the code checks the $is_body_html parameter to determine whether to set the Content-type header. If this parameter is set to TRUE, this code sets the Content-type header to a value of “text/html”. This indicates that the body is formatted with HTML tags. Otherwise, this code leaves the Content-type header at its default value of “text/plain”.

After setting the headers, this code sends the email by calling the send method of the mailer object. To do that, this code passes the recipients array, the header array, and the message body to the send method, and it stores the return value in the variable named $result. Then, if the $result variable is an error, this code throws an exception. If not, it doesn’t do anything since no error indicates that the email has been sent successfully.