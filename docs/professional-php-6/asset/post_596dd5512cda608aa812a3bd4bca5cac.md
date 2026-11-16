
The constructor method concerns itself with the setup of these two additional private member variables, and calls the superclass constructor for good measure.

The various methods used for adding and removing the master recipient, carbon copy recipients, and blind carbon copy recipients all work in much the same way. They check to see whether an object of that key (the key being the string representation of the recipient object) exists in the collection before performing the relevant operation. This is achieved using the `exists` method provided by the `collection` object.

Take a look at some test addresses just to prove that it works. You can then go back and look at the way you actually send the mail. To execute the following code, you need to `require()` all the classes developed so far in this chapter. Call this `test2.php` so you can see it in your Web browser:

```php
<?php
require("collection.phpm");
require("communication.phpm");
require("emailcommunication.phpm");
require("recipient.phpm");
require("emailrecipient.phpm");
require("emailrecipientcollection.phpm");
$objEmail = new EmailCommunication;
$objEmailRecipient = new EmailRecipient("ed@example.com",
 "Ed Lecky-Thompson");
$objEmailCCRecipient = new EmailRecipient("ted@example.com",
 "Ted Lecky-Thompson");
$objEmailBCCRecipient = new EmailRecipient("zed@example.com",
 "Zed Lecky-Thompson");
$objEmail->setPrimaryRecipient($objEmailRecipient);
$objEmail->addCarbonRecipient($objEmailCCRecipient);
$objEmail->addBlindRecipient($objEmailBCCRecipient);
$objEmail->send(); ?>
```

Run the preceding code. You should get output like that shown here:

```
ACTUAL RECIPIENTS

NAME: Ed Lecky-Thompson
EMAIL ADDRESS: ed@example.com
NAME: Ted Lecky-Thompson
EMAIL ADDRESS: ted@example.com
NAME: Zed Lecky-Thompson
EMAIL ADDRESS: zed@example.com

APPARENTLY TO RECIPIENT

NAME: Ed Lecky-Thompson
EMAIL ADDRESS: ed@example.com

APPARENT SECONDARY RECIPIENTS

NAME: Ted Lecky-Thompson
EMAIL ADDRESS: ted@example.com
```

This looks pretty healthy. As you can see from the code, Ed is the main recipient of this e-mail, while Ted has been Cc’d, and Zed has been Bcc’d. When Ed receives the mail, he will be able to see his name on the To: line, and Ted’s on the Cc: line. Ed won’t know Zed got the mail. When Ted receives the mail, he will see much the same. Again, he won’t know Zed was Bcc’d on this important message. When Zed receives the mail, he won’t see his name anywhere, but he’ll be able to deduce that he must have been Bcc’d on the original message.

The output from this dummy test implementation shows that the code is correct. The list of actual recipients displays all three genuine recipients of the e-mail. The primary recipient is correct, and the Cc’d recipient is listed correctly, too.

## Getting the Message Across

You must do a couple of things to make the `EmailCommunication` class function properly.

First, you must get the body of the e-mail built and slotted into the `message` member variable. A simple, plain-text e-mail consists of two parts: the header and the body. Conveniently enough, the two are separated by nothing more complex than a blank line. The header contains the sender’s address, the recipient’s address, the subject, the Cc: addresses, and a myriad of other bits and pieces.

Now, add two member variables: one for the subject line and one for the sender. The sender can again be an `EmailRecipient` object because a sender has a name and an address, just like a recipient:

```php
private $objApparentSender; // Visible From: address
private $strSubjectLine; // Subject line
```

The use of some basic methods will allow users of the class to set these properties.

For the time being, assume that you’re dealing with purely plain text e-mails. You add a simple method to allow public setting of the message property. The message property is synonymous with the body of the e-mail, because the headers will be managed separately:

```php
public function setSubject($strSubject) {
	$this->strSubjectLine = $strSubject;
}

public function setMessageBody($strMessageBody) {
	$this->setMessage($strMessageBody);
}

public function setSender($objSender) {
	$this->objApparentSender = $objSender->__clone();
}
```

All that remains to do now is to convert the `send()` method into something that assembles a header and a body, glues them together, and spits them out to the Internet.

