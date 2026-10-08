# Implementing Bookmark Storage and Retrieval

```
throw new Exception('Could not find email address.');
// username not in db
el {
$row = $result->fetch_object();
$email = $row->email;
$from = "From: support@phpbookmark \r\n";
$msg = "Your PHPBookmark password has been changed to .$password.\r\n" .
      "Please change next time you log in.\r\n";

if($email, 'PHPBookmark login information', $msg, $form) {
    return true;
} else {
    throw new Exception('Could not send email.');
}
```

In the notify_password() function, given a username and new password, you simply look up the email address for that user and use PHP's mail() function to send it to the user.

It would be more secure to give users a truly random password—made from any combination of upper and lowercase letters, numbers, and punctuation—rather than the random word and number. However, a password like zigzag48 will be easier for users to read and type than a truly random one. It is often confusing for users to work out whether a character in a random string is 0 or O (zero or capital O), or 1 or l (one or a lowercase L).

On our system, the dictionary file contains about 45,000 words. If a cracker knew we were creating passwords and knew a user's name, he would have to try 22,500,000 passwords on average to guess one. This level of security seems adequate for this type of application even if our users disregard our advice to change their password, since no real personal data is being stored.

However, a better approach to allowing users to reset their passwords would be to send users a link to a password reset page, in which the query string contains a one-time use token that expires after a certain amount of time (24 hours, 72 hours, and so on). This one-time use token would be the "key" that authorizes a user to change his or her password, without having to use a generated password that had been sent in plain text via email.

# Implementing Bookmark Storage and Retrieval

With the user account-related functionality behind you, let's move on and look at how users' bookmarks are stored, retrieved, and deleted.