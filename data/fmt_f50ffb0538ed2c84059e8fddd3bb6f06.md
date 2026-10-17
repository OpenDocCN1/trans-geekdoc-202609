
### 继承

## 摘要
为了充分利用面向对象语言的所有特性，你必须学习其处理继承的能力。本单元解释了在类层次结构中超类和子类之间的关系。它还解释了多态是什么，以及类层次结构中的对象如何可以相互独立工作。

![Images](img/idea.jpg)

## 关键点
![image](img/star.jpg) 类层次结构描述了类之间的关系。

![image](img/star.jpg) 继承允许对象使用其自身类中未定义的特性。

![image](img/star.jpg) 子类扩展超类（即父类）。

![image](img/star.jpg) 子类没有直接访问其父类的私有实例变量。

![image](img/star.jpg) 子类可以通过重新定义方法来覆盖父类的方法。

![image](img/star.jpg) 多态是当子类对象被允许以不同于其父类对象的方式行为时发生的情况。

![image](img/star.jpg) `Object` 类是所有类的父类（所有类的“母亲”）。

## 继承

抱歉，这里的继承并不是指你富有狂野的亲戚留给你的大笔遗产。它是 Java 这一极具价值的特性，允许一个类的对象继承另一个类的特性。

### 类层次结构
Java 最强大的特性之一是创建 **类层次结构** 的能力。层次结构使类可以继承另一个类的属性，从而实现 **代码复用**。这意味着层次结构较低的类会自动继承属性（如方法和实例变量），而无需在自身类中重新定义。

在生物学中，动物通过分类（如种、属、科、目、纲、界等）进行层级划分。每一个等级 **继承** 上一等级的特征和特性。

### 示例
展示猫、狗、马和大象的层次结构。注意所有德国牧羊犬都是狗，所有狗都是哺乳动物，因此所有德国牧羊犬都是哺乳动物。

![Image](img/f0292-01.jpg)

### 父类与子类（超类与子类）
这与编程有什么关系呢？在 Java 中，类有能力 **继承** 另一个类。也就是说，一个 **子类** 可以 **扩展** 一个 **父类**。当子类扩展父类时，它会继承父类的实例变量和方法。这意味着即使子类本身没有定义这些实例变量或方法，它仍然拥有它们。这是在不重写代码的前提下复用代码的强大方式。

注意：父类的方法会被子类继承，子类可以使用这些方法。然而，子类拥有自己独立的实例变量集合，与父类的实例变量是分开的。父类和子类的实例变量是两套不同的变量。子类只能通过父类提供的访问器和修改器方法来访问父类的私有实例变量。

![Image](img/power.jpg)

#### Something for Nothing（无中生有）
子类继承父类的方法，这意味着子类对象会自动获得这些方法，而无需自行定义。

#### 关键字 `extends`
**超类** 和 **父类** 可以互换使用，**子类** 和 **子类** 也可以互换使用。我们说“子类 **extends** 父类”或“子类是从超类 **derived**”。**is-a** 关系指代类层次结构。因此当我们谈论 `Dog` 或 `Mammal` 等类时，会说“`Dog` 是-a `Mammal`”甚至“`GermanShepherd` 是-a `Mammal`”。

一个类最多可以继承自 `at most one other class`；然而，类层次结构中可以存在任意数量的类。

![Image](img/power.jpg)

关键字 `extends` 用于标识正在进行继承。子类只能继承自一个父类。

### 示例
使用 `Mammal` 层次结构模拟类层次和继承。每个子类继承其父类的特征，并可以添加自己的额外特征。

![Image](img/f0293-01.jpg)
![Image](img/f0293-02.jpg)
![Image](img/f0293-03.jpg)

![Image](img/power.jpg)

#### Be Your Own Class
子类可以定义自己的额外方法。子类拥有的总方法数是父类和子类方法的组合。

### 构造函数和关键字 `super`
子类的构造函数不会从其父类继承。当从子类创建对象时，子类构造函数会自动调用父类的无参构造函数（某些集成开发环境，IDE，会显示此指令）。但是，如果你想在子类构造函数中调用带参数的父类构造函数，需要在子类构造函数的第一行显式使用 `super(arguments)` 指令。子类因此调用父类的参数化构造函数。传递给 `super` 方法的实际参数提供值，供构造函数初始化对象的实例变量。无论 `superclass` 构造函数是隐式还是显式调用，调用父类构造函数的过程都会一直进行，直到调用到 `Object` 构造函数为止。此时，层次结构中的所有构造函数都会执行，从 `Object` 构造函数开始。

