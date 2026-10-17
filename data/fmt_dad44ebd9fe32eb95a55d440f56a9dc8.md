
```julia
julia> typeof(nothing)
Nothing
```

我们还引入了 `typeof()` 方法，它提供值所属类型的信息。`nothing` 的用法相当普遍，常用于代码中存在变量可能未初始化的条件场景。

```julia
julia> a = nothing

julia> i = 5
5

julia> if i < 5
           a = 5
       end

julia> typeof(a)
Nothing
```

此处，若 `i` 小于 5，则 `a` 被赋值为 5；否则保持为 `nothing`。`Nothing` 和 `nothing` 在函数参数和返回类型中也被广泛使用。

### 布尔类型

`true` 和 `false` 在 Julia 中属于 `Bool` 类型。数值上，`true` 值为 1，`false` 值为 0。

### 整数类型

整数数值类型分为无符号和有符号，具有不同的字节大小。有符号数类型包括：`Int8`、`Int16`、`Int32`、`Int64` 和 `Int128`。对应的无符号数类型分别为：`UInt8`、`UInt16`、`UInt32`、`UInt64` 和 `UInt128`。

```julia
julia> typeof(1)
Int64
```

数字字面量的默认数值类型是 `Int`，它根据机器架构映射到 `Int32` 或 `Int64`。

不过，对于无符号数字面量，通过 `0<representation specifier><number>` 指定。

```julia
julia> typeof(0b1), typeof(0o7), typeof(0xff)
(UInt8, UInt8, UInt8)
```

这些数字在二进制、八进制和十六进制表示下均映射到 `UInt8`。数字的大小由容纳该字面量所需的最小字节数决定。

```julia
julia> typeof(0xf), typeof(0xfff), typeof(0xfffff), typeof(0xfffffffff), typeof(0xfffffffffffffffff)
(UInt8, UInt16, UInt32, UInt64, UInt128)
```

与大多数其他语言一样，`+/-` 可在 Julia 中用作符号限定符。

### 浮点数类型

Julia 提供 `Float16`、`Float32` 和 `Float64`，分别按 IEEE 754 标准表示半精度、单精度和双精度浮点数。字面量可使用 `f` 或 `e` 作为指数分隔符，分别对应 `Float32` 和 `Float64`。

```julia
julia> typeof(1.0), typeof(1e0), typeof(1.e4)
(Float64, Float64, Float64)

julia> typeof(1.0f0), typeof(1f-6), typeof(1.f4)
(Float32, Float32, Float32)
```

## 类型层级与抽象类型

Julia 中的类型可以从抽象类型派生。大多数面向对象语言将此类关系视为描述类层级中对象的手段。抽象类型仅为概念表示（类似接口），不包含数据元素。

```julia
julia> abstract type MyAbstractType end

julia> struct MyConcreteType <: MyAbstractType
           member
       end

julia> a = MyConcreteType(5)
MyConcreteType(5)

julia> a isa MyAbstractType
true
```

稍后我们将详细探讨此概念。值得注意的是，一个类型只能从一个抽象类型派生。中缀运算符 `isa` 用于判断某对象是否为特定类型，该类型可以是具体类型或抽象类型。以下是 Julia 数值类型的类型层级图：

![](img/n4upl4fndrd.jpeg)

**图 2.1：** 数值类型层级

# 基本类型

基本类型是 LLVM 支持的数据类型。Julia 将代码编译为 LLVM 对应的中间表示，随后再编译为原生 CPU 机器码以 **JIT**（即时编译）方式执行。因此，将 LLVM 类型引入 Julia 是非常合乎逻辑的。这些基本类型是位值。以下是在 Julia 中定义的一组基本类型。

```julia
primitive type <<name>> <: <<supertype>> <<bits>> end
primitive type Float16 <: AbstractFloat 16 end
primitive type Float32 <: AbstractFloat 32 end
primitive type Float64 <: AbstractFloat 64 end
primitive type Bool <: Integer 8 end
primitive type Char <: AbstractChar 32 end
primitive type Int8     <: Signed    8 end
primitive type UInt8    <: Unsigned  8 end
primitive type Int16    <: Signed    16 end
primitive type UInt16   <: Unsigned  16 end
primitive type Int32    <: Signed    32 end
primitive type UInt32   <: Unsigned  32 end
primitive type Int64    <: Signed    64 end
primitive type UInt64   <: Unsigned  64 end
primitive type Int128   <: Signed    128 end
primitive type UInt128  <: Unsigned  128 end
```

