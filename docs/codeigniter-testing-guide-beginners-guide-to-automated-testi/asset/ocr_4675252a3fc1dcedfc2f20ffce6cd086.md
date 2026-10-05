# Testing Rest Controllers

```
$ curl -X GET -v 'http://127.0.0.1:8000/api/example/users'
* Trying 127.0.0.1...
* Connected to 127.0.0.1 (127.0.0.1) port 8000 (*0)
> GET /api/example/users HTTP/1.1
> Host: 127.0.0.1:8000
> User-Agent: curl/7.43.0
> Accept: */
>
< HTTP/1.1
< Host: 127.0.0.1:8000
< Connection: close
< X-Powered-By: PHP/5.5.26
< Content-Type: application/json; charset=utf-8
< Closing connection
< [{"id":1,"name":"John","email":"john@example.com","fact":"Loves coding"},{"id":2,"name":"Jim","email":"jim@example.com","fact":"Developed on CodeIgniter"},{"id":3,"name":"Jane","email":"jane@example.com","fact":"Lives in the USA","hobbies":["guitar","cycling"]}]
```

We write a test class for it. The controller calls exit(), so we have to catch the CIPHUnitTestException exception.

application/tests/controllers/api/Example_test.php

```
<?php
/**
 * @group controller
 */
class Example_test extends TestCase
{
    public function test_When_get_users_Then_returns_all_user_data()
    {
        try {
            $this->request('GET', 'api/example/users');
        } catch (CIPHUnitTestException $e) {
            $output = ob_get_clean();
        }
    }

    $data = json_decode($output, true);
    $this->assertCount(3, $data);
    $this->assertResponseCode(200);
```