### 示例
演示一个拥有两个构造函数的子类。无参构造函数会调用父类的无参构造函数；带参数构造函数会调用父类的带参数构造函数。注意：子类的每个构造函数中的 `super()` 调用 *必须* 是第一行代码。

![Image](img/f0294-01.jpg)
![Image](img/f0295-01.jpg)
![Image](img/f0295-02.jpg)
![Image](img/f0295-03.jpg)

### 类层次结构内的数据封装
子类只能通过父类的访问器和修改器方法来访问或修改父类的私有实例变量。

![Image](img/error.jpg)
子类无法直接访问其父类的 `private` 实例变量

父类和子类都可能包含实例变量。这些实例变量应声明为 private。这是数据封装。子类必须使用父类的访问器和修改器方法来访问其父类的私有实例变量。

## 多态性
“有时子类想要与父类不同的行为。”

### 重写父类的方法
在 Java 中，子类被允许 **重写** 父类的方法。这意味着即使子类从父类继承了某种做事的方式，它仍然可以选择以不同的方式执行，如果它想要的话。这是 **多态** 的一个例子。

重写父类方法的方法是重新定义方法（签名/方法头）并修改方法内部的实现。当子类对象调用该方法时，它会执行子类中定义的操作，而不是父类中的方法。

### 示例
所有来自 `FamilyMember` 类的对象都会从杯子里喝水并使用叉子进食。然而，来自 `Baby` 类的对象会从杯子里喝水并用手进食。所有来自 `SporkUser` 类的对象会从杯子里喝水并使用勺叉进食。在这种情况下，`FamilyMember` 类的 `eat` 方法被 `Baby` 类和 `SporkUser` 类都覆盖。因此，尽管方法名称相同，`Baby` 类和 `SporkUser` 类的对象进食方式与 `FamilyMember` 类的对象不同。所有继承自超类的对象何时使用重写方法由编译时决定，这一过程称为 **静态绑定**。

任何被调用的方法必须在其自身类或其父类中定义。子类通常被设计为拥有修改（覆盖）或额外的方法或实例变量。子类会继承父类的所有 public 方法；这些方法在子类中仍然保持 public。

![Image](img/f0296-01.jpg)
![Image](img/f0297-01.jpg)
![Image](img/f0297-02.jpg)
![Image](img/f0297-03.jpg)
![Image](img/f0297-04.jpg)

![Image](img/power.jpg)

#### 多态性
Java 使用 **多态** 这个术语来描述同一父类的不同子类可以表现不同的方式。这通过子类重写父类的方法来实现。

### 动态绑定
当我们想要创建一个家庭成员列表时，问题出现了。*要创建一个 `people` 的数组或 `ArrayList`，它们必须全部是同一类型！* 为了解决这个问题，我们将所有引用变量的类型统一为 *父类* 类型。

### 示例
创建一个 `FamilyMember` `ArrayList` 来演示动态绑定。将引用变量的类型统一为父类名称，并创建来自子类的对象。允许每个对象以其设计方式进食和饮用。每个 `FamilyMember` 对象的进食方式在运行时决定（即 **运行时**），这一过程称为 **动态绑定**。很酷！

![Image](img/f0298-01.jpg)
![Image](img/f0299-01.jpg)

![Image](img/error.jpg)
引用变量和层次结构

引用变量 *可以* 是子对象的父类。

![Image](img/f0299-02.jpg)
引用变量 *不能* 是父对象的子类。

![Image](img/f0299-03.jpg)

### 从子类方法中使用 `super`
即使子类覆盖了父类的方法，子类对象仍然可以调用父类的方法（如果它想要）；但是，它必须在覆盖方法内部进行调用，并传递适当的参数。通过使用关键字 **super**，子类可以调用其已覆盖的父类方法。我们说，“子类可以调用父类的方法，如果它想要。”

### 示例
修改 `Baby` 类，使其在三岁以上时，可以用手或叉子进食；否则使用手进食。使用关键字 **super** 调用父类的 `eat` 方法。同时，添加一个实例变量用于表示年龄。

![Image](img/f0299-04.jpg)
![Image](img/f0300-01.jpg)
![Image](img/f0300-02.jpg)

### 谨慎使用父引用变量指向子对象
子对象能够执行其父类的所有 public 方法。然而，父类无法执行子类的特有操作，如果子对象拥有父引用变量，子对象也无法执行其自身类中定义的独有方法。

