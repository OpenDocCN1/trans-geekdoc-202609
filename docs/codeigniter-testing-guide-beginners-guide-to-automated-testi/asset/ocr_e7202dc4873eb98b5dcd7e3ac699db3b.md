# Testing Controllers

```
function ($CI) {
  $news_model = $this->getDouble(
    'News_model', ['set_news' => true]
  );
  $CI->news_model = $news_model;
}
```

```
$output = $this->request(
  'POST',
  '/news/create',
  [
    'title' => 'CodeIgniter is easy to write tests',
    'text' => 'You can write tests for controllers very easily!',
  ]
);
$this->assertContains('<h2>Successfully created/</h2>', $output);
```

```
public function test_when_post_invalid_news_item_Then_see_error_messages() {
  $output = $this->request(
    'POST',
    '/news/create',
    [
      'title' => '',
      'text' => '',
    ]
  );
  $this->assertContains('<p>The Text field is required.</p>', $output);
  $this->assertContains('<p>The Text field is required.</p>', $output);
}
```

Run phpunit and verify that all of the tests pass. Check the code coverage percentage, as well.

# 7.4 Authentication and Redirection

We often create controllers which need use authentication or redirect the user. We'll show you how to test controllers which use these features. Our examples will use Ion Auth for authentication.