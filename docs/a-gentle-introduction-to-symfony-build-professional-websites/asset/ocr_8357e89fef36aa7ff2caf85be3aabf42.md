```
Listing 11-3
$this->getMailer()->composeAndSend(
    'from@example.com',
    'fabien@example.com',
    'Subject',
    'Body'
);
```

The composeAndSend() method takes four arguments:

+   - the sender email address (from);
+   - the recipient email address(es) (to);
+   - the subject of the message;
+   - the body of the message.

Whenever a method takes an email address as a parameter, you can pass a string or an array:

```
Listing 11-4
$address = 'fabien@example.com';
$address = array('fabien@example.com' => 'Fabien Potencier');
```

Of course, you can send an email to several people at once by passing an array of emails as the second argument of the method:

```
Listing 11-5
$to = array(
    'foo@example.com',
    'bar@example.com',
);
$this->getMailer()->composeAndSend('from@example.com', $to, 'Subject',
    'Body');
```

```
$to = array(
    'foo@example.com' => 'Mr Foo',
    'bar@example.com' => 'Miss Bar',
);
$this->getMailer()->composeAndSend('from@example.com', $to, 'Subject',
    'Body');
```

# The Flexible Way

If you need more flexibility, you can also use the sfAction::compose() method to create a message, customize it the way you want, and eventually send it. This is useful, for instance, when you need to add an attachment as shown below:

```
Listing 11-6
// create a message object
$message = $this->getMailer()
    ->compose('from@example.com', 'fabien@example.com', 'Subject', 'Body')
    ->attach(Swift_Attachment::fromPath('/path/to/a/file.zip'))
;

// send the message
$this->getMailer()->send($message);
```

# The Powerful Way

You can also create a message object directly for even more flexibility:

```
Listing 11-7
$message = Swift_Message::newInstance()
    ->setFrom('from@example.com')
```