### 示例
演示父引用变量无法执行子类特有方法的情况。`FamilyMember` 对象不知道如何 `throwTantrum`。只有 `Baby` 对象知道如何 `throwTantrum`。注意：即使 `babyCousin` 是一个 `Baby` 对象，`FamilyMember` 引用变量也阻止它能够 `throwTantrum`。

![Image](img/f0300-03.jpg)
![Image](img/f0300-04.jpg)
![Image](img/f0301-01.jpg)

### 下转型
The problem described in the previous example can be solved using a technique called `downcasting`. This is similar to—but not exactly the same as—casting an `int` to a `double`. A parent object reference variable is cast to the object type of the object that it references.

## Downcasting
You can downcast a parent reference variable to a child object as long as the object it is referring to is that child.

![Image](img/f0301-02.jpg)

### Example 1
Demonstrate downcasting by allowing the parent reference variable to perform a method that is unique to a child class. The parent reference variable is cast as a child and must refer to the child object. Pay close attention to the parentheses when casting.

![Image](img/f0301-03.jpg)
![Image](img/f0301-04.jpg)

### Example 2
You *are not allowed* to cast a parent reference object to a child if the object is a parent. In this example, mom is a `FamilyMember` reference variable that refers to a `FamilyMember` object. Attempting to cast mom as a `Baby` results in an error.

![Image](img/f0301-05.jpg)

## The `Object` Class
The **Object class** is the mother of all classes. It is part of the `java.lang` package. Every class, even the ones you write, is a descendent of the Object class. The extends is *implied*, so you don’t have to write, “extends Object”, in your own classes. The Object class does not have any instance variables, but it does have several methods that every descendent inherits. Two of these methods, the **toString** and the **equals**, are tested on the AP Computer Science A Exam and are included on the Java Quick Reference sheet. Subclasses of `Object` often override the `equals` and `toString` methods with class-specific implementation. You must be able to implement the `toString` method; however, you only need to know how to use the equals method (like we do when we compare `String` objects).

![images](img/power.jpg)
You will receive a Java Quick Reference sheet to use on the Multiple-choice and Free-response sections, which lists the `String` class methods that may be included in the exam. Make sure you are familiar with it before you take the exam.

![Image](img/f0302-01.jpg)

### Overriding the `toString` Method
The **toString** method is inherited from the Object class and was created to describe the object in some way, typically by referencing its instance variables. The Object class’s `toString` method doesn’t give you anything valuable (it returns the hex value of the object’s address). Most of the time, when creating your own classes, you will override the `toString` method so it returns a String that describes the object in a meaningful way.

#### Example
We overrode the `toString` method for the Circle class in Unit 5 so the method gives a description of the Circle object that calls it. The String that is returned should include the radius of the circle and its area.

![Image](img/f0302-02.jpg)
![Image](img/f0302-03.jpg)
![Image](img/f0303-01.jpg)

![images](img/power.jpg)

### Overriding the `toString` Method
All classes extend the Object class. When you design your own classes, *be sure to override the toString() method* of the Object class so that it describes objects from your class in a unique way using its own instance variables.

### Casting an `Object`
If a method’s parameter list contains an `Object` reference variable, then you will have to downcast the reference before using it. You must make sure that the object that you are casting `is-a` object from the class.

#### Example
Demonstrate how to handle an `Object` reference parameter. In this example, when the `FamilyMember` object, `uncleDon`, gets passed to the `timeToEat` method, he is sent as a `FamilyMember` reference variable. When he is received by the `timeToEat` method, he is renamed as `hungryMember` and is now an `Object` reference. Finally, he is cast to a `FamilyMember` and is then able to eat.

![Image](img/f0303-02.jpg)

![Image](img/arrow1.jpg) Rapid Review

