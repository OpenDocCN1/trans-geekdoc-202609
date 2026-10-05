# CHAPTER 9. CREATING THE USER MODEL

```
type Signup struct {
  Name     string `schema:"name"
  Email    string `schema:"email"
  Password string `schema:"password"
}
```

You can also update your Create handler in the users controller to print out the name to ensure it is being parsed correctly.

```
fmt.Fprintln(w, "Name is", form.Name)
```

Restart your server and verify that this all works before proceeding.

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/9.7.1

Changes - book.usegolang.com/9.7.1-diff

# 9.7.2 Setting up a user service in our web application

Our next step is to setting up a user service when our application starts so that we can provide this service to any parts of our web application that need it.

While it might be tempting to push this logic off to the pieces that need a user service, doing so would have a few repercussions. For starters, several pieces of code would need to know how to construct a Postgres connection string,