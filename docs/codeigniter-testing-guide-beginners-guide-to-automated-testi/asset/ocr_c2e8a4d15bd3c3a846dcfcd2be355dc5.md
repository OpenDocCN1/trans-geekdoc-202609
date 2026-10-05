# Unit Testing for Models

```
['title', null, 'News Title'],
['text', null, 'News Text']
);

// Create mock object for CI_DB
$db = $this->getMock_CI_DB(
  'insert',
  'news',
  [
    "title" => "News Title",n    "slug" => "news-title",n    "text" => "News Text"
  ],
  true
)
```

```
// Inject mock objects into the model
$this->obj->input = $obj;
$this->obj->db = $db;
```

```
$result = $this->obj->set_news();
$this->assertTrue($result);
```

Run the phpunit command and make the tests pass. Check the code coverage report, as well.

# 6.4 With the Database or Without the Database?

We wrote the test case class with a Database Fixture in Chapter 5, Test Case for News Model. We wrote the test case with Mocks in the previous section.

Which is better? In this case, the test case with the database fixture is simpler and easier to understand. In fact, it seems a bit faster than the test case with mocks on my computer. You will probably prefer testing with the database.

Does it mean you should always write tests with the database? The answer is not so simple.

# Testing with Little Value

If we have two classes, Foo and Bar, like below: