```
# Returns: 16.73406
altair.get_dist ()
# Returns: The distance of Altair is 5.13 pc
# I create another star instance
other = star.Star('Vega')
otro.get_stars_number ()
# Returns: Total number of stars: 2
altair.get_stars_number ()
# Returns: Total number of stars: 2
```

Is not all this familiar? It is similar to the methods and properties of Python elements such as strings or lists, which are also objects defined in classes with their methods.

Objects have an interesting property called inheritance that allows you to reuse properties of other objects. Suppose we are interested in a particular type of star called a white dwarf, which are Star stars with some special properties, so we will need all the properties of the Star object and some new ones that we will add:

```
class WBStar (Star):
    """ "Class for White Dwarfs (WD)" """
    def __init__ (self, name, type):
        """ "WD type: dA, dB, dC, dO, dZ, dQ" """
        self.name = name
        self.type = type
        Star.num_stars += 1

    def get_type (self):
        return self.type

    def __str__ (self):
        return "White Dwarf {} of type {}".format (self.name, self.type)
```

Now, as a class parameter, instead of using an object to create a new object, we have set Star to inherit the properties of that class. Thus, when creating a WDStar object we are creating a different object, with all the Star properties and