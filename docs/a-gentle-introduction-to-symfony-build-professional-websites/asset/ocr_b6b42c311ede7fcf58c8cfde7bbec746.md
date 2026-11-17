By default, the checks are done on the first message sent. If several messages have been sent, you can choose the one you want to test with the withMessage() method:

```
$browser->
    get('/foo') ->
    with('mailer') ->begin() ->
        hasSent(2) ->
        withMessage('foo@example.com') ->
        checkHeader('Subject', '/Subject/') ->
        checkBody('/Body/') ->
    end()
;

```

The withMessage() takes a recipient as its first argument. It also takes a second argument to indicate which message you want to test if several ones have been sent to the same recipient.

Last but not the least, the debug() method dumps the sent messages to spot problems when a test fails:

```
$browser->
    get('/foo') ->
    with('mailer') ->
    debug()
;

```

# # Email Messages as Classes

In this chapter's introduction, you have learnt how to send emails from an action. This is probably the easiest way to send emails in a symfony application and probably the best when you just need to send a few simple messages.

But when your application needs to manage a large number of different email messages, you should probably have a different strategy.

> As an added bonus, using classes for email messages means that the same email message can be used in different applications; a frontend and a backend one for instance.

As messages are plain PHP objects, the obvious way to organize your messages is to create one class for each of them:

```
// lib/email/ProjectConfirmationMessage.class.php
class ProjectConfirmationMessage extends Swift_Message
{
    public function __construct()
    {
        parent::__construct('Subject', 'Body');

        $this
            ->setFrom(array('app@example.com' => 'My App Bot'))
            ->attach('...')
        ;
    }
}

```