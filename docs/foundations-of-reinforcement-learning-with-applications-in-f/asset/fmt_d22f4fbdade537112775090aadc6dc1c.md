
This example is a bit convoluted—with such a simple object, we would just write `d20 = Die(20)`—but `dataclasses.replace` becomes a lot more useful with more complex objects that have multiple attributes.

Returning a fresh copy of data rather than modifying in place is a common pattern in Python libraries. For example, the majority of Pandas operations—like `drop` or `fillna`—return a copy of the dataframe rather than modifying the dataframe in place. These methods have an `inplace` argument as an option, but this leads to enough confusing behavior that the Pandas team is currently deliberating on deprecating `inplace` altogether.

Apart from helping prevent odd behavior and bugs, `frozen=True` has an important bonus: we can use immutable objects as dictionary keys and set elements. Without `frozen=True`, we would get a `TypeError` because non-frozen dataclasses do not implement `__hash__`:

![](images/comp02_24.jpg)

With `frozen=True`, dictionaries and sets work as expected:

![](images/comp02_25.jpg)

Immutable dataclass objects act like plain data—not too different from strings and ints. In this book, we follow the same practice with `frozen=True` as we do with dataclasses in general: we set `frozen=True` unless there is a specific reason not to.

### 2.3.3 Checking Types

A die has to have an `int` number of sides—0.5 sides or `"foo"` sides simply doesn't make sense. Python will not stop us from trying `Die("foo")`, but we would get a `TypeError` if we tried sampling it:

![](images/comp02_26.jpg)

The types of an object's attributes are a useful indicator of how the object should be used. Python's dataclasses let us use type annotations (also known as “type hints”) to specify the type of each attribute:

![](images/comp02_27.jpg)

In normal Python, these type annotations exist primarily for documentation—a user can see the types of each attribute at a glance, but the language does not raise an error when an object is created with the wrong types in an attribute. External tools—Integrated Development Environments (IDEs) and typecheckers—can catch type mismatches in annotated Python code without running the code. With a type-aware editor, `Die("foo")` would be underlined with an error message:

> Argument of type "Literal\['foo'\]" cannot be assigned to parameter "sides" of type "int" in function "\_\_init\_\_"
>
> "Literal\['foo'\]" is incompatible with "int"\[reportGeneralTypeIssues\]

This particular message comes from pyright running over the language server protocol (LSP), but Python has a number of different typecheckers available

Instead of needing to call `sample` to see an error—which we then have to carefully read to track back to the source of the mistake—the mistake is highlighted for us without even needing to run the code.

#### 2.3.3.1 Static Typing

Being able to find type mismatches without running code is called static typing. Some languages (e.g., Java, C++) require all code to be statically typed; Python does not. In fact, Python started out as a dynamically typed language with no type annotations. Type errors would only come up when the code containing the error was run.

Python is still primarily a dynamically typed language—type annotations are optional in most places and there is no built-in checking for annotations. In the `Die("foo")` example, we only got an error when we ran code that passed `sides` into a function that required an `int` (`random.randint`). We can get static checking with external tools, but even then it remains optional—even statically checked Python code runs dynamic type checks, and we can freely mix statically checked and “normal” Python. Optional static typing on top of a dynamically typed languages is called gradual typing because we can incrementally add static types to an existing dynamically typed codebase.

Dataclass attributes are not the only place where knowing types is useful; it would also be handy for function parameters, return values and variables. Python supports optional annotations on all of these; dataclasses are the only language construct where annotations are required. To help mix annotated and unannotated code, typecheckers will report mismatches in code that is explicitly annotated but will usually not try to guess types for unannotated code.

How would we add type annotations to our example code? So far, we've defined two classes:

*   `Distribution`, an abstract class defining interfaces for probability distributions in general
*   `Die`, a concrete class for the distribution of an n-sided die

We've already annotated the `sides` in `Die` has to be an `int`. We also know that the outcome of a die roll is an `int`. We can annotate this by adding `-> int` after `def sample(...)`:

![](images/comp02_28.jpg)

Other kinds of concrete distributions would have other sorts of outcomes. A coin flip would either be `"heads"` or `"tails"`; a normal distribution would produce a `float`. Type annotations are particularly important when writing code for any kind of mathematical modeling because we ensure that the type specifications in our code correspond clearly to the precise specification of sets in our mathematical (notational) description.

### 2.3.4 Type Variables

Annotating `sample` for the `Die` class was straightforward: the outcome of a die roll is always a number, so `sample` always returns `int`. But what type would `sample` in general have? The `Distribution` class defines an interface for any distribution, which means it needs to cover any type of outcomes. For our first version of the `Distribution` class, we didn't annotate anything for `sample`:

![](images/comp02_29.jpg)

This works—annotations are optional—but it can get confusing: some code we write will work for any kind of distribution, some code needs distributions that return numbers, other code will need something else… In every instance `sample` better return something, but that isn't explicitly annotated. When we leave out annotations our code will still work, but our editor or IDE will not catch as many mistakes.

The difficulty here is that different kinds of distributions—different implementations of the `Distribution` interface—will return different types from `sample`. To deal with this, we need type variables: variables that stand in for some type that can be different in different contexts. Type variables are also known as “generics” because they let us write classes that generically work for any type.

To add annotations to the abstract `Distribution` class, we will need to define a type variable for the outcomes of the distribution, then tell Python that `Distribution` is “generic” in that type:

![](images/comp02_30.jpg)

In this code, we've defined a type variable `A` ![](images/comp02_31.jpg)

This lets us write specialized functions that only work with certain kinds of distributions. Let's say we wanted to write a function that approximated the expected value of a distribution by sampling repeatedly and calculating the mean. This function works for distributions that have numeric outcomes—`float` or `int`—but not other kinds of distributions (How would we calculate an average for a random name?). We can annotate this explicitly by using `Distribution[float]`:

![](images/comp02_32.jpg)

With this function:

*   `expected_value(Die(6))` would be fine
*   `expected_value(RandomName())` (where `RandomName` is a `Distribution[str]`) would be a type error

Using `expected_value` on a distribution with non-numeric outcomes would raise a type error at runtime. Having this highlighted in the editor can save us time—we see the mistake right away, rather than waiting for tests to run—and will catch the problem even if our test suite doesn't.

### 2.3.5 Functionality

So far, we've covered two abstractions for working with probability distributions:

*   `Distribution`: an abstract class that defines the interface for probability distributions
*   `Die`: a distribution for rolling fair n-sided dice
