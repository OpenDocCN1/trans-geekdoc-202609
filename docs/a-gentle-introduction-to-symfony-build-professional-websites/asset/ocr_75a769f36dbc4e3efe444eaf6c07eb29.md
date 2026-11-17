![](bbox=[0.12, 0.08, 0.76, 0.31])

Each time an email is sent, symfony also adds a message in the log.

# Testing

Of course, the integration would not have been complete without a way to test mail messages. By default, symfony registers a mailer tester (sfMailerTester) to ease mail testing in functional tests.

The hasSent() method tests the number of messages sent during the current request:

```
Listing 11-19
$browser->
  get('/foo')->
  with('mailer')->
  hasSent(1)
;
```

The previous code checks that the /foo URL sends only one email.

Each sent email can be further tested with the help of the checkHeader() and checkBody() methods:

```
Listing 11-20
$browser->
  get('/foo')->
  with('mailer')->begin()->
  hasSent(1)->
  checkHeader('Subject', '/Subject/')->
  checkBody('/Body/')->
  end()
;
```

The second argument of checkHeader() and the first argument of checkBody() can be one of the following:

+   * a string to check an exact match;
+   * a regular expression to check the value against it;
+   * a negative regular expression (a regular expression starting with a !) to check that the value does not match.