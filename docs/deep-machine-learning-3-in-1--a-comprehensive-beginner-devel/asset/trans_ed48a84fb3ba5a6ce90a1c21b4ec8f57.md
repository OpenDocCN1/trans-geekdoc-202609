
让我们现在分析一下代码。你可以在代码中找到三个参数，即 namep 和 agep。这些变量可以起任何名字。你可以把它们叫作 n 和 a，不过，按照 Python 的惯例，使用全名会让你或其他程序员更容易阅读和理解代码。

Peacock 类还有另外两个方法，可以让孔雀站立和飞行。在代码末尾，你可以看到我创建的一个名为 Timmy 的孔雀实例。你可以创建任意多个实例来尝试下面的方法。请看下面的代码片段。

```
class Peacock():
    """This is a simple try to build a model of a peacock."""
    def __init__(self, namep, agep):
        """This will initialize the name and age attributes."""
        self.namep = namep
        self.agep = agep

    def sit(self):
        """This will simulate a peacock standing in response to a particular command."""
        print(self.namep.title() + " is now standing.")

    def fly_away(self):
        """This will simulate flying over in response to a particular command."""
        print(self.namep.title() + " flew away!")

my_peacock = Peacock('timmy', 8)
print(" My peacock is named as " + my_peacock.namep.title() + ".")
print(" The peacock is of " + str(my_peacock.agep) + " years.")

my_peacock1 = Peacock('Crazy', 5)
print(" My peacock is named as " + my_peacock.namep.title() + ".")
print(" The peacock is of " + str(my_peacock.agep) + " years.")

my_peacock = Peacock('Lucy', 2)
print(" My peacock is named as " + my_peacock.namep.title() + ".")
print(" The peacock is of " + str(my_peacock.agep) + " years.")

my_peacock = Peacock('Jack', 9)
print(" My peacock is named as " + my_peacock.namep.title() + ".")
print(" The peacock is of " + str(my_peacock.agep) + " years.")

>>> ================ RESTART ================
>>>
My peacock is named as Timmy.
The peacock is of 8 years.
My peacock is named as Timmy.
The peacock is of 8 years.
My peacock is named as Lucy.
The peacock is of 2 years.
My peacock is named as Jack.
The peacock is of 9 years.
>>>
```

在下一个代码片段中，我将向同一个类添加方法。我将让孔雀站立和飞行。请看下面的代码片段。

```
class Peacock():

    """This is a simple try to build a model of a peacock."""

    def __init__(self, namep, agep):

        """This will initialize the name and age attributes."""

        self.namep = namep

        self.agep = agep

    def stand(self):
        """This will simulate a peacock standing in response to a particular command."""
        print(self.namep.title() + " is now standing in the middle of the pond.")

    def fly_away(self):
        """This will simulate flying over in response to a particular command."""
        print(self.namep.title() + " is gearing up to fly away!")

my_peacock = Peacock('timmy', 8)
print(" My peacock is named as " + my_peacock.namep.title() + ".")
print(" The peacock is of " + str(my_peacock.agep) + " years.")
my_peacock.stand()
my_peacock.fly_away()

my_peacock1 = Peacock('Crazy', 5)
print(" My peacock is named as " + my_peacock.namep.title() + ".")
print(" The peacock is of " + str(my_peacock.agep) + " years.")
my_peacock1.stand()
my_peacock1.fly_away()

my_peacock2 = Peacock('Lucy', 2)
print(" My peacock is named as " + my_peacock.namep.title() + ".")
print(" The peacock is of " + str(my_peacock.agep) + " years.")

my_peacock2.stand()
my_peacock2.fly_away()

my_peacock3 = Peacock('Jack', 9)
print(" My peacock is named as " + my_peacock.namep.title() + ".")
print(" The peacock is of " + str(my_peacock.agep) + " years.")

my_peacock3.stand()
my_peacock3.fly_away()

>>> ================= RESTART =================
>>>
My peacock is named as Timmy.

The peacock is of 8 years.
Timmy is now standing in the middle of the pond.
Timmy is gearing up to fly away!
My peacock is named as Timmy.
The peacock is of 8 years.

Crazy is now standing in the middle of the pond.
Crazy is gearing up to fly away!
My peacock is named as Timmy.
The peacock is of 8 years.

Lucy is now standing in the middle of the pond.
Lucy is gearing up to fly away!
My peacock is named as Timmy.
The peacock is of 8 years.

Jack is now standing in the middle of the pond.
Jack is gearing up to fly away!
>>>
```

