
$objRecipient->getStringRepresentation()))) {
    parent::addRecipient($objRecipient);
}
}

public function removeBlindRecipient($objRecipient) {
    if (!($this->arRecipientCollection->exists(
        $objRecipient->getStringRepresentation()))) {
        parent::removeRecipient($objRecipient->getStringRepresentation());
    }
}

public function setSubject($strSubject) {
    $this->strSubjectLine = $strSubject;
}

public function setMessageBody($strMessageBody) {
    $this->_setMessage($strMessageBody);
}

public function setSender($objSender) {
    $this->objApparentSender = $objSender->__clone();
}

public function send() {

    // Establish headers
    $strHeaders .= "From: " .
        $this->objApparentSender->getStringRepresentation() . "\n";
    $strHeaders .= "To: " .
        $this->objApparentPrimaryRecipient->getStringRepresentation() . "\n";
    foreach ($this->arObjApparentSecondaryRecipients as $strRecipientIdentifier =>
        $objEmailRecipient) {
        $strHeaders .= "Cc: " . $objEmailRecipient->getStringRepresentation() . "\n";
    }
    $strHeaders .= "Date: " . date('D, M j H:i:s T Y O') . "\n";

    // Establish body
    $strBody = $this->_getMessage();

    // Pull together to form complete email, correctly formatted
    $strFullEmail = $strHeaders . "\n" . $strBody;

if (!($smtp = new Net_SMTP("mail"))) {
    $this->strErrorMessage = "Unable to instantiate Net_SMTP object";
    $this->errorCode = 1;
    return(false);
}

if (PEAR::isError($e = $smtp->connect())) {
    $this->strErrorMessage = $e->getMessage();
    $this->errorCode = 2;
    $smtp->disconnect();
    return(false);
}

if (PEAR::isError($smtp->mailFrom(
    $this->objApparentSender->getStringRepresentation())))) {
    $this->strErrorMessage = "Unable to set sender";
    $this->errorCode = 3;
    $smtp->disconnect();
    return(false);
}

// Send to each recipient
foreach ($this->arRecipientCollection as $strRecipientIdentifier =>
    $objEmailRecipient) {
    $strThisAddress = $objEmailRecipient->getRecipientAddress();
    if (PEAR::isError($res = $smtp->rcptTo($strThisAddress))) {
        $this->strErrorMessage = "Unable to add recipient " . $strThisAddress;
        $this->errorCode = 4;
        $smtp->disconnect();
        return(false);
    }
};

if (PEAR::isError($smtp->data($strFullEmail))) {
    $this->strErrorMessage = "Unable to send data to server";
    $this->errorCode = 5;
    $smtp->disconnect();
    return(false);
}
$smtp->disconnect();
return(true);
}
};

Note a few things about this approach. First, when a recipient is added as the primary recipient or a member of the carbon copy (Cc) list, you can add the recipient to the collection held in the parent superclass, and then clone the recipient object before adding to the list of apparent recipients. This step isn't vital, but it means that you can implement your own `clone()` method in your `EmailRecipient` class, if you want, to modify the behavior taken when this copy is made.

Second, this example uses the error code and error message member variables of the `Communication` superclass. These are accessible through public functions. You can use these to debug your applications. E-mail can be an unpredictable phenomenon at times, and failure can occur through any number of scenarios, including a failure to reach the SMTP server, being denied permission to send e-mail to your particular IP address, or having a recipient be rejected outright by the SMTP server.

Third, the code `date("D, M j H:i:s T Y O")` is used to construct the e-mail header's date property. A quick glance at the PHP documentation reminds you that this produces a timestamp in the format `Tue, Jul 20 22:58:58 BST 2004 +0100`, which is the format required in e-mail headers.

To test the final working class, you can knock out some code like the following:

