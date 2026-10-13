
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
