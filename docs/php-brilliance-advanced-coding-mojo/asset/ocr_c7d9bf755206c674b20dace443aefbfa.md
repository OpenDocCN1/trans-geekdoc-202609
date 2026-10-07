# Ghostbusters 214

Furthermore, if all that we have done is put the entire process behind a method call then we're actually limiting ourselves to an all or nothing approach. We throw all of the necessary data to the method; if it works, that's great. If it doesn't, then what? Try it all again?

Even without a functioning crystal ball, we can be reasonably certain that at least one of our users will welcome email sending again, particularly if we're asking them to verify their email address in order to activate their account.

With this in mind, we can at least ascertain that we need to break the process down into two parts. Additionally, since we've already considered that these doers are in fact service candidates, then it's going to be entirely reasonable for us to ask Lizzie to implement the two processes as method calls on appropriately service classes.

This might lead us to something looking like this.

```
<?php
class UserRegistration
{
    public function addUser(array $data)
    {
        $userService = new UserService();
        $user = $userService->addUser($data);

        if($instanceof User {
            $emailService = new EmailService();
            $emailService->send($user, 'welcome.email.tpl');
        }
    }
}
```

Apppletely, we now have UserService and EmailService classes. Great.

However, if a poltergeist is generalised by an object that carries little or no internal state and whose apparent purpose is merely to trigger method calls on other system objects, then this is exactly what we have here.

Admittedly, this is a highly contrived route that we've taken in order to arrive at a poltergeist but it's actually not uncommon for our less experienced brethren to simply embody sequence of button pushes into an object that appears to 'automate' things for us. Crafting an object with the explicit intent of automating a