虽然用户可以定义自己的基本类型，但建议使用已定义的基本类型，仅在现有类型无法满足需求时才定义新类型。其次，具有相同位值的基本类型并非本质上可互换，也无法无缝转换。类型层级在这些类型的行为中起着重要作用。

```julia
julia> UInt32(3f-1)
ERROR: InexactError: UInt32(0.3)
```

尽管它们都是 32 位实体，但单精度浮点数并非在所有情况下都能表示为无符号整数。第三，你不能创建任意位大小的基本类型。仅支持 8 位的倍数作为位大小。

```julia
julia> primitive type MyType1 40 end
julia> primitive type MyType2 4 end
ERROR: invalid number of bits in primitive type MyType2 …
```

# 位类型

Julia 与在二进制接口上运行的语言（如 C/C++、FORTRAN 及其他原生编译语言）实现无缝互操作。在这种情况下，必须确保 Julia 中定义的某些数据类型在二进制布局上保持一致，以便这些原生编译语言使用。此类类型称为**位类型**。基本类型均为位类型数据类型。某些复合数据类型也是位类型。遇到时我们将进一步讨论它们。可以通过在实例上调用函数 `isbits` 以及在类型上调用 `isbitstype` 来查询位类型。

```julia
julia> a = 10
10

julia> isbits(a)
true

julia> isbitstype(Int)
true
```

# 有理数和复数类型

虽然 `Rational`（有理数）和 `Complex`（复数）数据类型属于数值类型，但它们不是基本类型。它们是使用复合数据类型创建的，我们将在用户定义类型部分对其进行回顾。

# Char 类型

`Char` 是表示为 32 位值的字符。它可以是 Unicode 字符的有效 UCS-4 表示。我们将在字符串章节中详细讨论 `Char` 及其与 `String` 的关系。提供了 `AbstractChar` 抽象类型，以便用户开发自己的类字符数据类型。

# 字符串

字符串是字符的集合。虽然大多数字符串由 Unicode 字符代码组成，但它们也可以存储其他类型的二进制数据。提供了 `AbstractString` 抽象类型，以便高级用户定义自定义字符串类型。我们将在后续章节中详细讨论这些内容。

# 复合类型

虽然 Julia 提供了相当多的内置类型，但始终存在对复合数据类型的需求，这类类型可能需要将各种属性组合在一起。

## 不可变复合类型 (`struct`)

这些类型一旦定义，其属性就不能被修改。这些不可变数据类型在 Julia 中表示为 `struct`。

```julia
julia> struct Rectangle
           h::Float64
           w::Float64
       end

julia> r = Rectangle(10.0, 20.0)
Rectangle(10.0, 20.0)

julia> r.h = 15
ERROR: setfield! immutable struct of type Rectangle cannot be changed …
```

如上所示，`Rectangle` 是一个定义的 `struct`，并使用值 `10.0` 和 `20.0` 进行初始化。属性的值无法被修改。初始化通过 `Rectangle(10.0, 20.0)` 进行。这是一个特殊用途的函数。当我们讨论函数和方法时将了解更多相关内容。

## 可变复合类型 (`mutable struct`)

假设我们要使 `Rectangle` 可变，可以创建一个可变结构体，如下所示：

```julia
julia> mutable struct MRectangle
           h::Float64
           w::Float64
       end

julia> mr = MRectangle(10.0, 20.0)
MRectangle(10.0, 20.0)

julia> mr.h = 15.0
15.0

julia> mr
MRectangle(15.0, 20.0)
```

如上所示，实例化对象后可以修改属性值。Julia 中的复合数据类型也可以从 `abstract type`（抽象类型）派生。

```julia
julia> abstract type Shape end

julia> struct Rectangle <: Shape
           w::Float64
           h::Float64
       end

julia> struct Square <: Shape
           l::Float64
       end
```

## 复合类型行为与构造函数

Julia 中的复合类型拥有成员属性，但没有成员函数或方法。Julia 的多重分发架构用于使函数表现得像特定类型的方法，但它们与面向对象语言中的方法并不相同。有一类特殊的函数可以成为类型的成员，它们被称为**构造函数**。当我们讨论函数时将详细回顾构造函数。复合类型中成员的类型信息并不总是必须指定。

