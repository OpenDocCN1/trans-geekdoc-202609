Therefore, a username has to be compared without considering case sensitivity. This can be done either by using `strcasecmp()`—see the previous phrase—or by first converting both the provided password and the real password into lower-case letters (or uppercase letters). This is done by the functions `strtolower()` or `strtoupper()`. The preceding code shows an example using `strcmp()`/`strcasecmp()` and also the compare operator `==`.

Depending on the data provided in the uniform resource locator (URL) of the call to the script, the login either fails or succeeds. For instance, the following URL successfully logs in the user. (You have to change the *servername* portion.)

```
```text
http://servername/comparelogin.php
↪?user=CHRISTIAN&pass=topsecret
```
```

In contrast, the following login does fail:

```
```text
http://servername/comparelogin.php
↪?user=Christian&pass=TopSecret
```
```

**NOTE:** Of course, providing usernames and passwords via GET is a very bad idea; POST is preferred. (See Chapter 4, “Interacting with Web Forms,” for more details on form data.) However, for testing purposes, this chapter’s code uses GET.