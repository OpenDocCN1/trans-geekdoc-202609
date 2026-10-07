# Ghostbusters 215

complicated process seems like a perfectly valid approach but if object brings nothing of its own to the table, the chances are'll be a poltergeist.

Fortunately, fixing the code that we have is quite simple and straightforward. Like any instance of the Poltergeist anti-pattern, it can be banished by refactoring the logic out of the body of the beast and into the caller or the callee. This is an enduring characteristic of the Poltergeist - the fact that they have no real substance of their own is evident in their behaviour as some sort of bridge between a piece of code that needs something doing and the target code that will do what is required.

Banishing our poltergeist here is simply a matter of moving those service back back the controller. The services themselves are providing the actual functionality that is needed, we just need outlet to push the buttons instead.

```
// inside controller
```

```
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
```

With these changes in place our poltergeist has been exorcised from our code base, allowing us to delete the UserRegistration class quite safely. Furthermore, the addition of the two service classes provides us with easy access to the two discrete processes of creating user accounts and sending the welcome/verification emails.

This is significant in a number of ways.