portions of code are refactored to a single place, thus applying the Don’t Repeat Yourself (DRY) principle.

And to make sure that the application still runs when it changes constantly, it needs a full set of unit tests that can be automated. If well written, unit tests are a solid way to ensure that nothing is broken by adding or refactoring code. Some development methodologies even stipulate writing tests before coding—that’s called test-driven development (TDD).

> There are many other principles and good habits related to agile development. One of the most effective agile development methodologies is called Extreme Programming (abbreviated as XP), and the XP literature will teach you a lot about how to develop an application in a fast and effective way. A good starting place is the XP series books by Kent Beck (Addison-Wesley).

Symfony is the perfect tool for RAD. As a matter of fact, the framework was built by a web agency applying the RAD principle for its own projects. This means that learning to use symfony is not about learning a new language, but more about applying the right reflexes and the best judgment in order to build applications in a more effective way.

# YAML

According to the official YAML website15, YAML is “a human friendly data serialization standard for all programming languages”. Put another way, YAML is a very simple language used to describe data in an XML-like way but with a much simpler syntax. It is especially useful to describe data that can be translated into arrays and hashes, like this:

```
$house = array(
    'family' => array(
        'name' => 'Doe',
        'parents' => array('John', 'Jane'),
        'children' => array('Paul', 'Mark', 'Simone')
    ),
    'address' => array(
        'number' => 34,
        'street' => 'Main Street',
        'city' => 'Nowheretown',
        'zipcode' => '12345'
    )
);
```

This PHP array can be automatically created by parsing the YAML string:

```
house:
  family:
    name: Doe
    parents:
      - John
      - Jane
    children:
      - Paul
      - Mark
      - Simone
  address:
    number: 34
    street: Main Street
```

15. http://www.yaml.org/