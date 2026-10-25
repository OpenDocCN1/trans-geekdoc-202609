
```python
def get_descriptive_bname(self):

    long_bname = str(self.byear) + ' ' + self.bmake + ' ' + self.bmodel
    return long_bname.title()

def reading_odometer(self):
    print("The heavy bike has " + str(self.odometer_b_reading) + " miles on the meter.")

def updating_odometer(self, bmileage):
    self.odometer_b_reading = bmileage

    if bmileage >= self.odometer_b_reading:
        self.odometer_b_reading = bmileage

    else:

        print("Sorry, you are not allowed to roll back the odometer!")

my_bike = Bike('bmw', 'F 900 R', 2015)
print(my_bike.get_descriptive_bname())
my_bike.updating_odometer(15)
my_bike.reading_odometer()
```

```python
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
```

The heavy bike has 15 miles on the meter.

2015 Bmw F 900 R

The heavy bike has 10 miles on the meter.

2015 Bmw F 900 R

The heavy bike has 22 miles on the meter.

2015 Bmw F 900 R

The heavy bike has 25 miles on the meter.

>>>

You can add up to the value of an attribute by adding another method to the code snippet. See the following code example.

```python
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

        if bmileage >= self.odometer_b_reading:

            self.odometer_b_reading = bmileage

        else:

            print("Sorry, you are not allowed to roll back the odometer!")

    def increment_b_odometer(self, bmiles):

        self.odometer_b_reading += bmiles
```

```python
my_bike = Bike('bmw', 'F 900 R', 2015)
print(my_bike.get_descriptive_bname())
my_bike.updating_odometer(25500)
my_bike.reading_odometer()
my_bike.increment_b_odometer(150)
my_bike.reading_odometer()

my_bike1 = Bike('bmw', 'F 900 XR', 2012)
print(my_bike.get_descriptive_bname())
my_bike1.updating_odometer(10)
my_bike1.reading_odometer()
my_bike1.increment_b_odometer(100)
my_bike1.reading_odometer()

my_bike2 = Bike('bmw', 'S 1000 R', 2019)
print(my_bike.get_descriptive_bname())
my_bike2.updating_odometer(22)
my_bike2.reading_odometer()

my_bike2.reading_odometer()
my_bike2.increment_b_odometer(250)
my_bike2.reading_odometer()
my_bike3 = Bike('bmw', 'S 1000 RR', 2010)
print(my_bike.get_descriptive_bname())
my_bike3.updating_odometer(25)
my_bike3.reading_odometer()
my_bike3.reading_odometer()
my_bike3.increment_b_odometer(500)
my_bike3.reading_odometer()
>>> ================================ RESTART ================================
==============================================================
>>>
2015 Bmw F 900 R
The heavy bike has 25500 miles on the meter.
The heavy bike has 25650 miles on the meter.
2015 Bmw F 900 R
The heavy bike has 10 miles on the meter.
The heavy bike has 110 miles on the meter.
2015 Bmw F 900 R
The heavy bike has 22 miles on the meter.
The heavy bike has 22 miles on the meter.
The heavy bike has 272 miles on the meter.
2015 Bmw F 900 R
The heavy bike has 25 miles on the meter.
The heavy bike has 25 miles on the meter.
The heavy bike has 525 miles on the meter.
>>>
```

You can use methods in this way to control how your users will update values just like the value of the odometer. Different functions will allow you to take extreme attention to detail in addition to some basic checks such as the ones that are shown below. In the next section, I will explain what a child's class is and how you can use it in coding different complex programs. I will use the same main class and create different child classes to the same.

```python
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

        if bmileage >= self.odometer_b_reading:

            self.odometer_b_reading = bmileage

        else:

            print("Sorry, you are not allowed to roll back the odometer!")

    def increment_b_odometer(self, bmiles):
        self.odometer_b_reading += bmiles

class HeavyBike(Bike):
    def __init__(self, bmake, bmodel, byear):
        super(HeavyBike, self).__init__(bmake, bmodel, byear)

my_bmw = HeavyBike('bmw', 'R600', 2012)
print(my_bmw.get_descriptive_bname())

my_bike = Bike('bmw', 'F 900 R', 2015)
print(my_bike.get_descriptive_bname())
my_bike.updating_odometer(25500)
my_bike.reading_odometer()
my_bike.increment_b_odometer(150)
my_bike.reading_odometer()

my_bike1 = Bike('bmw', 'F 900 XR', 2012)
print(my_bike.get_descriptive_bname())
my_bike1.updating_odometer(10)
my_bike1.reading_odometer()
my_bike1.increment_b_odometer(100)
my_bike1.reading_odometer()

my_bike2 = Bike('bmw', 'S 1000 R', 2019)
print(my_bike.get_descriptive_bname())

my_bike2.updating_odometer(22)
my_bike2.reading_odometer()

my_bike2.reading_odometer()
my_bike2.increment_b_odometer(250)
my_bike2.reading_odometer()

my_bike3 = Bike('bmw', 'S 1000 RR', 2010)
print(my_bike.get_descriptive_bname())

my_bike3.updating_odometer(25)
my_bike3.reading_odometer()

my_bike3.reading_odometer()
my_bike3.increment_b_odometer(500)
my_bike3.reading_odometer()
```

```
>>>
= RESTART: C:/Users/saifia
computers/AppData/Local/Programs/Python/Python38/q.py
```

2012 Bmw R600
2015 Bmw F 900 R
The heavy bike has 25500 miles on the meter.
The heavy bike has 25650 miles on the meter.
2015 Bmw F 900 R
The heavy bike has 10 miles on the meter.
The heavy bike has 110 miles on the meter.
2015 Bmw F 900 R
The heavy bike has 22 miles on the meter.
The heavy bike has 22 miles on the meter.
The heavy bike has 272 miles on the meter.
2015 Bmw F 900 R

The heavy bike has 25 miles on the meter.
The heavy bike has 25 miles on the meter.
The heavy bike has 525 miles on the meter.
>>>

I will add another attribute to the child class which will tell the users about the size of the battery. See the following code snippet.

```python
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

        if bmileage >= self.odometer_b_reading:
            self.odometer_b_reading = bmileage
        else:
            print("Sorry, you are not allowed to roll back the odometer!")

    def increment_b_odometer(self, bmiles):
        self.odometer_b_reading += bmiles

class HeavyBike(Bike):
    def __init__(self, bmake, bmodel, byear):
        super(HeavyBike, self).__init__(bmake, bmodel, byear)
        self.battery_size = 100
```