所有的孔雀都在按照我们的要求做同样的事情。

```
class Bike():

    """This is a simple attempt for the representation of a car."""

    def __init__(self, bmake, bmodel, byear):

        self.bmake = bmake

        self.bmodel = bmodel

        self.byear = byear

    def get_descriptive_bname(self):

        long_bname = str(self.byear) + ' ' + self.bmake + ' ' + self.bmodel

        return long_bname.title()


my_bike = Bike('bmw', 'z4', 2014)

print(my_bike.get_descriptive_bname())

>>> ================= RESTART =================
==============================================
>>>

2014 Bmw Z4

>>>
```

现在让我们向 Bike 类添加另一个属性，即 odometer_b_reading。这将帮助你读取自行车的里程表。

```
class Bike():
    """This is a simple attempt for the representation of a car."""
    def __init__(self, bmake, bmodel, byear):
        self.bmake = bmake
        self.bmodel = bmodel
        self.byear = byear
        self.odometer_b_reading = 0
    def get_descriptive_bname(self):
        long_bname = str(self.byear) + ' ' + self.bmake + ' ' + self.bmodel
        return long_bname.title()
    def reading_odometer(self):
        print("The heavy bike has " + str(self.odometer_b_reading) + " miles on the meter.")
```

my_bike = Bike('bmw', 'F 900 R', 2015)
print(my_bike.get_descriptive_bname())
my_bike.reading_odometer()

my_bike1 = Bike('bmw', 'F 900 XR', 2012)
print(my_bike.get_descriptive_bname())
my_bike1.reading_odometer()

my_bike2 = Bike('bmw', 'S 1000 R', 2019)
print(my_bike.get_descriptive_bname())
my_bike2.reading_odometer()

my_bike3 = Bike('bmw', 'S 1000 RR', 2010)
print(my_bike.get_descriptive_bname())
my_bike3.reading_odometer()

>>> ================= RESTART
=================
>>>
2015 Bmw F 900 R

The heavy bike has 0 miles on the meter.

2015 Bmw F 900 R

The heavy bike has 0 miles on the meter.

2019 Bmw S 1000 R

The heavy bike has 0 miles on the meter.

2010 Bmw S 1000 Rr

The heavy bike has 0 miles on the meter.

>>>

在下一个代码片段中，我将向类添加另一个函数。请看下面的代码片段。

```
class Bike():

    """This is a simple attempt for the representation of a car."""

    def __init__(self, bmake, bmodel, byear):

        self.bmake = bmake

        self.bmodel = bmodel

        self.byear = byear

        self.odometer_b_reading = 0

    def get_descriptive_bname(self):

        long_bname = str(self.byear) + ' ' + self.bmake + ' ' + self.bmodel
        return long_bname.title()

    def reading_odometer(self):

        print("The heavy bike has " + str(self.odometer_b_reading) + " miles on the meter.")

    def updating_odometer(self, bmileage):

        self.odometer_b_reading = bmileage


my_bike = Bike('bmw', 'F 900 R', 2015)
print(my_bike.get_descriptive_bname())
my_bike.updating_odometer(15)
my_bike.reading_odometer()


my_bike1 = Bike('bmw', 'F 900 XR', 2012)
print(my_bike.get_descriptive_bname())
my_bike1.updating_odometer(10)
my_bike1.reading_odometer()


my_bike2 = Bike('bmw', 'S 1000 R', 2019)
print(my_bike.get_descriptive_bname())
my_bike2.updating_odometer(22)
my_bike2.reading_odometer()


my_bike3 = Bike('bmw', 'S 1000 RR', 2010)
print(my_bike.get_descriptive_bname())
my_bike3.updating_odometer(25)
my_bike3.reading_odometer()

>>> ================= RESTART =================
==============================
>>>
2015 Bmw F 900 R
The heavy bike has 15 miles on the meter.
2015 Bmw F 900 R
The heavy bike has 10 miles on the meter.
2015 Bmw F 900 R
The heavy bike has 22 miles on the meter.
2015 Bmw F 900 R
The heavy bike has 25 miles on the meter.
>>>
```

你可以使用 updating_odometer () 方法在每次尝试修改里程表读数时执行额外工作。你可以向类添加另一个条件，以确保没有人可以回滚里程表读数。看看你可以如何做到这一点。

```
class Bike():

    """This is a simple attempt for the representation of a car."""

    def __init__(self, bmake, bmodel, byear):

        self.bmake = bmake

        self.bmodel = bmodel

        self.byear = byear

        self.odometer_b_reading = 0
```
