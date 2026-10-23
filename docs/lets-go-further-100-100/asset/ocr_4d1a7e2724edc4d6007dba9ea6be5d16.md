# Creating Email Templates

To start with, we’ll keep the content of the welcome email really simple, with a short message to let the user know that their registration was successful and confirmation of their ID number. Similar to this:

```
Hi,

Thanks for signing up for a Greenlight account. We're excited to have you on board!

For future reference, your user ID number is 123.

Thanks,

The Greenlight Team
```

**Note:** Including the user ID probably isn’t something you’d normally do in a welcome email, but it’s a simple way for us to demonstrate how to include *dynamic data* in emails — rather than just static content.

There are several different approaches we could take to define and manage the content for this email, but a convenient and flexible way