# Testing REST Controllers

{"id":100, "name":"John", "email":"john@example.com", "message":"Added a resource"}

> The above request does not work properly with most of the web servers built-in with PHP, because of a bug. The bug has been fixed only on PHP 5.6.13 or later. If you try to use this request, please use PHP 5.6.13 or later, or another web server, like Apache.

We can test this request with the following method:

application/tests/controllers/api/Example_test.php

```
public function test_when_post_user_data_Then_returns_created() {
    $json = '{"name":"John", "email":"john@example.com"}';n    $json_array = json_decode($json, true);

    $this->request->setHeader('Content-Type', 'application/json');
    $output = $this->request('POST', '/api/example/users', $json);
    $data = json_decode($output, true);

    $this->assertEquals($json_array['name'], $data['name']);
    $this->assertEquals($json_array['email'], $data['email']);
    $this->assertResponseCode(REST_Controller::HTTP_CREATED);
}
```

You can test the request body (a JSON string) with the third argument of the $this->request() method.

Run the phpunit command, and verify that the tests pass.

# 9.6 Testing DELETE Requests

You can send a DELETE request: