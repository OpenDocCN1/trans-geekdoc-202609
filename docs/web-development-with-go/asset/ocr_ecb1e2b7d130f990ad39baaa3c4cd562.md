# CHAPTER 11. REMEMBERING USERS

While this in itself isn’t a security concern, what it implies is that we don’t have ownership of the cookie. In other words, the end user has the freedom to edit those cookies and we can’t do anything to stop them. This is known as cookie tampering.

Editing cookies stored on your computer is actually pretty easy to do, and there are several Chrome extensions that will allow you to do just that. Take Edit-ThisCookie for example - after installing this extension you could update the email address stored in your cookie in a matter of seconds.

If you are thinking “that doesn’t sound very secure...” then you are absolutely correct. As a general rule, all data stored in cookies shouldn’t be trusted unless you have done something to make it trustworthy.

One way to do this is to store a digital signature of all of the data that you store in a cookie. The detail of how you can do this from case to case, but the general idea is always the same. Let’s imagine that you wanted to store the following data in a cookie.

```
{
  "id": 123,
  "email": "jon@calhoun.io"
n}
```

If all we decided to store, it would be pretty easy for an end user to alter the id or email and start accessing your website as another user. We don’t currently have any way to validate the data that we originally set in the cookie.

One way to solve this problem is to create a signature to also attach to the cookie using a hashing function like HMAC. What makes this hashing function ideal is that it requires both a secret key and data to be hashed, and the output of the hashing function changes if either of these changes. A few examples of this are shown below; You don’t need to worry about coding this, but look at how changing either of the secret key or the data being hashed will alter the resulting hash value.