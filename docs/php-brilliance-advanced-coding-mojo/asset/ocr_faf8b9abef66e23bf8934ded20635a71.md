# Encapsulating our ideas.

Look at what we've done there! The suggestion here is that all of the validation logic for the $UserData array is tucked away nicely in the UserValidator object. As long as we can have faith in this validator and its operation, we initialising our User object with validated data in a very succinct fashion. Furthermore, any future changes to the structure of the $UserData (Y'know, the biz team wants 'favourite colour' recording. Next week, it'll be 'Shoe size') will result in zero changes to our User class as it stands, which can only be a good thing, right?

Still, we can take this one step further. We can combine the $UserData array and the UserValidator into a single object. Let's call it a UserDataTransport object and the code up the changes like:

```
class User
{
  /**
   * @var UserDataTransport
   */
  private $userData;

  public function __construct(UserDataTransport $udt)
  {
    $this->userData = $udt;
  }
}
```

Finally, we've arrived at a very short and sweet User class which correctly holds its validated user attributes in a private property but in such a way as not clutter up the User class itself with validation routines that we might very well need elsewhere too. From the perspective of our User class, it's now initialised correctly with valid data since we are also trusting the $udt instance to have done its correctly prior to being passed in.

Some of you might be thinking at this point that all we've achieved here is to move the methods that should be in the User class into something else, and then proceeded to put a rather useless shell, called User, on top of that. If this was the end of our journey then it would be quite right.

It isn't the end of the journey though. Whilst we are indeed approaching the final straight, we have gotten to the point where we should take a pause, make a nice cup of tea and cogitate a bit.