
$val = new Zend_Validate_Regex('/^\\p{L}+\[-\\'\\p{L} \]+$/u');

The code inside the function is very straightforward. However, the function works in a very different way from most functions. Normally, when you pass an argument to a function, it’s passed by value. Whatever happens inside the function has no effect on the variable outside unless the value is returned by the function and reassigned to the original variable.

However, `validatePlaceName()` doesn’t return a value. Instead, it uses a technique known as passing by reference, which does change the original value.

Look closely at the two arguments in the parentheses—the function signature. The first argument, `$name`, represents the value in the `name` text input field. The second argument, `$errors`, represents the `$errors` array that stores error messages. What’s different is that it’s preceded by an ampersand like this: `&$errors`. This results in a permanent change to the value(s) stored in the variable passed as the argument to the function.

This means that if the `$name` variable fails validation, a `name` element will be added to the `$errors` array passed as the second argument to the function.

### ![image](graphics/note.jpg)**NOTE:**

Although the function definition uses the same name as the array in the rest of the script, it’s the ampersand in front of the argument that makes the difference. It would work the same if you passed an array called `$messages` to the function.

**2** The other text fields that you need to validate are the description and photo captions. Add the following function definitions to db\_definitions.php:

function validateDescription($description, $val, &$errors) {  

    if (!$val->isValid($description)) {  

        $errors['description'] = 'Description is required';  

    }  

}

function validateCaption($caption, $num, $val, &$errors) {  

    if (!$val->isValid($caption)) {  

        $errors["photo{$num}"] = "Caption for photo $num is too long";  

    }  

}

Like `validatePlaceName()`, these two functions pass the `$errors` argument by reference. So, they result in elements being added to the original `$errors` array if the value passed to the validator is rejected. Unlike the previous function, they don’t instantiate a `Zend_Validator` object. Instead, they expect a validator (`$val`) to be passed to them as an argument.

The `validateCaption()` function also expects an argument called `$num`. The function will be used inside a loop, so it’s necessary to keep count of how many times the loop has run. `$num` is used inside double quotation marks to insert the correct photo number in the `$errors` array.

**3.** The validator for the description and captions checks the length of the string. To avoid the need to change the minimum and maximum values in multiple places, add the following definitions at the top of db\_definitions.php:

$captionMin = 0;  

$captionMax = 150;  

$descriptionMin = 10;  

$descriptionMax = NULL;

These set the minimum length of a caption to zero and the maximum to 150 characters. The minimum for a description is set to 10 characters. Setting the maximum to `NULL` means there’s no upper limit.

**4.** After validating the text fields, the script needs to check if the place name already exists in the database. Again, this uses a technique from [Lesson 7](#ch07.html#ch07). You need to run a `SELECT` query to see if there is a match for the name. Add the following function definition to db\_definitions.php:

function checkDuplicatePlacename($read, $name, &$errors) {  

    $sql = $read->quoteInto('SELECT place_id FROM places WHERE name = ?', $name);  

    $result = $read->fetchAll($sql);  

    if ($result) {  

        $errors['name'] = $_POST['name'] . ' is already listed';  

    }  

}

The function signature has three arguments: `$read` is a `Zend_Db` object capable of running `SELECT` queries; `$name` is the name you want to check; and `&$errors` is the array of error messages—again it’s passed by reference.

The code in the body of the function creates a SQL query to select the primary key of a record that has the same name as `$name` and then executes the query. If a match is found, `$result` equates to `TRUE`, adding a message to the `$errors` array. If no match is found, the name is not a duplicate.

**5.** With those definitions in place, you can now start building the processing script. Save db\_definitions.php, and switch to db\_insert\_place.php.

Add a conditional statement to ensure that the code runs only when the submit button has been clicked. The `name` attribute of the button is `insert`, so the code looks like this:

try {  

    require_once('db_definitions.php');  

    $states = getAllStates($dbRead);  

    **if (isset($_POST['insert'])) {**  

        // processing code goes here  

    **}**  

} catch (Exception $e) {  

**6.** Inside the conditional statement, call the first of the functions you just defined by pressing Ctrl+spacebar and typing **va**. Code hints display the three validation functions. Select `validatePlaceName()` and double-click or press Enter/Return. Code hints also remind you of the arguments required. The first one is the name submitted from the form, `$_POST['name']`, and the second one is the `$errors` array. The new line of code should look like this:

validatePlaceName($_POST['name'], $errors);

### ![image](graphics/caution.jpg)**CAUTION!**

When you use a function that passes an argument by reference, do not prefix the argument with an ampersand. The ampersand is used only in the function definition.

**7.** Create an instance of the `StringLength` validation class, and set the minimum and maximum values for the description using the variables defined in step 3 (they should appear in code hints after you type a dollar sign):

$val = new Zend\_Validate\_StringLength($descriptionMin, $descriptionMax);

**8** Pass the description submitted from the form, together with the validator and the `$errors` array to `validateDescription()`. Don’t forget that pressing Ctrl+spacebar will bring it up in code hints for autocompletion.

validateDescription($_POST['description'], $val, $errors);

**9.** The captions use different minimum and maximum lengths, so you need to change them using the `setMin()` and `setMax()` methods like this:

$val->setMin($captionMin);  

$val->setMax($captionMax);

**10** The form contains multiple caption fields, so you need to use a loop to check each one. The `$photofields` variable controls the number of photo and caption fields, so you can use it to limit the number of times the loop runs. Add the following code to your script:

for ($num = 1; $num <= $photofields; $num++) {  

    validateCaption($_POST["caption{$num}"], $num, $val, $errors);  

}

The counter `$num` is initialized at 1. It’s embedded in a double-quoted string in the `$_POST` variable’s key, so the loop validates `$_POST["caption1"]`, `$_POST["caption2"]`, and so on. `$num` is also passed as an argument to add the correct number to any error messages. The third and fourth arguments are the validator and the `$errors` array.

**11** The next stage is to check whether the place is already listed in the database. This involves querying the database, but there’s little point in doing so if the validation tests have failed. Wrap the call to `checkDuplicatePlacename()` in a conditional statement like this:

if (!$errors) {  

    checkDuplicatePlacename($dbRead, $_POST['name'], $errors);  

}

**12** Save db\_insert\_place.php, and test insert\_place.php in Live View or a browser. Start by submitting a blank form, remembering to hold down Ctrl/Cmd when clicking Insert Place in Live View. You should see the following error messages at the top of the page:

![image](graphics/fig10_15.jpg)