## Hierarchy and Inheritance
• One major advantage of an object-oriented language is the ability to create a hierarchy of classes that allows objects from one class to inherit the features from another class.
• A class hierarchy is formed when one class extends another class.
• A class that extends another class is called the child or subclass.
• The class that is extended is called the parent or superclass.
• A class can only extend one other class.
• A class hierarchy can extend as many times as you want. That is, a child can extend a parent, then the parent can extend another parent, and so on.
• When a class hierarchy gets extended to more than just one parent and one child, the lower ends of the hierarchy inherit the features of each of the parent classes above it.
• The phrase “is-a” helps describe what parent classes a child class belongs to.
• If you want a child class to modify a parent class’s method, then you override the parent class’s method. To do this, you simply redefine the method in the child class (using the exact same method declaration and replace the code with what you want the child to do).
• The word “super” can be used to refer to either a parent’s constructor or methods.
• To purposefully call the no-argument super constructor, you must put `super()` as the first line of code in the child’s constructor. Other instructions are placed after the `super()` call.
• To call the parameterized super constructor, you must put `super(arguments)` as the first line of code in the child’s parameterized constructor. Other instructions are placed after the `super()` call.
• If you write a method that overrides the parent class’s method, you can still call the original parent’s method if you want to. Example: `super.parentMethod()`.
• A reference variable can be a parent class type if the object being created is its child class type.
• A reference variable cannot be a child class type if the object being created is its parent class type.
• A reference variable that is of a parent data type can be cast to a child data type as long as the object that it is referencing is a child object of that type.

## Polymorphism
• Polymorphism is when more than one child class extends the same parent class and each child object is allowed to act in a different way than its parent and even its siblings.
• If several child classes extend the same parent class and each child class overrides the same method of the parent class in its own unique way, then each child will act differently for that method.
• Static binding is the process of deciding which method the child reference variable will perform during compile-time.
• Dynamic binding is the process of deciding which method the parent reference will perform during run-time.
• The `Object` class is the mother of all classes in Java since it is the root of the class hierarchy and every class has `Object` as a superclass.
• The Object class contains two methods that are tested on the AP Computer Science A exam: equals and toString.
• The public boolean `equals(Object other)` method returns true if the object reference variable that calls it is referencing the same exact object as other. It returns false if the object reference variables are not referencing the same object.
• It is common to override the `equals` method when you want to determine if two objects from a class are the same.
• The public String `toString()` method returns a String representation of the object.
• It is very common to override the `toString()` method when generating your own classes.
• Downcasting is casting a reference variable of a parent class to one of its child classes.
• Downcasting is commonly used when an `Object` is in a parameter list or `ArrayList`.
• A major problem with downcasting is that the compiler will not catch any errors, and if the cast is made incorrectly, a run-time error will be thrown.

## Basic Level
假设所有类都以其名称适当的方式定义，下面哪个语句会导致编译时错误？

(A) `Object obj = new Lunch();`
(B) `Lunch lunch = new Lunch();`
(C) `Lunch sandwich = new Sandwich();`
(D) `Lunch lunch = new Object();`
(E) `Sandwich sandwich = new Sandwich();`

下面的问题 2–5 参考以下类的定义。

![Image](img/f0305-01.jpg)

### 2. 下面哪项陈述是正确的？
I. `Freshman` 是 `UnderClassman` 的子类，而 `UnderClassman` 是 `Student` 的子类
II. `Student` 是 `UnderClassman` 和 `Freshman` 的超类
III. `UnderClassman` 是 `Freshman` 的超类，同时是 `Student` 的子类

(A) I 只
(B) II 只
(C) I 和 II 只
(D) II 和 III 只
(E) I、II 和 III

### 3. 哪个选项列出的实例数据只能直接被 `Freshman` 类对象访问？
(A) `middleSchoolCode`
(B) `gradYear, gpa`
(C) `homeRoomNum, counselor`
(D) `middleSchoolCode, homeRoomNum, counselor`
(E) `middleSchoolCode, homeRoomNum, counselor, gradYear, gpa`

### 4. 假设这三个类都有带参数的构造函数（如下面所示），且所有变量都逻辑命名。
![Image](img/f0306-01.jpg)
在 `Freshman` 类的构造函数中，下面哪个 `super` 调用是合法的？
(A) `super(gradYear, gpa, homeRoomNum, counselor, middleSchoolCode);`
(B) `super(gradYear, gpa, homeRoomNum, counselor);`
(C) `super(homeRoomNum, counselor);`
(D) `super(gradYear, gpa);`
(E) `super();`

### 5. 考虑 `Student` 类中的下面方法。
![Image](img/f0306-02.jpg)
`Freshman` 对象必须像 `Student` 对象一样调用 `attendClass`，并且还需要使用 `initialPlanner` 方法（未显示）给老师初始化作业计划本。下面哪个选项展示了 `Freshman attendClass` 方法的可能实现？
![Image](img/f0307-01.jpg)
![Image](img/f0307-02.jpg)

## Advanced Level
问题 6–7 参考以下类的定义。
![Image](img/f0307-02.jpg)