```php
$objEmail = new EmailCommunication;
$objEmailRecipient = new EmailRecipient("ed@example.com", "Ed Lecky-Thompson");
$objEmailCCRecipient = new EmailRecipient("cc@example.com", "Ted Lecky-Thompson");
$objEmailSender = new EmailRecipient("info@example.com", "Test Sender");
$objEmail->setPrimaryRecipient($objEmailRecipient);
$objEmail->setSender($objEmailSender);
$objEmail->setMessageBody("Hello, \n\nThis is a short test email.\n\nGoodbye!");
$objEmail->setSubject("Test Subject");
$objEmail->addCarbonRecipient($objEmailCCRecipient);
$objEmail->addBlindRecipient($objEmailBCCRecipient);

if ($objEmail->send()) {
    print "DONE! All went well! Mail sent successfully.";
} else {
    print "Sorry, didn't send mail successfully.";
};
```

## Being Smart with Templates

In Chapter 13 we talk about how separating application and display logic from each other through the model-view-controller (MVC) paradigm is generally an excellent idea, one well worth pursuing in your own application architecture.

Chapter 13 also covers a package called Smarty, which helps you do just that, and describes how useful it can be in traditional Web application implementation. Smarty has another use that is often overlooked: It can produce template-driven e-mail output.

As you know, nine times out of ten, the e-mails you send your users will be virtually the same. A few tags, or the first name after "Dear," or an account number might change, but not much else.

Splicing variables into strings is fine for smaller operations, but when those e-mails start to get bigger and more unwieldy, and even contain printed array structures, things will get tough. The solution is to use the TemplatedEmailCommunication class.

The TemplatedEmailCommunication class makes full use of Smarty. If you haven’t read Chapter 13 yet, now would be an excellent time. You need to know how Smarty works in order to pull this off.

The class you’re about to create actually extends EmailCommunication, so have that up and running first; and have Smarty installed and working, too:

```php
class TemplatedEmailCommunication extends EmailCommunication {

    private $path_to_template_file;
    private $objSmarty;

    public function __construct($strPathToTemplateFile) {
        $this->objSmarty = new Smarty;
        $this->path_to_template_file = $strPathToTemplateFile;
        parent::__construct();
    }

    public function setParameter($strParameter, $strValue) {
        $this->objSmarty->assign($strParameter, $strValue);
    }

    public function parse() {
        $this->setMessageBody($this->objSmarty->fetch($this
            ->path_to_template_file));
    }
}
```

The preceding code is simple but effective. Now try the following code. It needs to point to a simple Smarty template, so first create a template file named `test.tpl` as follows:

Name: {$name}
Favorite Food: {$favefood}

Next, enter the PHP code that follows. Ensure that it resides in the same directory as your Smarty template, or modify the first line to point to the right path. You’ll see that it’s very similar to the last time you took `EmailCommunication` for a drive, but the differences in the code are highlighted for you:

```php
$objEmail = new TemplatedEmailCommunication("test.tpl");
$objEmail->setParameter("name", "Ed");
$objEmail->setParameter("favefood", "Steak");
$objEmail->parse();

$objEmailRecipient = new EmailRecipient("ed@example.com", "Ed Lecky-Thompson");
$objEmailSender = new EmailRecipient("info@example.com", "Test Sender");
$objEmail->setPrimaryRecipient($objEmailRecipient);
$objEmail->setSender($objEmailSender);
$objEmail->setSubject("Test Subject");

if ($objEmail->send()) {
    print "DONE! All went well! Mail sent successfully.";
} else {
    print "Sorry, didn't send mail successfully.";
};
```

This produces the following output in the body of the sent e-mail:

Name: Ed
Favorite Food: Steak

As you can see, the `parse()` method constructed the body of the e-mail for you. Smarty parsed the template according to the two parameters you gave it; but rather than use the traditional `display()` method, you use `fetch()` to capture its output into a string. You then set the message body to be that string and you’re all set to send the e-mail.

Note that by extending the `EmailCommunication` class, you’ve not only avoided reinventing the wheel with respect to recipient management and SMTP connectivity, but also kept the `TemplatedEmailCommunication` class down to just a few lines of code, making it much easier to tinker with.
