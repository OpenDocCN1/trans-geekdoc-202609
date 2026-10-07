Talking Points

296

To use a pattern or a principle effectively, it's important to understand it first. To internalise the hows and the whys and the essence of the problems that these things provide solutions for. After that, it becomes necessary to be able to recognise when you have that problem.

# Loose coupling and the art of testability

One of the key concerns that have been dealt with this part of the book, even if it wasn't mentioned by name all too often, the idea of loose coupling versus tight coupling.

Tightly coupled code is brittle code, code that is prone to breaking, code that presents a very real threat to leaving work on time and getting some quality pub time.

Here's another example of some tightly coupled code employing the much maligned Singleton Database pattern.

```
class Database
{
    private $pdo;
    private static __instance;
    private function __construct($dsn, $user, $pass) {
        $this->pdo = new PDO($dsn, $user, $pass);
    }

    public static function getInstance() {
        if (is_null(self::$instance)) {
            $config = Config::getInstance()->getParams('db');
            self::$instance = new self($config);
        }
        return self::$instance;
    }
}
```

This is the old way of doing singletons, through the provision of a private constructor and a static instance accessor. Now don't get me wrong, singletons still have their