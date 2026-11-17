```
{
    $msg = unserialize($message);
    $this->setPriority($msg->getPriority());
    parent::setMessage($message);
}
```

```
// for Doctrine
class MailMessage extends BaseMailMessage
{
    public function setMessage($message)
    {
        $msg = unserialize($message);
        $this->priority = $msg->getPriority();

        $this->_set('message', $message);
    }
}
```

Notice that the message is serialized by the queue, so it has to be unserialized before getting the priority value. Now, create a method that orders the messages by priority:

```
// for Propel
class MailMessagePeer extends BaseMailMessagePeer
{
    static public function getSpooledMessages(Criteria $criteria)
    {
        $criteria->addAscendingOrderByColumn(self::PRIORITY);

        return self::doSelect($criteria);
    }

    // ...
}
```

```
// for Doctrine
class MailMessageTable extends Doctrine_Table
{
    public function getSpooledMessages()
    {
        return $this->createQuery('m')
            ->orderBy('m.priority')
        ;

    }

    // ...
}
```

The last step is to define the retrieval method in the factories.yml configuration to change the default way in which the messages are obtained from the queue:

```
spool_arguments: [ MailMessage, message, getSpooledMessages ]
```

That's all there is to it. Now, each time you run the project:send-emails task, each email will be sent according to its priority.