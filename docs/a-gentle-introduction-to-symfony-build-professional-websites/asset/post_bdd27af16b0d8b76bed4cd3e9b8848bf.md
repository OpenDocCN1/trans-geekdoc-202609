
'message' => new sfValidatorString(array('min_length' => 4))));

You can apply more than one validator on a field. For instance, you may want to check that the email field satisfies both the sfValidatorEmail and the sfValidatorString validators with a minimum size of 4 characters. In such a case, use the sfValidatorAnd validator to combine two validators, and pass the two sfValidatorEmail and sfValidatorString validators as an argument:

```
$this->form->setValidators(array(
  'name' => new sfValidatorString(),
  'email' => new sfValidatorAnd(array(
    new sfValidatorEmail(),
    new sfValidatorString(array('min_length' => 4)),
  ), array('required' => false)),
  'subject' => new sfValidatorString(),
  'message' => new sfValidatorString(array('min_length' => 4))
));

```

If both validators are valid, then the email field is declared valid. Similarly, you can use the sfValidatorOr validator to combine several validators. If one of the validators is valid, then the field is declared valid.

Each invalid validator results into an error message in the field. These error messages are in English but use the symfony internationalization helpers; if your project uses other languages, you can easily translate the error messages with an i18n dictionary. Alternatively, every validator provides a third argument to customize its error messages. Each validator has at least two error messages: the required message and the invalid message. Some validators can display error messages for a different purpose, and will always support the overriding of the error messages through their third argument:

```
// in modules/foo/actions/actions.class.php
$this->form->setValidators(array(
  'name' => new sfValidatorString(),
  'email' => new sfValidatorEmail(array(), array(
    'required' => 'Please provide an email',
    'invalid' => 'Please provide a valid email address (me@example.com)'
  )),
  'subject' => new sfValidatorString(),
  'message' => new sfValidatorString(array('min_length' => 4), array(
    'required' => 'Please provide a message',
    'min_length' => 'Please provide a longer message (at least 4 characters)'
  ))
));

```

Naturally, these custom messages will render in the templates through i18n helpers, so any multilingual application can also translate custom error messages in a dictionary (see Chapter 13 for details).

## Applying a Validator To Several Fields

The syntax used above to define validators on a form does not allow to validate that two fields are valid together. For instance, in a registration form, there are often two password fields that must match, otherwise the registration is refused. Each password field is not valid on its own, it is only valid when associated with the other field.

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

## Validators

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

```
// Email validator
$form->setValidator('email', new sfValidatorEmail());
// URL validator
$form->setValidator('website', new sfValidatorUrl());
// Regular expression validator
$form->setValidator('IP', new sfValidatorRegex(array(
    'pattern' => '^[0-9]{3}\\.[0-9]{3}\\.[0-9]{2}\\.[0-9]{3}$'
)));
```

Even though some form controls (like drop-down lists, checkboxes, radio button groups)
restrict the possible choices, a malicious user can always try to hack your forms by
manipulating the page with Firebug or submitting a query with a scripting language.
Consequently, you should also validate fields that only accept a limited array of values:

```
// Boolean validator
$form->setValidator('has_signed_terms_of_service', new sfValidatorBoolean());
// Choice validator (to restrict values in a list)
$form->setValidator('subject', new sfValidatorChoice(array(
    'choices' => array('Subject A', 'Subject B', 'Subject C')
)));
// Multiple choice validator
$form->setValidator('languages', new sfValidatorChoice(array(
    'multiple' => true,
    'choices' => array('en' => 'English', 'fr' => 'French', 'other')
)));
```

I18n choice validators exist for country lists (sfValidatorI18nChoiceCountry) and
language lists (sfValidatorI18nChoiceLanguage). These validators accept a restricted
list of countries and languages if you want to limit the possible options.

The sfValidatorChoice validator is often used to validate a sfWidgetFormChoice
widget. And since you can use the sfWidgetFormChoice widget for foreign key columns, so
symfony also provides a validator to check that the foreign key value exists in the foreign
table:

```
// Propel choice validator
$form->setValidator('section_id', new sfValidatorPropelChoice(array(
    'model' => 'Section',
    'column' => 'name'
)));
```

```
// Doctrine choice validator
$form->setValidator('section_id', new sfValidatorDoctrineChoice(array(
    'model' => 'Section',
    'column' => 'name'
)));
```

Another useful Model-related validator is the sfValidatorPropelUnique validator, which
checks that a new value entered via a form doesn't conflict with an existing value in a
database column with a unique index. For instance, two users cannot have the same login,
so when editing a User object with a form, you must add a sfValidatorPropelUnique
validator on this column:

```
// Listing 10-36
// Propel unique validator
$form->setValidator('nickname', new sfValidatorPropelUnique(array(
  'model' => 'User',
  'column' => 'login'
)));
```

```
$form->setValidator('nickname', new sfValidatorDoctrineUnique(array(
  'model' => 'User',
  'column' => 'login'
)));
```

To make your forms even more secure and avoid Cross-Site Request Forgery attacks, you can enable the CSRF protection:

```
// Listing 10-37
// CSRF protection - set the secret to a random string that nobody knows
$form->addCSRFProtection('flkd445rvvrGV34G');
```

> You can set the CSRF secret once for the whole site in the settings.yml file:

```
// Listing 10-38
# in apps/myapp/config/settings.yml
all:
 .settings:
  # Form security secret (CSRF protection)
  csrf_secret: ##CSRF_SECRET## # Unique secret to enable CSRF
  protection or false to disable
```

The multiple validators work with the whole form, rather than a single input. Here is a list of available multiple validators:

```
// Listing 10-39
// compare validator - compare two fields
$form->setPostValidator(new sfValidatorSchemaCompare('password1', '==',
 'password2'));
```

```
// Extra field validator: looks for fields in the request not present in
the form
$form->setOption('allow_extra_fields', false);
$form->setOption('filter_extra_fields', true);
```

## Alternative Ways to Use a Form

## Form Classes

With all the widget options, validators and form parameters, the contact form definition
written in the actions class looks quite messy:

```
// Listing 10-40
// in modules/foo/actions/actions.class.php
// Define the form
$this->form = new sfForm();
$this->form->getWidgetSchema()->setNameFormat('contact[%s]');
$this->form->getWidgetSchema()->setIdFormat('my_form_%s');
```
