Suppose that you designed a small Web application. Over time, your client kept adding new features to it, and gradually the number of classes in the application increased. Certain pages on your Web site started building up many calls to the various objects. Such pages might resemble the following example:

```
$dbManager = new DBManager();
$userArray = $dbManager->getNewUsers();
$mailer = new Mailer();
$stats = new StatLog();

for ($i = 0; $i < count($UserArray[$i]; $i++) {
    $user = $UserArray[$i];
    $userPref = $user->getMailPreference();
    $userMail = $user->getEmail();

    if ($userPref == true) {
        $mailer->sendMailToUser($userMail);
    } else {
        $stats->storeUnmailedUser($user->getID());
    }
}
```

The preceding hypothetical code would send an e-mail to new users who indicated they want to receive mail. If they don't want to receive mail, their userID would be sent to a part of the application that manages statistics about users. Although this code isn't too ugly, if you had to mix in large amounts of HTML and get information back to report to the user, it might become unwieldy. Following is another version of using the facade pattern:

```
Application::mailNewUsers();
```

Now, any time this functionality is required, the front end just requests it from the facade (in this case, the Application class). All messages from the front end of the site go through the Application class and never interact directly with the other objects in the system. The Application object's methods can be static because you don't even need an instance of the Application class.

Notice that the client of the Application class doesn't need to know how it works internally. One good result of this (in addition to cleaner code) is that it enables a separation of front-end presentation and back-end functionality. The less your application is tied up in a particular presentation of HTML, the more likely it is to be reusable elsewhere. There's more discussion of this good design practice in Chapter 13.

# The Builder Pattern

If you look back at the composite pattern, you'll notice that the objects that made up the composite were manually created, as shown in the following example:

```
$drums = new DrumSet("tama maple set");
$drums->add(new SnareDrum("snare drum"));
$drums->add(new BaseDrum("large bass drum"));
```