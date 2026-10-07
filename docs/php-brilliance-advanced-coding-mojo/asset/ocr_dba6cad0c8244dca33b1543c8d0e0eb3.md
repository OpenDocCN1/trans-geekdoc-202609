More pub time through interfaces.

a particular method is included in an object, client code is only interested in the methods that it can actually invoke. It has no business knowing about the object’s internals. Again, an interface is a public declaration made for the benefit of the implementing object’s collaborators.

There are a couple of pretty important things to remember here though. Important as in “When is your spouse’s birthday” important.

The first is that an interface never declares the actual implementation logic that goes into a method. The guarantee being offered extends to declaring the method names that are provided, and the list of expected parameters for each of those methods. There, of course, no guarantee that the named methods will behave as the method name might suggest. That particular responsibility is down to you and/or the members of your team.

As such, the method names declared in an interface are always written down as single line of code terminated with a semi-colon, like this:

```
public function methodName($arg1, $arg2);
```

That right is called the method signature, which in turn comprises precisely of the method name itself and a declaration of any parameters that the method requires. Whenever the opportunity arises the developer exhibiting PHP Brilliance will stick the appropriate type hints in there too, leading to a method specification that looks more like this one.

```
public function setAdapter(AdapterInterface $adapter);
```

The second important thing to note is that, whilst we are waiting for PHP7 to go mainstream, our interfaces cannot declare the data type of any values that might be returned from invoking the declared methods. What means in reality is that even if an interface guarantees that the getEmail() will be present, the guarantee doesn’t extend as far as ensuring the implemented method will give you back an email address, or that the return value even be a string. PHP7 gives that ability in some degree but in the meantime, responsibility is also squarely on the shoulders of you and your team.