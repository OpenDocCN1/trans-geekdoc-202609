nd set, with Python Standard Library types like `Decimal`, and with NumPy arrays,
Matplotlib `Figures` and `Axes`, and pandas `Series` and `DataFrames`.

To take maximum advantage of Python you must familiarize yourself with lots of preexisting
classes. Over the years, the Python open-source community has crafted an enormous number
of valuable classes and packaged them into class libraries. This makes it easy for you to reuse
existing classes rather than “reinventing the wheel.” Widely used open-source library classes
are more likely to be thoroughly tested, bug free, performance tuned and portable across a
wide range of devices, operating systems and Python versions. You’ll find abundant Python
libraries on the Internet at sites like GitHub, BitBucket, Source Forge and more—most easily
installed with `conda` or `pip`. This is a key reason for Python’s popularity. The vast majority
of the classes you’ll need are likely to be freely available in open-source libraries.

# Creating Your Own Custom Classes

Classes are new data types. Each Python Standard Library class and third-party library class
is a custom type built by someone else. In this chapter, you’ll develop application-specific
classes, like `CommissionEmployee`, `Time`, `Card`, `DeckOfCards` and more.

Most applications you’ll build for your own use will commonly use either no custom classes
or just a few. If you become part of a development team in industry, you may work on
applications that contain hundreds, or even thousands, of classes. You can contribute your
custom classes to the Python open-source community, but you are not obligated to do so.
Organizations often have policies and procedures related to open-sourcing code.

# Inheritance

Perhaps most exciting is the notion that new classes can be formed through inheritance and
composition from classes in abundant class libraries. Eventually, software will be constructed
predominantly from standardized, reusable components just as hardware is
constructed from interchangeable parts today. This will help meet the challenges of
developing ever more powerful software.

When creating a new class, instead of writing all new code, you can designate that the new
class is to be formed initially by inheriting the attributes (variables) and methods (the class
version of functions) of a previously defined base class (also called a superclass). The new
class is called a derived class (or subclass). After inheriting, you then customize the
derived class to meet the specific needs of your application. To minimize the customization
effort, you should always try to inherit from the base class that’s closest to your needs. To do
that effectively, you should familiarize yourself with the class libraries that are geared to the
kinds of applications you’ll be building.

# Polymorphism

We explain and demonstrate polymorphism, which enables you to conveniently program
“in the general” rather than “in the specific.” You simply send the same method call to objects
possibly of many different types. Each object responds by “doing the right thing.” So the same