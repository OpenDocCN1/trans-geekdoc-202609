```
return instance;
}

public function exampleName():String
{
    return "Joey";
}
}
```

The majority of this class is the same as previous examples, with the exception of the addition of the getInstance method. This method is used to ensure that a unique instance of the class is always used. Any call to this class is done through the getInstance method, such as:

```
import User;

trace("Example Call: " + User.getInstance().exampleName);
```

The first time the class is referenced the unique instance is generated. Any call from that point simply returns the existing instance. This ensures any changes to this class will be seen by all callers. The magic behind this class is the static method and properties, which are used to essentially put a gate between the methods and the caller. All calls going through getInstance also allow you to place an authorization check on all calls.

> **NOTE** A singleton should only be used when needed. Turning every class you create into a singleton is not a good practice; in fact, most programs have one singleton that stores all of the necessary information.

# # Getters and setters

You may have noticed that a lot of class usage is focused on passing data back and forth. In fact, that is pretty much what all programming is, in a way. The idea behind a getter and setter is to gain access to private properties. In fact, it is a pretty safe bet that most of your properties will be private, because that is sort of the idea of a class. Here is an example of a getter and setter, using a class skeleton as an example:

```
class People
{
    private var _person:String;
    public function get person():String
    {
        return _person;
    }
    public function set person(u:String):void
    {
        if(u.length > 0 && u.length < 25)
        {
            _person = u;
        }
    }
}
```