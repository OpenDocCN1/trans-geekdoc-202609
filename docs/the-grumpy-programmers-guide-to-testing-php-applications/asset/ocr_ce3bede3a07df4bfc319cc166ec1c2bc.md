used in production, the more likely you will end up with tests that pass but applications that do not work as expected.

# Assert

The final section of the test is the one where we have all our assertions or other statements that verify our code is behaving the way we expect. Some people follow a rule of “one assertion per test,” while others follow “use however many assertions you need.” There is no correct answer, but a test case without some kind of assertion is not testing anything. In our example, we are verifying the expected output matches what the arabicToRoman() method returns.

Back to our example; it fails because I haven’t created my NumeralConvertor object.

```
Error : Class 'NumeralConverter' not found
    /Users/chartjes/grumpy-guide/test/NumeralConverterTest.php:11
```

Let me create an empty shell for the object.

```
<?php
declare(strict_types=1);

class NumeralConverter
{
}
```

Then, I update my test by adding a line where to load this object:

```
require __DIR__ . '/../src/NumeralConverter.php';
```

Finally, I run the test again, and it fails because the method I am testing doesn’t exist yet.

```
Error : Call to undefined method NumeralConverter::arabicToRoman()
    /Users/chartjes/grumpy-guide/test/NumeralConverterTest.php:16
```

Yes, this is exactly how I do my testing work. I go slow and steady, making sure not to leave anything out. We all have our own habits and programming techniques we like to use; being deliberate minimizes the likelihood I skip steps and make an easily avoidable mistake.

Now I write just enough code to satisfy the behavior we are testing for.