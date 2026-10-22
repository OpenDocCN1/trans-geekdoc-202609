# 9. Testing APIs

Does the test pass?

```
Testing started at 1:54 p.m. ...
/usr/local/bin/php -dxdebug.remote_mode=jit /usr/local/bin/phpunit \
--no-configuration --filter "/(::it_finds_a_page_of_cards)( .*)?$ /" \
ApiResponseTest /Users/chartjes/grumpy-guide/test/api_response_test.php \
--teamcity
PHPUnit 8.3.4 by Sebastian Bergmann and contributors.

Time: 409 ms, Memory: 14.00 MB

OK (1 test, 4 assertions)
```

Next, I want to write a test for when I can get a guarantee that the API request I am going to make will be the same no matter how many times I call it. After looking at their documentation, it appears they are using unique IDs to represent cards in their database. I'll build a test that makes one of these specific calls and then make sure some of the fields in the response contain values I am expecting. Here's what the test looks like:

```
1. public function it_gets_card_details_as_expected(): void
2. {
3.   // Arrange
4.   $card_id = '9ff745f8-8fc2-4f88-ba25-03f8b9ae4932';
5.   $api_url = 'https://api.scryfall.com/cards/' . $card_id;
6. 
7.   // Act
8.   $response = json_decode(
9.     file_get_contents($api_url),
10.    true,
11.    512,
12.    JSON_THROW_ON_ERROR
13.  );
14. 
15.   // Assert
16.   $this->assertEquals('card', $response['object']);
17.   $this->assertEquals($card_id, $response['id']);
18.   $this->assertEquals('Dusk // Dawn', $response['name']);
19. }
```

My test passes.