```julia
julia> mutable struct A
           member
       end

julia> a = A(5)
A(5)

julia> typeof(a.member)
Int64

julia> a1 = A("String")
A("String")

julia> typeof(a1.member)
String
```

虽然在前面的示例中，实例化对象时消除了歧义，但永远无法确定类型，因为成员属性可以动态地赋值为另一种类型。

```julia
julia> a.member = "String"
"String"

julia> typeof(a.member)
String
```

`a.member` 曾为 `Int64` 类型，现在变为 `String` 类型。Julia 会将此类未指定的类型推定为 `Any`。在无法确定类型的场景下，Julia 会将类型推定为 `Any`。从性能角度来看，使用 `Any` 是不可取的。每次访问 `Any` 类型的对象时，都会发生一次额外的重定向以访问实际对象。`Any` 类型对象的大小无法提前得知。它将是一个指针，指向内存中实际对象驻留的另一位置：

![](img/n4upl4fndre.jpeg)

**图 2.2：** (a) 成员定义为 Any (b) 成员定义为 Float32

将 `Any` 作为类型会引入不必要的间接寻址，因此可能效率低下。有时类型不一定影响算法，但会引入不同的数据位宽。例如，前文在数值数据类型背景下介绍的 `Rational` 数据类型，其分子和分母可以是任意整数数据类型，如 `Int8`、`Int16`、`Int32`、`Int64` 或 `Int128`。`Rational` 数据类型的定义如下 6：

`:`

```
struct Rational{T<:Integer} <: Real
    num::T
    den::T
end
```

该类型的两个属性 `num` 和 `den` 均为 `T` 类型，其中 `T` 是 Integer 的子类型。`Rational` 是 Real 的子类型。以下是关于参数化数据类型的一些观察。

```
julia> Rational{Any}
ERROR: TypeError: in Rational, in T, expected T<:Integer, got Type{Any}
…
```

**Any 不是 Integer 的子类型。因此无法实例化 Rational{Any}。**

```
julia> Rational{Int32} <: Rational
true
julia> Rational{Int32} <: Rational{Integer}
false
```

理解这种行为尤为重要。尽管 `Int32` 是 Integer 的子类型，但参数化表示 `Rational{Int32}` 并不是 `Rational{Integer}` 的子类型。然而 `Rational{Int32}` 是 Rational 的子类型。

正如具体数据类型一样，抽象数据类型也可以被参数化。

```
julia> abstract type Shape{T<:AbstractFloat} end
julia> struct Rectangle{T<:AbstractFloat} <: Shape{T}
           w::T
           h::T
       end
julia> struct Square{T<:AbstractFloat} <: Shape{T}
           s::T
       end
```

可以使用上述方案为 `Float32` 或 `Float64` 开发两套功能。为 `Rectangle{Float32}` 生成的类型与 `Rectangle{Float64}` 不同，它们在实例化具体类型时于编译期间生成。

虽然类型参数化是 Julia 语言一项非常有用的特性，但参数化也可以针对整数值进行。

```
julia> struct Point{T<:AbstractFloat, N}
           x::Vector{T}
       end
```

```
julia> p = Point{Float32, 2}([1f0, 2f0])
Point{Float32,2}(Float32[1.0, 2.0])
```

正如所见，类型中使用的 `N` 是一个作为类型参数使用的整数。

## 类型操作

有一些适用于类型的操作。我们迄今已见过其中一些，将在本节详细阐述。

### typeof

此函数提供与类型实例相关联的具体类型。

```
julia> a = 1//2<a id="ftn7a" href="#ftn7"><sup>7</sup></a>

1//2
julia> typeof(a)
Rational{Int64}
```

#### 别名

类型本身是 `DataType` 类型的实例。

```
julia> typeof(Int)
DataType
julia> typeof(Rational{Int})
DataType
```

像其他实例对象一样，它们可以被比较和赋值。以下是来自 base/boot.jl 的代码片段。8

```
if Int ===<a id="ftn9a" href="#ftn9"><sup>9</sup></a> Int64
    const UInt = UInt64
else
    const UInt = UInt32
end
```
