You can use the “del” keyword to selectively **remove properties of an object**, as shown in the example below:

```
class Vehicle:
    def __init__ (refobject, name, year)
    refobject.name = name
    refobject.name = year

    def newfunc (xyz):
        print (“I am a proud owner of ” + xyz.name)

v1 = Vehicle (“BMW”, 2018)

del v1.year

print (v1.age)
```

OUTPUT – ‘Vehicle’ object has no ‘year’ attribute

You can also use the “del” keyword to entirely **delete an object**, as shown in the example below:

```
class Vehicle:
    def __init__ (refobject, name, year)
    refobject.name = name
    refobject.name = year

        def newfunc (xyz):
```