

- __hash__ (self)：返回对象的整数哈希值，并用于可哈希集合（例如集合和字典）；如果重写 __eq__，则也应重写 __hash__，以确保被视为相等的对象具有相同的哈希值——有关此含义的说明，请参见第 B4.1.6 节
- __lt__ (self, other)、__le__ (self, other)、__gt__ (self, other)、__ge__ (self, other)：分别用于比较运算符 <、<=、> 和 >=；它们被 sorted() 函数及其他涉及对象排序概念的领域使用
- __getitem__ (self, key)、__setitem__ (self, key, value)、__delitem__ (self, key)：用于使用索引语法 obj[key] 来检索、设置或删除项目
- __iter__ (self) 和 __next__ (self)：用于使对象可迭代（例如可用于 FOR 循环）；__iter__ 应返回迭代器对象（通常是对象本身），而 __next__ 应返回下一项或引发 StopIteration 以结束迭代。

有关上述每个方法的实现示例，请参阅 Java 和 Python 文档（如适用）。

## B3.2.3 抽象和抽象类

利用继承和多态的一种常见方式是使用抽象类。抽象类可以被视为没有任何可执行代码的通用模板。它们是无法实例化的类。它们的设计目的是由其他类扩展。

当你知道所有子类都应具有某些方法或字段，但这些方法的实现本质上特定于每个子类，以至于提供默认实现在逻辑上说不通时，就会使用抽象类。

尽管抽象类不提供任何功能，但它在子类的实现中提供了标准化和一致性；其好处是，任何使用你的类层次结构的人都知道某些方法始终可用，任何新的派生类都需要遵守定义的协议。

例如，考虑一个需要对象来管理各种 2D 几何图形属性的应用程序，例如可能的计算机游戏。要求所有实现 2D 图形的类都有一个返回其表面积的函数和另一个返回其周长的函数，这是合理的。可以定义一个抽象类 Shape 来规定这些要求，如下示例所示。

请注意，因为 Python 和 Java 可以依赖与 Shape 关联的协议，所以创建在包含 Rectangle 和 Circle 对象混合体的数组上执行 getPerimeter() 和 getArea() 的代码没有问题。

```java
abstract class Shape{
    public abstract double getArea();
    public abstract double getPerimeter();
}
class Rectangle extends Shape {
    protected double width;
    protected double height;
    Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }
    @Override // Specify we are overriding the abstract method
    public double getArea() {
        return this.width * this.height;
    }
    @Override // Specify we are overriding the abstract method
    public double getPerimeter() {
        return 2 * (this.width + this.height);
    }
}
class Circle extends Shape {
    protected double radius;
    Circle(double radius) {
        this.radius = radius;
    }
    @Override
    public double getArea() {
        return Math.PI*this.radius*this.radius;
    }
    @Override
    public double getPerimeter() {
        return 2*Math.PI*this.radius;
    }
}
class Main {
    public static void main(String[] args) {
        Shape[] shapes = new Shape[4];
        shapes[0] = new Rectangle(10.0, 4.0);
        shapes[1] = new Rectangle(36.0, 7.0);
        shapes[2] = new Circle(42.0);
        shapes[3] = new Circle(10.0);
        for (int i = 0; i < shapes.length; i++) {
            System.out.println( shapes[i].getArea() );
            System.out.println( shapes[i].getPerimeter() );
        }
    }
}
```

### Python

```python
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

> ### 常见错误
> 
> **混淆抽象类的作用**
> 
> 人们常误解抽象的目的，并在简单的带继承的基类足以胜任的地方使用它。当你有一个不应自身实例化，但具有要与已实例化的子类共享的公共代码的基类时，请使用抽象类。确保任何子类都实现抽象超类的所有抽象方法。

## B3.2.4 组合和聚合

由于类类似于数据类型，对象类似于变量，你很快就会遇到这样的程序：一个对象作为其内部的变量包含许多不同类的其他对象，而且这一过程可以重复多层。发生这种情况时，这些不同的对象被认为相互关联且相互依赖。

定义这些依赖关系的方式有多种。例如，继承是一种依赖关系，其中子类需要父类作为其属性和方法的原始来源存在。

我们现在将探讨定义依赖关系的另外两种方式：组合和聚合。

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_435_0.png)

### 组合

组合是指一个对象由一个或多个对象组成，而组成对象如果没有包含对象则无法存在。这创建了一种强烈的“一是另一的一部分”关系，其中组成对象的生命周期由容器管理。这甚至可以被称为“死亡关系”，意思是如果整体被销毁，其部分也会被销毁。

组合关系的一些示例包括：

- ■ 汽车和发动机：汽车对象由发动机对象组成。发动机是汽车的组成部分。在汽车之外，它无法发挥其设计用途。如果汽车被销毁，发动机也会随之销毁。
- ■ 房屋和房间：房屋对象由多个房间对象组成。房间是房屋的一部分；如果房屋被拆除，房间也将不再作为功能单元存在。
- ■ 计算机和组件：计算机对象由 CPU、主板、内存等组成。这些组件是计算机的组成部分，分离后无法独立运行。
- ■ 人和器官：人对象由心脏、大脑和肺组成。这些器官是人体的重要组成部分，在体外无法运作。

### 聚合

聚合是指一个对象包含一个或多个对象，但被包含的对象可以独立于“容器”而存在。如果包含对象不再存在，先前被包含的对象仍可以独立存在。以这种方式，被包含对象的生命周期不由包含对象管理。

聚合关系的一些示例包括：

- ■ 大学和学生：大学包含许多学生对象。如果大学关闭（或学生完成学业后），学生在不再隶属于大学时仍继续存在。
- ■ 图书馆和书籍：图书馆包含许多书籍对象。图书馆有书，但书也可以在图书馆之外存在。
- ■ 购物车和产品：购物车包含多个产品对象。购物车有产品，但产品不依赖购物车而存在。

