username and password for testing purposes. Ideally, in a real-life scenario, we would query a database to verify the authenticity of the information provided by the user.

# # Starting and storing session data

```
```php
<?php
// Basic username and password for tests
$valid_username = "toto";
$valid_password = "azerty123";

// Check if form data has been sent
if (isset($_POST['username']) && isset($_POST['password'])) {
// Check that username and password are correct
if ($valid_username == $_POST['username'] && $valid_password == $_POST['password']) {
// Start session
session_start();

// Save session parameters
$_SESSION['username'] = $_POST['username'];
$_SESSION['password'] = $_POST['password'];

// Display a welcome message and a link to the members' area
echo "Logged in as " . $_SESSION['username'] . "<br />";
echo 'You can access the members\' area: <a href="members.php">Link to members\' page</a>';
```
```