
# Ghostbusters

// inside controller

```php
if ($_POST['accept_terms']) {
  $user = new User();
  $user->setEmail($_POST['email']);
  $user->setPassword($_POST['password']);

  if ($user->save()) {
    $email = new Email();
    $email->setSubject('Please verify..');

    if ($email->send()) {
      $this->flashMsg('Congrats');
      $this->redirect('/login.php');
    } else {
      // something about failed email
    }
  } else {
    // something about failed user save
  }
}
```

Looks familiar? I know many PHP developers who have done this sort of thing once in their coding careers, when the registration process involves more steps than simply creating a user record and sending an email. We have already seen how this kind of data mangling inside a controller method leads to duplicated code; an entirely avoidable situation.

What would Lizzie do? Her first attempt might be to encapsulate the entire process into a single object, giving a rise to a controller method that looks more like this.

// inside controller

```php
$accepted = filter_input(INPUT_POST, 'accept_terms');
if ($accepted) {
  $reg = new UserRegistration();
  if ($reg->addUser($_POST)) {
    $this->flashMsg('Congrats');
    $this->redirect('/login.php');
  } else {
    $errors = $reg->getErrors();
    // show errors
  }
}
```

# Ghostbusters 213

From the perspective of our controller, this is a vast improvement. Instead of being cluttered with lots of messy ifs, some of which are even nested, we now have a single call to the addUser() method on our UserRegistration instance.

The assumption there then is that the UserRegistration object co-ordinates the entire process of validating user data, hashing the password, creating the user record and any related rows and finally sending that to email.

At first glance, this looks entirely satisfactory. After all, what we have now is an object that we only need to throw an appropriately structured array of data in order to get a user account created and the end result is a leaner, much more succinct controller. Better yet, we seem to be honouring the “Tell, Don’t Ask” principle even though we haven’t read about that yet.

So, a step in the right direction but have we finished this particular journey yet? It depends on UserRegistration class and its addUser() method. If all has happened that we’ve moved those nested ifs into a method, we really haven’t achieved anything.

```php
<?php
class UserRegistration
{
    public function addUser(array $data) {
        $user = new User();
        $user->setEmail($data['email']);

        if ($user->save()) {
            $email = new Email();
            $email->setSubject('Please verify...');

            if ($email->send()) {
                return true;
            } else {
                return false;
            }
        } else {
            return false;
        }
    }
}
```

# Ghostbusters 214

Furthermore, if all that we have done is put the entire process behind a method call then we're actually limiting ourselves to an all or nothing approach. We throw all of the necessary data to the method; if it works, that's great. If it doesn't, then what? Try it all again?

Even without a functioning crystal ball, we can be reasonably certain that at least one of our users will welcome email sending again, particularly if we're asking them to verify their email address in order to activate their account.

With this in mind, we can at least ascertain that we need to break the process down into two parts. Additionally, since we've already considered that these doers are in fact service candidates, then it's going to be entirely reasonable for us to ask Lizzie to implement the two processes as method calls on appropriately service classes.

This might lead us to something looking like this.

```php
<?php
class UserRegistration
{
    public function addUser(array $data)
    {
        $userService = new UserService();
        $user = $userService->addUser($data);

        if($instance instanceof User) {
            $emailService = new EmailService();
            $emailService->send($user, 'welcome.email.tpl');
        }
    }
}
```

Completely, we now have UserService and EmailService classes. Great.

However, if a poltergeist is generalised by an object that carries little or no internal state and whose apparent purpose is merely to trigger method calls on other system objects, then this is exactly what we have here.

Admittedly, this is a highly contrived route that we've taken in order to arrive at a poltergeist but it's actually not uncommon for our less experienced brethren to simply embody sequence of button pushes into an object that appears to 'automate' things for us. Crafting an object with the explicit intent of automating a

# Ghostbusters 215

complicated process seems like a perfectly valid approach but if object brings nothing of its own to the table, the chances are all be a poltergeist.

Fortunately, fixing the code that we have is quite simple and straightforward. Like any instance of the Poltergeist anti-pattern, it can be banished by refactoring the logic out of the body of the beast and into the caller or the callee. This is an enduring characteristic of the Poltergeist - the fact that they have no real substance of their own is evident in their behaviour as some sort of bridge between a piece of code that needs something doing and the target code that will do what is required.

Banishing our poltergeist here is simply a matter of moving those service back to the controller. The services themselves are providing the actual functionality that is needed, we just need outlet to push the buttons instead.

```php
// inside controller
```

```php
$accepted = filter_input(INPUT_POST, 'accept_terms');
if ($accepted) {
    $userService = new UserService();
    $emailService = new EmailService();
    try {
        $user = $userService->addUser($user);
        $emailService->send($user, 'welcome.email.tpl');
        $this->flashMsg('Congrats!');
        $this->redirect('/login.php');
    } catch (UserService $use) {
        // Error handling
    } catch (EmailService $ese) {
        // Error handling
    } catch (Exception $e) {
        // Unknown error handling
    }
}
```

With these changes in place our poltergeist has been exorcised from our code base, allowing us to delete the UserRegistration class quite safely. Furthermore, the addition of the two service classes provides us with easy access to the two discrete processes of creating accounts and sending welcome emails.

This is significant in a number of ways.

# Ghostbusters 216

Decoupling the account creation process from the controller makes it possible to create users outside of the web context. What would be the benefit of this? If we are rolling this out to a large organisation, or we have to migrate users from a legacy application to our shiny new one, the ability to create user accounts in bulk is going to prove most advantageous to us. Generating user accounts from an uploaded CSV file makes it cinch.

The benefit of providing an independent email service should be immediately apparent. Nevertheless, now that it has been separated from the process of account creation will mean that we will have the opportunity to send a different email template to user accounts that were created in bulk - one that is eminently more appropriate. Further, for the singular web user, we can offer the facility to remain the welcome email independently of the form post that created their account in the first place.

Even though we have to look at the "Tell, Don't Ask" principle (that is coming up shortly) the elimination of this particular poltergeist led to us satisfying that principle's requirements. This is not an uncommon side effect of poltergeist elimination and as such, we will be returning to our controller/service example again shortly.

These are:

- Transient and stateless objects
- Single operation classes that are used only to trigger other operations or sequences of operations.
- Temporary, short-lived objects that provide only control-like operations.