How do you go about doing that? The easiest way is with PEAR’s `Net_SMTP` package, which gels quite neatly with this setup, and again provides a good example of why PEAR is so useful in avoiding reinventing the wheel in your application development. The `Net_SMTP` package may already be installed in your PHP setup. If not, install it in the usual way.

## Part II: Learning Advanced Development Techniques

The basic syntax for using the Net_SMTP package is simple. You can feed it the assembled message as-is with no changes. Just tell it the operands to use when talking to the mail server. The minimum that the mail server requires is a sender and a list of recipients. The server doesn't look at your headers. This is why blind carbon copies work. Although the server is told to deliver the message to that recipient, the recipient is never listed anywhere in the headers.

The following example shows a basic usage of Net_SMTP, step by step, assuming that the completed message is in $full_message_content and that an array of recipients exists in $rcpt:

```php
if ( ! $smtp = new Net_SMTP("mail") ) {
    die("Unable to instantiate Net_SMTP object\n");
}
```

First, you instantiate a new instance of the Net_SMTP class with the name of your SMTP server, and die if you are unable to do so for some reason:

```php
if (PEAR::isError($e = $smtp->connect())) {
    die($e->getMessage() . "\n");
}
```

Next, you ensure that you can connect to the SMTP server you just specified; if not, you die:

```php
if (PEAR::isError($smtp->mailFrom("sender@example.com"))) {
    die("Unable to set sender\n");
}
```

In this case, the sender was set to be sender@example.com:

```php
foreach($rcpt as $recipient) {
    if (PEAR::isError($res = $smtp->rcptTo($rcpt))) {
        die("Unable to add recipient: " . $res->getMessage() . "\n");
    }
}
```

Now loop through your array of recipients, adding each into the Net_SMTP class instance and dying if any single recipient proves impossible to add:

```php
if (PEAR::isError($smtp->data($full_message_content))) {
    die("Unable to send data\n");
}
$smtp->disconnect();
```

Finally, you send your message and disconnect from the SMTP server.

Note that this example uses mail as the hostname of the remote SMTP server. If you're running on Linux or something similar, then you can probably stick a reference to the hostname mail in your /etc/hosts file pointing to 127.0.0.1 and everything will work fine out of the box. Otherwise, you must locate the nearest friendly SMTP server to relay for you, and use that instead.

Now take a look at the following finished `EmailCommunication` class, complete with an SMTP send through `Net_SMTP`:

```php
class EmailCommunication extends Communication {
private $objApparentSender; // Visible From: address
private $strSubjectLine; // Subject line
private $objApparentPrimaryRecipient; // Visible To: address
private $arObjApparentSecondaryRecipients; // Visible Cc: address(es)

public function __construct() {
// Superclass collection
$this->arRecipientCollection = new EmailRecipientCollection();
// Local collection of visible (CC:) recipients
$this->arObjApparentSecondaryRecipients = new EmailRecipientCollection();
parent::__construct();
}

public function setPrimaryRecipient($objRecipient) {
if (!($this->arRecipientCollection->exists(
$objRecipient->getStringRepresentation()))) {
parent::addRecipient($objRecipient);
}
$this->objApparentPrimaryRecipient = clone $objRecipient;
}

public function addCarbonRecipient($objRecipient) {
if (!($this->arRecipientCollection->exists(
$objRecipient->getStringRepresentation()))) {
parent::addRecipient($objRecipient);
};
if (!($this->arObjApparentSecondaryRecipients->exists(
$objRecipient->getStringRepresentation()))) {
$this->arObjApparentSecondaryRecipients->addItem(
$objRecipient, $objRecipient->getStringRepresentation()));
};
}

public function removeCarbonRecipient($objRecipient) {
if ($this->arRecipientCollection->exists(
$objRecipient->getStringRepresentation()))) {
parent::removeRecipient($objRecipient);
};
if (($this->arObjApparentSecondaryRecipients->exists(
$objRecipient->getStringRepresentation()))) {
$this->arObjApparentSecondaryRecipients->removeItem(
$objRecipient->getStringRepresentation()));
};
}

public function addBlindRecipient($objRecipient) {
if (!($this->arRecipientCollection->exists(
```
