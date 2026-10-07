# Encapsulating our ideas.

validated their email address too. Ah, we'd best also have hair colour, eye colour and preferred brand of toothpaste.

You know it's true. It doesn't matter whether you follow agile or waterfall development methodologies - the business team will be giving you change requests midcycle regardless. The problem here is that constructor is going to get very large and very messy in a surprisingly short space of time. Jokingly, I listed an extra properties that the business team wanted to add to our user profile. If we just kept adding them we would end up with a constructor comprising thirty lines of code for validation and an additional ten lines of code for the actual property assignments. In other words, a maintenance nightmare.

So what approach do we do?

One approach that we might consider taking is to replace the list of property specific parameters with a single array parameter. After all, we can type-hint safely on an array still.

```
public function __construct(array $userData) {
    if (!$this->isValid($userData)) {
        throw new Exception('Provided user data array is invalid');
    }

    $this->username = $userData['username'];
    $this->email = $userData['email'];
}
```

At least our constructor is much more succinct, even though the we've clearly just taken the retrograde step of reintroducing exceptions to our constructor. Nevertheless, we could even strip the individual lines of property assignment by holding the $userData array itself as a private property instead. This is certainly a step in the right direction, which would leave us with a User class that looks very much like this: