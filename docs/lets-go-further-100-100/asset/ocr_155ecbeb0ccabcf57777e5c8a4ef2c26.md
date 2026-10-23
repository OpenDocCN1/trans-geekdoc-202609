| Method | URL Pattern | Handler | Action |
|---|---|---|---|
| POST | /v1/users | registerUserHandler | Register a new user |
| PUT | /v1/users/activated | activateUserHandler | Activate a specific user |

And the workflow will look like this:

+   1. The user submits the plaintext activation token (which they just received in their email) to the `PUT /v1/users/activated` endpoint.
+   2. We validate the plaintext token to check that it matches the expected format, sending the client an error message if necessary.
+   3. We then call the `UserModel.GetForToken()` method to retrieve the details of the user associated with the provided token. If there is no matching token found, or it has expired, we send the client an error message.
+   4. We activate the associated user by setting `activated = true` on the user record and update it in our database.
+   5. We delete all activation tokens for the user from the `tokens` table. We can do this using the `TokenModel.DeleteAllForUser()` method that we made earlier.
+   6. We send the updated user details in a JSON response.

Let’s begin in our `cmd/api/users.go` file and create the new `activateUserHandler` to work through these steps:

```
File: cmd/api/users.go
```