There are certain methods that can be created with the Python Objects. These methods can be considered as functions of that object. For example, to create a function that would print a comment regarding ownership of the vehicle and executed on the object v1, the command below will be used:

```
class Vehicle:
    def __init__ (self, name, year)
    self.name = name
    self.name = year

    def newfunc (ownership):
        print ("I am a proud owner of " + self.name)
```

```
v1 = Vehicle ("BMW", 2018)
v1.newfunc ()
```

OUTPUT – I am a proud owner of BMW

# Reference Parameter

To refer to the latest instance of a class, the “self” parameter is used. It allows you to access variables that have been derived from a class. This parameter can be named as needed and does not have to be named “self”. The important thing to remember here is that the first parameter defined for a class will become the reference parameter for that class, as shown in the example below: