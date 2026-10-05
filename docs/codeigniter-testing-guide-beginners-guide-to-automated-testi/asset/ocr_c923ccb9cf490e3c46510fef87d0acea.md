# Testing Page Contents

We can write tests the same way as we did in WelcomeCept. Set the URI with the $I->amOnPage() method and check the result with the $I->see() method.

tests/acceptance/NewsCept.php

```
$I->amGoingTo('access the archive page');
$I->amOnPage('/news');
$I->see('News archive');
$I->see('News test');
$I->see('News text', '.main');
$I->seeInTitle('CodeIgniter Tutorial');
```

# Comments

The $I->amGoingTo() method allows you to describe the actions you are going to perform. A method of adding comments to your test. You can also use the $I->expect() and $I->expectTo() methods to add comments describing the expected results.

$I->amGoingTo('access the archive page');

# Assertions

The $I->see() method is an assertion method. It allows us to check whether the argument string is on the page.

```
$I->see('News archive');
$I->see('News test');
```

We can use the second argument to apply a CSS class which we expect to be applied to the string.

```
$I->see('News text', '.main');
```

We can also check the page title.

```
$I->seeInTitle('CodeIgniter Tutorial');
```

To learn more about assertion methods, see the documentation's assertions section.

# Testing Forms

Codeception also allows us to fill out and submit forms. We use the $I->fillField() method to fill out the fields in the form, then use the $I->click() method to click the submit button.

> *http://codeception.com/docs/03-AcceptanceTests#Assertions