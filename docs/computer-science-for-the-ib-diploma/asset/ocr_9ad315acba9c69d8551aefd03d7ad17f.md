# Python

```
from abc import ABC, abstractmethod
import math
# Shape: Abstract class in Python, inherits from ABC (Abstract Base Class)
class Shape(ABC):
    @abstractmethod
    def get_area(self):
        pass
    @abstractmethod
    def get_perimeter(self):
        pass
# Rectangle class, inherits from Shape
class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height
    def get_area(self):
        return self.width * self.height
    def get_perimeter(self):
        return 2 * (self.width + self.height)
# Circle class, inherits from Shape
class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius
    def get_area(self):
        return math.pi * self.radius ** 2
    def get_perimeter(self):
        return 2 * math.pi * self.radius
# Main section
if __name__ == "__main__":
    shapes = [
        Rectangle(10.0, 4.0),
        Rectangle(36.0, 7.0),
        Circle(42.0),
        Circle(10.0)
    ]
    for i in range(len(shapes)):
        print(shapes[i].get_area())
        print(shapes[i].get_perimeter())
```

> ### Common mistake
> 
> **Confusing the role of abstract classes**
> 
> It is common to misunderstand the purpose of abstraction, and to use it where a simple base class with inheritance might suffice. Use abstract classes when you have a base class that should not be instantiated itself, but has common code to share with the subclasses that are instantiated. Make sure any subclass implements all the abstract methods from the abstract superclass.