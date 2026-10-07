Instantiaphobia

```
class User {
    private function __construct() {
        // Init object
    }
    /**
     * Factory method included in the class definition
     * /
     */
    public static function create() {
        return new User();
        // A real(create) method would of course
        // do much more to set up the user instance
        // rather than just "return new"
    }
}
```

// Elsewhere in our application
$user = User::create();

Now, with the code above, not only have we declared the User class, we've also gotten the instantiation of User objects covered by including a factory method directly within the class. On its own, this strategy will undoubtedly have an army of developers outraged and reaching for the pitchforks and torches. I'll get on to the reasons why this might be so shortly, but first, let's take a look at the benefits that this technique provides. We'll be able to keep these benefits in mind as we progress through steadily improving solutions.

From the get-go, we've provided our entire application's code base with the means necessary to get hold of a User instance. Regardless of whereabouts in the application you are, if you need a User instance, can pick one up in our newly approved fashion simply calling the corresponding create() method.

$user = User::create();

That's not all.. If, during the process of building out the User class, we find ourselves needing to specify certain dependencies that must be supplied to the