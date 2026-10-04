# E-mailing with PHP

After clicking Send, the user receives an e-mail showing him or her the postcard message like. A link is provided at the bottom of the e-mail asking the user to confirm the postcard.

Once the user Sent! Internet clicks the confirmation link, the postcard is sent to the intended recipient.

![](bbox=[0.301, 0.183, 0.814, 0.743])

# 10-9

By now, you should be fairly familiar with using PHP to access MySQL. The file db_makeconfirm.php is pretty standard:

```
$sql = <<EOD
CREATE TABLE confirm (
    id INT NULL PRIMARY KEY AUTO_INCREMENT,
    validator VARCHAR (32) NOT NULL,
```