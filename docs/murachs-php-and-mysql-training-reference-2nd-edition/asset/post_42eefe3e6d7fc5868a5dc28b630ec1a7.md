
## The Field and Fields classes (model/fields.php)

```php
<?php
class Field {
    private $name;
    private $message = '';
    private $hasError = false;

    public function __construct($name, $message = '') {
        $this->name = $name;
        $this->message = $message;
    }
    public function getName()    { return $this->name; }
    public function getMessage() { return $this->message; }
    public function hasError()   { return $this->hasError; }

    public function setErrorMessage($message) {
        $this->message = $message;
        $this->hasError = true;
    }
    public function clearErrorMessage() {
        $this->message = '';
        $this->hasError = false;
    }

    public function getHTML() {
        $message = htmlspecialchars($this->message);
        if ($this->hasError()) {
            return '<span class="error">' . $message . '</span>';
        } else {
            return '<span>' . $message . '</span>';
        }
    }
}

class Fields {
    private $fields = array();

    public function addField($name, $message = '') {
        $field = new Field($name, $message);
        $this->fields[$field->getName()] = $field;
    }

    public function getField($name) {
        return $this->fields[$name];
    }

    public function hasErrors() {
        foreach ($this->fields as $field) {
            if ($field->hasError()) { return true; }
        }
        return false;
    }
}
?>
```

Figure 15-11   The Registration application (part 2 of 7)

## The Validate class (model/validate.php)

```php
<?php
class Validate {
    private $fields;

    public function __construct() {
        $this->fields = new Fields();
    }

    public function getFields() {
        return $this->fields;
    }

    // Validate a generic text field
    public function text($name, $value,
            $required = true, $min = 1, $max = 255) {

        // Get Field object
        $field = $this->fields->getField($name);

        // If field is not required and empty, remove error and exit
        if (!$required && empty($value)) {
            $field->clearErrorMessage();
            return;
        }

        // Check field and set or clear error message
        if ($required && empty($value)) {
            $field->setErrorMessage('Required.');
        } else if (strlen($value) < $min) {
            $field->setErrorMessage('Too short.');
        } else if (strlen($value) > $max) {
            $field->setErrorMessage('Too long.');
        } else {
            $field->clearErrorMessage();
        }
    }

    // Validate a field with a generic pattern
    public function pattern($name, $value, $pattern, $message,
            $required = true) {

        // Get field object
        $field = $this->fields->getField($name);

        // If field is not required and empty, remove errors and exit
        if (!$required && empty($value)) {
            $field->clearErrorMessage();
            return;
        }

        // Check field and set or clear error message
        $match = preg_match($pattern, $value);
        if ($match === false) {
            $field->setErrorMessage('Error testing field.');
        } else if ( $match != 1 ) {
            $field->setErrorMessage($message);
        } else {
            $field->clearErrorMessage();
        }
    }

    public function phone($name, $value, $required = false) {
        $field = $this->fields->getField($name);

        // Call the text method and exit if it yields an error
        $this->text($name, $value, $required);
        if ($field->hasError()) { return; }

        // Call the pattern method to validate a phone number
        $pattern = '/^[[:digit:]]{3}-[[:digit:]]{3}-[[:digit:]]{4}$/';
        $message = 'Invalid phone number.';
        $this->pattern($name, $value, $pattern, $message, $required);
    }

    public function email($name, $value, $required = true) {
        $field = $this->fields->getField($name);

        // If field is not required and empty, remove errors and exit
        if (!$required && empty($value)) {
            $field->clearErrorMessage();
            return;
        }

        // Call the text method and exit if it yields an error
        $this->text($name, $value, $required);
        if ($field->hasError()) { return; }
```

After doing the preliminary field checks, this code splits the email address into its *local* and *domain* parts. If there are not two parts or either of the parts is too long, it sets an appropriate error message in the Field object. Otherwise, it uses regular expressions to test each part for validity.

