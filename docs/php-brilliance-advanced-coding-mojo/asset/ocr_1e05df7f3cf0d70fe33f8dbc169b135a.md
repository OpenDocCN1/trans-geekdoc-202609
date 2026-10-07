Encapsulating our ideas.

Say we have a user object, the properties of which are username, email address and some sort of credit balance. We can reasonably expect that we'd want to render these property values to the user's browser. By far, the easiest and quickest way to do this would be to make those properties public and just echo them out at the relevant point in our code. Let's just take a look at this code so that we can see what I'm on about.

```
class User {
    public $username;
    public $email;
    public $balance;
    public function __construct($username, $email, $balance) {
        $this->username = $username;
        $this->email = $email;
        $this->balance = $balance;
    }
}

$u = new User('joe', 'joe@example.com', 12.95);
```

```
echo $u->username;
```

This is our super quick and easy way of setting up our object and then rendering of our object's public property. As far as PHP is concerned, it's perfectly valid code of course. As far as reflecting PHP Brilliance by being part of a robust, secure and maintainable enterprise grade application, it's nothing like it.

So what are we to do? The first step to fixing the user object above is to declare the properties private. This is always the right thing to do. If ours was one of those ideal worlds, it wouldn't even be possible to declare object properties as being public in the first place. Unfortunately, our world is a little way off being ideal, so we need to be on our guard against such fundamental mistakes. I say on our guard, but the sooner that PHP developer starts crafting their class definitions with private