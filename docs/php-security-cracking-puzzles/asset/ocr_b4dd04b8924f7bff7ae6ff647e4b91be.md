```
}
else {
  // Automatic redirection to the
  // authorization page
  echo "<HTML><HEAD>
    <META HTTP-EQUIV='Refresh' CONTENT='0; URL=1.php'>n  </HEAD></HTML>";
}
```

How is possible to bypass the authorization system shown in Listings I.7.2 and I.7.3? How would you protect the authorization system to make it impossible to bypass?

# I.7.8. Protecting User Names

Even if there no possibility of discovering the user password or bypassing the authorization system to obtain access to the user account, it is possible to discredit an existing user by forging his or her name. A name is forged by replacing English letters with characters of national alphabets, or vice versa, that are similar in appearance. For instance, assume that the cheops are made up of English letters. In this case, it is enough to register the same name but replace the English letter with its equivalent from another language (in Cyrillics, for example) and carry out malicious activity, such as flooding or spam, on behalf of that user, discredit a lawful individual with the site's administration. This forgery might make the site's administrators nervous, causing them to worry and search for nonexistent security holes if they do not notice the forgery. Develop an algorithm that would check user registration and eliminate the possibility of forged user names.

# I.7.9. Session-Based Authorization

Cookies are convenient Web developers can easily specify their lifetime. However, they are easy to forge, and they can be disabled in the browser settings. Therefore, most Web developers use authorization based on sessions. Such authorization systems provide stronger security, because the data do not leave the server and the client machine exchanges information with the server only by