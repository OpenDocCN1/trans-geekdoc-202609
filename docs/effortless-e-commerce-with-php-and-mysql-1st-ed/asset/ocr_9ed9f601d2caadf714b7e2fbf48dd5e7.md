more secure to store. And the third will redirect the browser should the user not meet the requirements for accessing a particular page.

There are a few benefits to using these custom functions:

+   Keeps complex logic from cluttering up other code

+   Allows the same logic to be used in multiple scripts

+   Makes changes to the logic a snap

The last two are really the key points: If you separate out processes, they can be used by different parts of a site without having to repeat the code. And if you later decide you need to tweak the process, you can do so in one place.

# Creating Form Inputs

The functionality provided by the scripts in this chapter is almost entirely form-based: The user must complete a registration, login, change password, or forgot password form. All these forms use just two types of form inputs — text and password (not counting the submit buttons). An input starts off with this simple HTML:

```
<input type="type" name="name" id="name" />
```

For example:

```
<input type="text" name="username" id="username" />
```

In cases where the form was submitted but not properly completed, the user will be presented with the form again. As a convenience, the form should remember the entered values (that is, it should be sticky). To achieve that effect, you need to add value="whatever value" to each input. In PHP code, that would be:

```
<input type="text" name="username" id="username" value="<?php echo $_POST['username']; ?>" />
```

However, the first time the form is loaded, $_POST['username'] won't be set, so the code should really be:

```
<input type="text" name="username" id="username" value="<?php if (isset($_POST['username'])) echo $_POST['username']; ?>" />
```

You can add sizes to the inputs, if you want. I chose not to size them, so they would all be equally sized to the browser's default.