### 6. 假设 `ArrayList<String> members_1` 和 `ArrayList<String> members_2` 已经正确实例化并初始化为包含非零数量的适当元素。
下面哪个声明是无效的？
![Image](img/f0307-03.jpg)

### 7. 下面哪个选项可以替换 `/* missing code */` 在 `SchoolClub` 构造函数中，以确保所有实例变量都正确初始化？
![Image](img/f0308-01.jpg)

问题 8–9 参考以下类的定义。
![Image](img/f0308-02.jpg)

### 8. 考虑下面的代码片段。
![Image](img/f0309-01.jpg)
执行该代码片段后会打印什么结果？
(A) `contains kazoo`
(B) `kazoo`
(C) `contains kazoo for a child age 4`
(D) 一切不打印。编译时错误：非法类型转换
(E) 一切不打印。运行时错误：非法类型转换

### 9. 考虑下面的代码片段。
![Image](img/f0309-02.jpg)
执行该代码片段后会打印什么结果？
(A) `contains blocks`
(B) `contains blocks for a child age 4`
(C) `contains kazoo for a child age 4`
(D) 一切不打印。编译时错误：`KidsPresent` 类中不存在 `setContents` 方法
(E) 一切不打印。运行时错误：`KidsPresent` 类中不存在 `setContents` 方法

### 10. Point3D 类
下面是类的定义：
![Image](img/f0309-03.jpg)
编写类 `Point3D`，使其继承自该类，表示一个三维点，包含 x、y 和 z 坐标。请使用适当的继承，不要重复代码。
你需要编写：
a. 构造函数，接受三个 `int` 值，分别表示 x、y、z 坐标
b. 适当的修改器和访问器方法（setter 和 getter）

![Image](img/arrow1.jpg) 答案和解释

• 选项 D 是正确答案。
• 当你实例化对象时，左侧声明类型，右侧调用相应构造函数。这里可以很好地运用 `is-a` 关系。你说：“给我一个三明治，我会感谢你请客”，这总是对的，但你不能说：“给我午餐，我会感谢你给三明治”。如果我做汤呢？
• 选项 A 正确，因为 `Lunch` 是 `Object` 的子类。
• 选项 B 和 E 正确，因为 `Lunch` 是 `Lunch` 的子类，`Sandwich` 是 `Sandwich` 的子类。（不要混淆变量名 `sandwich` 与类 `Lunch`，这会导致读者误解，但语法上是合法的。）
• 选项 C 正确，因为 `Sandwich` 是 `Lunch` 的子类。
• 选项 D 错误。`Object` 不是 `Lunch`，不存在逆向关系。右侧必须是左侧的子类（is-a 关系），否则编译失败。

### 2. 答案是 E。
• 超类包括祖父类一直到继承链的顶层，子类包括子女一直到继承链的底层，因此三个关系均为真。

### 3. 答案是 A。
• `Freshman` 对象只有自己的实例变量可以直接访问。
• `UnderClassman` 和 `Student` 的实例变量是 private，只能在对应类内部访问。
• 请注意，声明公共实例变量违背封装原则，在 AP Computer Science A 考试中会被扣分！

### 4. 答案是 B。
• 由于 `super` 调用必须是构造函数的第一条语句，`Freshman` 构造函数会保留参数 `middleSchoolCode`，并通过 `super` 调用将剩余参数传递给 `Underclassman` 的构造函数。随后它会把 `middleSchoolCode` 参数赋值给自己的实例变量。（值得注意的，`Underclassman` 构造函数会设置自己的两个变量，然后再通过 `super` 将剩余参数传递给其父类构造函数。）

### 5. 答案是 D。
• 选项 A 和 B 错误。它们错误地使用了 “extends”，该关键字应出现在类声明中，而不是方法声明中。
• 选项 C 错误。它在 `super` 调用的实际参数旁边放置了数据类型（实际参数），而类型只应出现在声明（形式参数）旁边。
• 选项 D 正确。它同时解决了上述两个错误：使用 `super.methodName` 调用父类中同名方法，并传递它期望的两个参数。随后调用 `initialPlanner` 方法。
• 选项 E 错误。它试图直接把参数赋值给父类中的对应变量。父类中的变量是 private，子类无法直接访问，即使它们存在，子类也不应假设只需赋值即可完成父类方法的全部操作。`attendClass` 显然不止这些！

### 6. 答案是 C。
### 7. 答案是 B。
### 8. 答案是 A。
### 9. 答案是 D。

### 10. (a) 构造函数：
```java
