That's why you can set a ‘multiple’ validator via setPostValidator() to set the validators that work on several values. The post validator is executed after all other validators and receives an array of cleaned up values. If you need to validate raw input form data, use the setPreValidator() method instead.

A typical registration form definition would look like this:

```
// in modules/foo/actions/actions.class.php
// Define the form
$this->form = new sfForm();
$this->form->setWidgets(array(
	'login' => new sfWidgetFormInputText(),
	'password1' => new sfWidgetFormInputText(),
	'password2' => new sfWidgetFormInputText()
	));
$this->form->setValidators(array(
	'login' => new sfValidatorString(), // login is required
	'password1' => new sfValidatorString(), // password1 is required
	'password2' => new sfValidatorString(), // password2 is required
	));
$this->form->setPostValidators(new sfValidatorSchemaCompare('password1',
	'==', 'password2'));

```

The sfValidatorSchemaCompare validator is a special multiple validator that receives all the cleaned up values and can pick up two of them for comparison. Naturally, you can define more than one post validator by using the sfValidatorAnd and the sfValidatorOr validators.

# Validators

Symfony offers quite a lot of validators. Remember that each validator accepts an array of option and an array of errors as arguments where you can at least customize the required and invalid error messages.

```
// String validator
$form->setValidator('message', new sfValidatorString(array(
	'min_length' => 4,
	'max_length' => 50,
	),
	array(
	'min_length' => 'Please post a longer message',
	'max_length' => 'Please be less verbose',
	)));

// Number validator
$form->setValidator('age', new sfValidatorNumber(array( // use
	'sfValidatorInteger' instead if you want to force integer values
	'min' => 18,
	'max' => 99.99,
	),
	array(
	'min' => 'You must be 18 or more to use this service',
	'max' => 'Are you kidding me? People over 30 can\'t even use the
	Internet',
	)));

```