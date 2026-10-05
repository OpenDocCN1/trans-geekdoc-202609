# Testing REST Controllers

```
curl -X POST 'http://127.0.0.1:8000/api/example/users' \
  --data-urlencode name="M&M" \\
  --data-urlencode email="mms@example.com'
```

```
{"id":100,"name":"M&M","email":"mms@example.com","message":"Added a resource"}
```

We can write the following test method:

application/tests/controllers/Example_test.php

```
public function test_When_post_user_data_Then_returns_created()
{
    $post = [
        'name' => 'John',
        'email' => 'john@example.com',
    ];

    $output = $this->request('POST', 'api/example/users', $post);
    $data = json_decode($output, true);

    $this->assertEquals($post['name'], $data['name']);
    $this->assertEquals($post['email'], $data['email']);
    $this->assertResponseCode(RESTController::HTTP_CREATED);
}
```

You can pass the $POST data as the third argument of the $this->request('POST') method. Run the phpunit command, and verify that the tests pass.

# 9.5 Testing JSON Requests

You can send a JSON request, too. In this case, we use the --data-binary option and specify the "Content-Type: application/json" header.

```
curl -X POST 'http://127.0.0.1:8000/api/example/users' \
  -H "Content-Type: application/json" \
  --data-binary '{"name":"John","email":"john@example.com"}'
```