
              `'username'`  => $\_POST\['username'\],  

              `'password'`  => sha1($\_POST\['password'\]);

`Zend_Db` automatically sanitizes the values before inserting them into the database. The password is the only value that receives special treatment. It’s passed to the `sha1()` function for encryption.

**3.** To insert the data, you need to use the `Zend_Db` object with read/write privileges. Add this line after the array you have just created:

$dbWrite->insert('users', $data);

The first argument to the `insert()` method is a string containing the name of the table you want to use, and the second argument is the data array.

**4.** That’s all there is to inserting the data. After the data is inserted, redirect the user to the login page with the `header()` function like this:

header('Location: login.php');

### ![Image](graphics/note.jpg)**NOTE:**

Strictly speaking, you should use a full URL when redirecting a page, but all current browsers accept a relative URL. Using this shortcut is acceptable for local testing, but you should replace this with a fully qualified URL when deploying your pages on a live site. See [http://docs.php.net/manual/en/function.header.php](http://docs.php.net/manual/en/function.header.php).

**5.** Save user\_registration.php, and copy lesson07/start/login.php to your lesson07/workfiles folder.

**6.** Test add\_user.php to enter a new user in the database. If there are no errors, you will be taken to login.php. You can compare your code with lesson07/completed/scripts/user\_registration.php.

### **Authenticating User Credentials with Zend\_Auth**

The end result of the improved registration form that you just created is the same as Dreamweaver’s built-in Insert Record server behavior—it inserts user details in the database. Dreamweaver’s User Authentication server behaviors can still be used to control access to pages. However, ZF makes it easy to create scripts to authenticate user credentials. Using external files for the scripts that control access and log out users simplifies their inclusion in any page.

#### **Controlling user access with Zend\_Auth**

The `Zend_Auth` class creates a *singleton* object, which means that only one instance can exist at a time. In practical terms, the only difference is that you use `getInstance()` instead of the `new` keyword like this:

$auth = Zend\_Auth::getInstance();

`Zend_Auth` is capable of using a variety of authentication methods. When the user credentials are stored in a database, authentication is done by an adapter called `Zend_Auth_Adapter_DbTable`, which takes the following five arguments:

• A `Zend_Db` object that connects to the database

• The name of the table that contains the user credentials

• The name of the column that contains the username

• The name of the password column

• The encryption, if any, to be applied to the password

The fifth argument uses a question mark as a placeholder for the password. The `users` table uses `sha1()` encryption, so you create an adapter like this:

$adapter = new Zend\_Auth\_Adapter\_DbTable($dbRead, 'users', 'username',  

'password', 'sha1(?)');

When a user logs in, pass the username and password to the adapter like this:

$adapter->setIdentity($\_POST\['username'\]);  

$adapter->setCredential($\_POST\['password'\]);

To check whether the user’s credentials are valid, pass the adapter to the `Zend_Auth` object’s `authenticate()` method:

$result = $auth->authenticate($adapter);

Finally, if the login succeeds, store the user’s details like this:

if ($result->isValid()) {  

  $storage = $auth->getStorage();  

  $storage->write($adapter->getResultRowObject(  

    array('username', 'first\_name', 'family\_name')));  

}

The array passed as an argument to the `getResultRowObject()` method is a list of the database fields you want to store. Dreamweaver’s built-in Log In User server behavior stores only the username and access level, if any. `Zend_Auth` gives you access to as much information about the user as you want—provided, of course, it’s stored in the database.

### ![Image](graphics/note.jpg)**NOTE:**

The `getStorage()` and `write()` methods store the user’s details as a `Zend_Auth_Storage_Session` object, which is essentially just another way of storing session variables.

You restrict access to pages by using the `hasIdentity()` method, which returns `TRUE` if the user has logged in.

To access details of a logged-in user, use the `getIdentity()` method like this:

$auth = Zend\_Auth::getInstance();  

if ($auth->hasIdentity()) {  

  $identity = $auth->getIdentity();  

}

The details can then be accessed as properties of `$identity`, for example:

$identity->first\_name

To log out a visitor, use the `clearIdentity()` method.

#### **Creating the login script**

The Log In User server behavior that you used in [Lesson 6](#ch06.html#ch06) sends the user to another page on failure or displays the login form again without explanation. This time you’ll display an error message so the user knows what’s happened.

**1.** Create a new PHP page, and save it as **user\_authentication.php** in lesson07/workfiles/scripts. The page will contain only PHP code, so delete the HTML inserted by Dreamweaver, and add an opening PHP tag.

**2.** To control the error message, create a `FALSE` Boolean variable:

$failed = FALSE;

If the login fails, this will be reset to `TRUE` and display the message.

**3.** The login script should run only if the form is submitted. Add a conditional statement to include library.php if the `$_POST` array equates to `TRUE`:

if ($\_POST) {  

  require\_once('library.php');  

  // check the user's credentials  

}

**4** The script uses objects, so add `try` and `catch` blocks inside the conditional statement, and get an instance of `Zend_Auth` in the `try` block.

try {  

  $auth = Zend\_Auth::getInstance();  

} catch (Exception $e) {  

  echo $e->getMessage();  

}

### ![Image](graphics/tip.jpg)**TIP:**

A quick way to select the code hint for Zend\_Auth is to press Ctrl+spacebar, and type **dau**. This selects `Zend_Auth` immediately. Press Enter/Return to insert it, and then type two colons to bring up a code hint for `getInstance()`.

The rest of the script goes inside the `try` block.

**5.** Create a `Zend_Auth_Adapter_DbTable` object. A quick way to select its code hint is by typing **hada** after the `new` keyword. This takes five arguments, but Dreamweaver helps you by highlighting the current argument in bold.

![Image](graphics/fig07_27.jpg)

The code for this line should look like this:

$adapter = new Zend\_Auth\_Adapter\_DbTable($dbRead, 'users', 'username', 'password', 'sha1(?)');

**6.** Set the identity and credential values for the adapter. They come from the `username` and `password` values in the `$_POST` array:

$adapter->setIdentity($\_POST\['username'\]);  

$adapter->setCredential($\_POST\['password'\]);

**7.** Pass the adapter to the `authenticate()` method of the `Zend_Auth` object, and save the result in a variable:

$result = $auth->authenticate($adapter);

**8.** Use the `isValid()` method to determine whether the user’s credentials are correct. If they are, store the details, and use `header()` to redirect the user to members_only.php. If the login attempt fails, reset `$failed` to `TRUE`. The code looks like this:

if ($result->isValid()) {  

  $storage = $auth->getStorage();  

  $storage->write($adapter->getResultRowObject(array(  

    'username', 'first\_name', 'family\_name')));  

  header('Location: members\_only.php');  

  exit;  

} else {  

  $failed = TRUE;  

}

### ![Image](graphics/caution.jpg)**CAUTION!**
