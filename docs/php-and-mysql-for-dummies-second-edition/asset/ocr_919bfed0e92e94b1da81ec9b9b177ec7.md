The customer controls what happens next. If the customer clicks the button to return to the main page, the PetShopFront.php programs runs. If the customer clicks the Members Only Section submit button, the first page of the Members Only section is shown.

# Writing the Members Only section

The Web pages in the Members Only section are no different than any other Web pages. You just want to restrict them to members who are logged in. To do this, you start a session and check whether they’re logged in at the top of every page. The statements for the top of each program are

```
session_start();
if (@$_SESSION['auth'] != "yes")
{
    header("Location: Login.php");
    exit();
}
```

When session_start executes, PHP checks for an existing session. If one exists, it sets up the session variables. One of the session variables is $auth. When the user logs in, $_SESSION[auth] is set to yes. If $_SESSION[auth] doesn’t equal yes, the user is not logged in, and the program takes the user to the login page.

# Planning for Growth

The original plan for an application usually includes every wonderful thing that the user might want it to do. Realistically, it’s usually important to make the application available to the users as quickly as possible. Consequently, applications usually go public with a subset of the planned functionality. More functionality is added later. That’s why it’s important to write your application with future growth in mind.

Looking at the login application in this chapter, I’m sure you can see many things that could be added to it. Here are some possibilities:

+   - **E-mail a forgotten password.** Users often forget their passwords. Many login applications have a link that users can click to have their passwords e-mailed to them.
+   - **Change the password.** Members might want to change their password. The application could offer a form for password changes.