According to the SMTP specification, the local part of an email address can be in one of two formats: an *address format* or a *quoted text format*. Of these two formats, the address format is the format that’s almost always used. Although the quoted text format is rarely if ever used, it is still potentially valid. As a result, you should validate it or you run the risk of blocking a valid email address.

The address format starts with an *atom*, which is a letter, number, or one of 19 symbols (!#$%&'*+-/=?^_\`{|}~). After that, an atom may be followed by other atoms. Or, an atom may be followed by zero or more atoms that are preceded by a dot. In other words, the address format can contain letters, numbers, and some symbols. However, it can’t begin or end with a dot or have two consecutive dots. For example, “ray.harris” would be valid, but “ray..harris” or “ray.” would not be valid.

The quoted text format contains text surrounded by double quotes. The text can contain any characters, but the double quote and backslash must be preceded by a backslash. For example, “Ray Harris” and “Ray\\Harris” are valid but “Ray\Harris” is invalid. In this code, the `$char` pattern matches any character that is not a backslash or double quote, and the `$esc` pattern matches either the `\\` or `\"` escaped characters. As a result, the `$text` pattern matches any character or the escaped backslash or double quote, and the `$quoted` pattern is the `$text` pattern surrounded by double quotes.

The final pattern for the local part is a choice of either the address format or the quoted text format. Next, this code uses the pattern method to validate the local part of the email address against the pattern. If the local part is not valid, it sets an appropriate error message in the Field object and exits the method.

The domain part consists of one or more *host names* followed by a *top level domain*. A host name can have up to 64 letters, numbers, or hyphens, but can’t start or end with a hyphen. The `$hostname` pattern matches a beginning alphanumeric character followed by an optional subpattern of up to 62 hyphens and alphanumeric characters with an ending alphanumeric character. This gives a total possible range of 1 to 64 characters.

When an email address has multiple host names, they must be separated by a dot. That’s why the `$hostnames` pattern matches a `$hostname` pattern followed by zero or more host names that are preceded by a dot. Finally, the top level domain can have two to six letters or numbers and must be preceded by a dot.

The final pattern for the domain part is one or more hostnames followed by a top level domain. Next, this code uses the pattern method to validate the domain part of the email address. If the domain part is not valid, the pattern method sets an appropriate error message in the Field object. However, if the domain part is valid, the pattern method clears the error message from the Field object. As a result, the email address for the field is valid.

## The controller

Part 6 presents the controller for the Registration application that’s stored in the index.php file. This code checks all data entered on the registration page to see if it’s valid.

The code for the controller begins by loading the fields.php and validate.php files that contain the classes. Then, it creates a new Validate object and stores it in the $validate variable. Next, it stores a reference to the Fields object in the $fields variable.

After getting the Fields object from the Validate object, this code uses the addField method to add a field for each of the fields in the form. This code gives a default message to the phone and email fields. As a result, when the browser loads the form for the first time, these messages are displayed to the user.

After setting up the fields, the code checks whether a field named action exists in the global $_POST array. If not, it sets the $action variable to a default value of “reset”. Otherwise, this code copies the action to a local variable named $action. But first, it uses the strtolower function to convert the action string to all lowercase letters.

After getting the action, this code uses a switch statement to execute the appropriate code based on the current action. If the action is reset, this code resets the values for the variables and displays the registration page using the default values for the fields.

If the action is register, the code copies the data for the form fields to local variables using the trim function to remove any leading or trailing spaces. Then, it uses the text, phone, and email methods of the Validate object to validate each of the form fields.

After validation, this code uses the hasErrors method of the Validate object to check whether any of the fields has an error. If so, it displays the registration page again. Otherwise, it displays a page that indicates that the data was successfully entered.

Note that the calls to the text, email, and phone methods don’t provide a value for the optional third argument that specifies whether the field is required. As a result, these fields use the default values provided by the methods. This means that the phone number field isn’t required, but the other three fields are required. If you want to change the default value, of course, you can specify the third argument. For example, to require the phone number field, you can specify the third parameter like this:

```php
$validate->phone('phone', $phone, true);  // require phone field
```
