At first pass it's reasonable to say the design isn't so bad. It only has 2 dependencies!

Re-evaluate the design by considering the handler's responsibilities:

+   - Parse the request body into a `User` ✔
+   - Use `UserStore` to check if the user exists ?
+   - Use `UserStore` to store the user ?
+   - Compose an email ?
+   - Use `Emailer` to send the email ?
+   - Return an appropriate http response, depending on success, errors, etc ✔

To exercise this code, you're going to have to write many tests with varying degrees of test double setups, spies, etc

+   - What if the requirements expand? Translations for the emails? Sending an SMS confirmation too? Does it make sense to you that you have to change a HTTP handler to accommodate this change?
+   - Does it feel right that the important rule of "we should send an email" resides within a HTTP handler?
+     - Why do you have to go through the ceremony of creating HTTP requests and reading responses to verify that rule?

**Listen to your tests.** Writing tests for this code in a TDD fashion should quickly make you feel uncomfortable (or at least, make the lazy developer in you be annoyed). If it feels painful, stop and think.

What if the design was like this instead?

```
type UserService interface {
    Register(newUser User) error
}
```

```
func NewRegistrationHandler(userService UserService) http.Handle
    return func(writer http.ResponseWriter, request *http.Reques
        // parse user
```