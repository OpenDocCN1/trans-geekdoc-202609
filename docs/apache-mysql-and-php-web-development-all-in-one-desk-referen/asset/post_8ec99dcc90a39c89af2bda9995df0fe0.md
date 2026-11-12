

}
mysql_free_result($result);
}
mysql_close();
return $themeByNum;
}

```php
function GeneratePassword() {
// skip the L's since they look like 1's!
$wordlist = array("apple", "array", "book",
"bold", "catalog", "cook", "door", "down",
"echo", "eat", "flag", "funny", "garage",
"going", "house", "heavy", "inside",
"icecream", "jump", "jack", "kludge", "keep",
"merry", "making", "need", "next", "other",
"open", "perfect", "place", "quite", "quick",
"rest", "read", "taking", "tophat", "under",
"upside", "video", "vanish", "wane", "wipe");
$firstword = $wordlist[rand(0,
count($wordlist) - 1)];
$secondword = $wordlist[rand(0,
count($wordlist) - 1)];
$number = rand(10,99);
$newpass = $firstword.$number.$secondword;
return $newpass;
}
// Important: Do not put any blank lines
// After the closing ?> in this file!
?>
```

![](img/3f967ab8a8fddc723173059f56621648_618_0.png)

If you're not careful when entering Listing 7-7, you could easily run into a problem that is a nightmare to track down. *Don't put any blank lines at the end of your useraccess.php file.* Make sure there are no newlines after the closing `?>`. The reason for this is that when these blank lines are included they are sent to the browser as text. But this `useraccess.php` file gets processed during the HTML headers. If you send blank text lines, the browser gets very confused. Therefore, don't let any blank lines creep into this file!

## Logging in with the checkAccess function

The checkAccess function is a multipurpose function that performs the following operations:

- Checks whether a user is already logged in
- Logs the user in if he or she isn't logged in already
- Uses the results of the `login.html` form if present for the login; otherwise, uses cookies so the user doesn't have to keep logging in
- Saves the user login information for the entire session (or long term if the user chose the Remember Me check box in the login form)
- Sends the user to the logininfailed.html page if the user provides incorrect login information

The goal behind this function is to allow you to put a call in to this function at the beginning of any private page, and PHP will take care of the rest. You can see how I did that earlier in this chapter in Listing 7-5, which is the welcome.php page.

The first thing this function does is look for the e-mail and password in the $_POST array. If the page that calls this function (welcome.php, for example) was arrived at via the login.html page, the $_POST array will contain the information the user typed into the form.

If the $_POST array doesn't have the e-mail and password information, this function checks the user's cookies for the information.

If an e-mail address and password are located (and if the user got here via the login.html page and did not check the Remember Me box), the e-mail address and password are saved in a session cookie. That way, if the user visits other protected pages without closing the Web browser, he or she doesn't have to go through the login process again. (How is this possible? More semicircular reasoning is required here: Because the e-mail address and password were saved to a session cookie, the next time this checkAccess function gets called, the cookies will be set, and the part that checks the cookies for e-mail and password information will work.)

Also if an e-mail address and password are located, the page verifies the information against the login table within MySQL. This gives the illusion of being logged into the system, when, in fact, each time the user accesses a private page, the system simply verifies that the user is allowed to see the page. There is no “logging in” taking place, even though the user feels like there is.

If the login cannot be verified, or if no e-mail address and password are present, the code sends the user to the logininfailed.html page, by setting a header as follows:

```
header("location: logininfailed.html");
```

Because you're calling a header function, you can only use this checkAccess function at the beginning of a .php file, before the initial <html> tag and before calling any PHP print or echo statements. You can see that I followed this rule in the welcome.php page earlier in Listing 7-5.

![](img/3f967ab8a8fddc723173059f56621648_619_0.png)

## Dealing with encryption troubles

I tested the sample system in this chapter on a Windows XP system and a Linux system, both running Apache. And I found something bizarre: the crypt function behaved differently on each computer. As it turns out, this difference is related to how Apache was configured for each operating system.

If you see the same output each time you run it, your system is using DES encryption. If you see a different output each time, your system is using MD5 encryption. (It's not that MD5 encrypts differently each time; rather with MD5, the PHP system randomly generates a salt each time. Different salts cause the MD5 algorithm to behave differently, resulting in a different encryption.)

The problem is that the crypt function has different ways of choosing which encryption technique to use. (The two most common encryption techniques are DES, which stands for Data Encryption Standard, and MD5, which stands for Message Digest version 5.)

- 2. Next, look at the output and count the number of characters in the random string.

Two factors are important here: how big you make the password field of your login table and how you handle password comparisons after the user types in the password. Both factors are related to what type of encryption is used.

This is how long you need to make the password column of your login table.

- 3. If the output from the little test program showed the same value each time, then use this line to encrypt your passwords:

```
$passcrypt = crypt($password);
```

Here's a test program you can use to find out which encryption technique you're using:

- 4. If the output from the little test program showed different values each time, then use this line to encrypt your passwords, which extracts the salt that was used when the user registered, and forces the MD5 algorithm to use that same salt.

```php
<?php
print crypt("test");
print "\n";
?>
```

```
$passcrypt = crypt($password,
substr($pass, 0, 12));
```

Follow these steps to find your encryption technique:

- 1. Save this file as crypttest.php and run it several times at the prompt on your Web server using php crypttest.php.

Finally, if the user came to this page via the login.html page, and that user checked the Remember Me box, the e-mail address and password are saved in a long-term cookie. The expiration date is set to Unix date 2000000000, which corresponds to sometime on May 17, 2033, less than 30 years from the publication of this book. (If you're reading this on May 18, 2033, too bad — although for me, it would be cool if this book were still going strong after 30 years.)

Now here are some final points about the cookies. If you save the long-term cookie, you may realize that the cookie will get rewritten the next time the user logs in. This is not a problem for a couple reasons:

- If it’s the same user logging in, the cookie’s expiration date will not change because the data in the cookie doesn’t change.
- If a different user logs in, that user’s information is saved as a session cookie (not long term unless the user checks the Remember Me box), and that new cookie information overwrites the previous cookie. In other words, everything works out as you want it to.

In addition to using cookies, PHP includes a sophisticated mechanism for handling *sessions*. This mechanism keeps track of user information during a single browser session using cookies and other devices, much like I do in these examples. If you want to explore the PHP session-handling mechanism, check out www.php.net/session.

## Signing up with the signup function

The signup function is simple. It doesn’t do any checking; it just enters the user information into the login table.

This function takes an unencrypted password as a parameter and encrypts the password before saving it to the database. You want to make sure, however, that you use the correct encryption approach for your particular PHP installation. Take a look at the sidebar, “Dealing with encryption troubles” for more information on this.

## Obtaining theme info

The useraccess.php file (refer to Listing 7-7) contains three items dealing with themes:

- The ThemeInfo class
- The getTheme function
- The getThemeNames function

The ThemeInfo class for now has only one member, $bgcolor. For this example, I could just use a background color and not bother creating a ThemeInfo class. However, I want to provide you with a starting point whereby you can add additional theme information beyond just a background color. Thus, I create the ThemeInfo class.

