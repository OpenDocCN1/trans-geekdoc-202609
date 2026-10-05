# Testing Controllers

100

```
42
43  'POST',
44  '/news/create',
45  [
46      'title' => CodeIdentifier is easy to write tests',
47      'text' => 'You can write tests for controllers very easily!',
48  ]
49  
50  );
51  $this->assertContains('<h2>Successfully created</h2>', $output);
52  
53  public function test_access_news_Then_see_two_items())
54  {
55      $output = $this->request('GET', '/news');
56      $this->assertContains('<h3>News test</h3>', $output);
57      $this->assertContains(
58          '<h3>CodeIdentifier is easy to write tests</h3>', $output
59      );
60  }
61  
62  public function test_post_invalid_news_item_Then_see_error_messages())
63  {
64      $output = $this->request(
65          'POST',
66          '/news/create',
67          [
68              'title' => '',
69              'text' => '',
70          ]\n71      );
72      $this->assertContains('<p>The Title field is required.</p>', $output);
73      $this->assertContains('<p>The Text field is required.</p>', $output);
74  }
```

We can use the database fixtures (setUpBeforeClass() method) from the News_model_test class in Chapter 5. We also use the $this->request() and $this->assertResponse() methods in Chapter 5.

The new thing here is that send (emulate) POST requests. We can set $_POST data using the third argument of the $this->request('POST') method.