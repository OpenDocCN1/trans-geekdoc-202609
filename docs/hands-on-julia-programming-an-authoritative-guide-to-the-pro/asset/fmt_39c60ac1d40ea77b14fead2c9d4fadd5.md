
**Figure 2.1:** Hierarchy of numeric types

# Primitive Types

Primitive types are data types that LLVM supports. Julia compiles the code to LLVM equivalent and subsequently to a native CPU machine code for execution in a **JIT** fashion. Hence, it is quite logical to bring in the LLVM types into Julia. These primitive types are bit values. Here are a set of primitive types defined in Julia.

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

While users can define their own primitive types, it is advisable to use the already defined primitive types and define newer ones when the existing ones cannot serve the purpose. Second, primitive types of the same bit values are not essentially interchangeable or can be converted seamlessly. The type hierarchy plays an important role in the behavior of such types.

```julia
julia> UInt32(3f-1)
ERROR: InexactError: UInt32(0.3)
```

Even though they are both 32-bit entities, a single-precision float cannot be represented as an unsigned integer in every situation. Third, you cannot create primitive types of arbitrary bit sizes. Only bit sizes that are multiples of 8-bits are supported.

```julia
julia> primitive type MyType1 40 end
julia> primitive type MyType2 4 end
ERROR: invalid number of bits in primitive type MyType2 …
```

# Bit Types

Julia interoperates seamlessly with languages that operate on a binary interface like C/C++, FORTRAN, and other natively compiled languages. In such a condition, it is imperative to expect certain data types defined in Julia are consistent in binary layout to be used by these natively compiled languages. Such types are known as **Bit Types**. The primitive types are all of bit typed data types. Certain composite data types are bit types. We will discuss about them further when we encounter them. The bit types can be queried with the function `isbits` on an instance and `isbitstype` on a type.

```julia
julia> a = 10
10

julia> isbits(a)
true

julia> isbitstype(Int)
true
```

# Rational and Complex Types

`Rational` and `Complex` data types though numeric types are not primitive types. They are created using composite data types that we will review as part of user-defined types.

# Char Type

`Char` is a character represented as a 32-bit value. It can be a valid UCS-4 representation of a Unicode character. We will discuss in details `Char` and its relationship with `String` in the chapter on Strings. `AbstractChar` abstract type is provided such that one can develop her own char-like data types.

# Strings

Strings are collection of characters. While most of the strings are composed of Unicode character codes, they can store other kinds of binary data as well. `AbstractString` abstract type is provided so that advanced users can define custom string types. We will discuss these in detail in a later chapter.

# Composite Types

While Julia provides quite a few built-in types, there is always a need to have data types that are composite and may require various attributes be grouped together.

## Immutable Composite Types (`struct`)

These types cannot have their attributes modified once they are defined. These immutable data types are represented as `struct` in Julia.

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

As can be seen, `Rectangle` is a `struct` defined and which is initialized with values `10.0` and `20.0`. The values of attributes cannot be modified. The initialization is carried out with `Rectangle(10.0, 20.0)`. This is a special purpose function. We shall know more about when we discuss functions and methods.

## Mutable Composite Types (`mutable struct`)

Suppose we were to make the `Rectangle` mutable we could have created a mutable struct as shown as follows:

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

As can be seen, the attribute values are modified after instantiating the object. Composite data types in Julia can also be derived from an `abstract type`.

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

## Composite Type Behavior and Constructors

The composite types in Julia have member attributes and no member functions or methods. The Julia multi-dispatch architecture is used to make functions behave like methods for specific types, but they are not the same as methods in an object-oriented language. There is a special category of functions that can be a member of a type. Those are called **constructors**. We will review constructors in details as we discuss about functions. The type information of members is not always to be specified in a composite type.

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

While in the preceding example, the ambiguity is resolved when an object is instantiated, one can never be sure of the type as dynamically member attribute can be assigned to another type.

```julia
julia> a.member = "String"
"String"

julia> typeof(a.member)
String
```
