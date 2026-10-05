application/tests/controllers/News_test.php

```
public function test_When_post_valid_news_item_Then_see_successful_message()
{
    $output = $this->request(
        'POST',
        '/news/create',
        [
            'title' => 'CodeIgniter is easy to write tests',
            'text' => 'You can write tests for controllers very easily!',
        ]
    );
    $this->assertContains('Successfully created', $output);
}
```

We are done. Run phpunit and verify that all of the tests pass. Check the code coverage percentage, as well.

# 7.3 Mocking Models

In the previous section, we wrote tests the database. We performed some integrated testing with the controller, model, and views.

If you are not interested in testing the model, you can mock it. So you can write tests for the controller without the model. For example, when you haven't completed the models, you can still write tests for the controllers.

Here is the test case class.

application/tests/controllers/News_with_mocks_test.php

```
<?php
/**
 * @group controller
 */
class News_with_mocks_test extends TestCase
{
    public function test_When_access_news_Then_see_news_archive()
{
    $result_array = [
        [
            "id" => "1",
        ]
```