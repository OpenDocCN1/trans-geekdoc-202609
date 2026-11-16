Show suggested code

# Step 2

Create a GET /account/view route which maps to a new accountView handler. The route should be restricted to authenticated users only.

Show suggested code

# Step 3

Update the accountView handler to get the "authenticatedUserID" from the session, fetch the details of the relevant user from the database (using the new UserModel.Get() method), and dump them out in a plain text HTTP response. If no user matching the "authenticatedUserID" from the session could be found, redirect the client to GET /user/login to force re-authentication.

When you visit https://localhost:4000/account/view in your browser as an authenticated user, you should get a response similar to this:

![](bbox=[0.112, 0.47, 0.885, 0.84])

Show suggested code