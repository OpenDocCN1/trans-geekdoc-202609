
# Julia 字符串操作

## 字符串索引

就像其他集合一样，Julia 字符串也支持基于 1 的索引，并在每个位置呈现字符。

```julia
julia> s[1], s[2], s[3], s[4], s[5]
('J', 'u', 'l', 'i', 'a')
```

`begin` 和 `end` 可以像用于其他类型的集合一样使用。

```julia
julia> s[begin], s[begin+2], s[end-1], s[end]
('J', 'l', 'i', 'a')
```

让我们看一个包含多字节 UTF-8 字符的字符串。

```julia
julia> s = "\u2200 x \u2203 y"
"∀ x ∃ y"
julia> length(s)   # 字符串中的字符数
7
julia> sizeof(s)   # 字符串中的字节数
11
```

```julia
julia> s[1]
'∀': Unicode U+2200 (category Sm: Symbol, math)
```

```julia
julia> s[2]
StringIndexError("∀ x ∃ y", 2)

Stacktrace:
 [1] string_index_err(::String, ::Int64) at .\strings\string.jl:12
 [2] getindex_continued(::String, ::Int64, ::UInt32) at .\strings\string.jl:220
 …
```

```julia
julia> s[4]
' ': ASCII/Unicode U+0020 (category Zs: Separator, space)
```

所以，`getindex` 方法以字节索引作为输入并返回一个有效字符。然而，当索引不映射到有效字符时，会抛出异常，如 `s[2]` 所示。不过，`for...in` 循环可以按字符迭代。

```julia
julia> for c in s
       println(c)
       end
∀
x
∃
y
```

使用索引变量的另一种方法是 `nextind()` 方法。该方法返回包含有效字符的下一个索引。

```julia
julia> i, l = firstindex(s), lastindex(s);

julia> while i <= l
       println(s[i])
       i = nextind(s, i)
       end
∀
x
∃
y
```

## 字符串分割与拼接

将字符串分割为子字符串的最简单方法之一是使用索引和 `*` 运算符进行拼接。

```julia
julia> str = "This is a String"

julia> str[1:4]
"This"

julia> str[1:4]*str[end-6:end]
"This String"
```

- 由于字符串是不可变的，每次子字符串或拼接操作都会在拼接前分配中间字符串。可以使用 `repeat` 函数或别名运算符 `^` 创建文本模式的重复序列。

```julia
julia> repeat("A:-", 5)
"A:-A:-A:-A:-A:-"

julia> "A:="^4
"A:=A:=A:=A:="
```

- `join()` 组合输入的字符串集合。可以选择提供分隔符（如逗号 `,`）和最后的连接词（如 `and`）。

```julia
julia> join(["1", "2", "3", "4", "5"])
"12345"

julia> join(["Jack", "Jill", "Cathy", "Trevor"], ", ", " and ")
"Jack, Jill, Cathy and Trevor"
```

- `chomp()` 移除字符串中最后的行尾字符。

```julia
julia> str = "This is a\nString\n"

julia> chomp(str)
"This is a\nString"
```

- `chop()` 从头部和尾部移除字符。默认情况下，头部不移除字符，尾部仅移除一个字符。不过，可以使用关键字 `head` 和 `tail` 分别指定从头部和尾部移除的具体字符数。

```julia
julia> chop("October")
"Octobe"

julia> chop("October", head=2, tail=3)
"to"
```

- `split()` 方法沿空格字符分割 `String` 并返回 `SubString` 对象数组。

```julia
julia> s = "\u2200 x \u2203 y"

julia> ss = split(s)
4-element Array{SubString{String},1}:
 "∀"
 "x"
 "∃"
 "y"
```

- `String` 对象是不可变的，任何提取字符串一部分的表达式都会分配一个新的 `String`。`SubString` 是 `String` 对象的视图。在前面的示例中，数组中所有分割的 `SubString` 对象都指向同一个 `String` 对象。`SubString` 对象扩展了 `AbstractString` 接口，因此在需要时可以转换为 `String` 对象。`split()` 方法也支持分隔符。

```julia
julia> s = "\u2200,x,\u2203,y"

julia> ss = split(s, ',', limit=2)
2-element Array{SubString{String},1}:
 "∀"
 "x,∃,y"

julia> s = "\u2200,x,\u2203,y"

julia> ss = rsplit(s, ',', limit=2)
2-element Array{SubString{String},1}:
 "∀,x,∃"
 "y"
```

`split()` 示例使用逗号 `,` 作为分隔符，并将分割部分的数量限制为 2。与从左侧分割字符串的 `split` 非常相似，`rsplit` 从右侧分割字符串。

- `lpad` 和 `rpad` 向字符串添加前缀或后缀，使其达到特定长度。

```julia
julia> lpad("string", 10, "p")
"ppppstring"

julia> rpad("string", 10, "s")
"stringssss"
```

- `strip` 函数移除字符串两侧的空格字符。该函数的一个方法可以选择性地接受一个字符数组，从两端移除这些字符。返回 true 的谓词也可用于从两端剥离。`lstrip` 和 `rstrip` 是两个功能类似的函数，但分别仅作用于字符串的左端和右端。

```julia
julia> strip("    string 123  ")
"string 123"

julia> strip(" {a}    string 123  ", ['{', 'a', '}', ' '])
"string 123"

julia> strip("    string 123  aaa") do x
       return x == ' ' || x == 'a'
       end
"string 123"
```

## 大小写转换

一些函数及其预期结果：

```julia
julia> uppercase("Julia")
"JULIA"

julia> lowercase("JUliA")
"julia"

julia> titlecase("hands on programming in julia")
"Hands On Programming In Julia"

julia> uppercasefirst("julia")
"Julia"

julia> lowercasefirst("Julia")
"julia"
```

## 模式匹配

模式匹配函数可分为多种类别。其中一些如下：

- `startswith()`、`endswith()` 和 `contains()` 在字符串的开头、结尾和任意位置搜索一部分字符串，并返回它们是否存在于字符串中。`occursin(needle, haystack)` 是 `contains(haystack, needle)` 的另一种形式。

```julia
julia> str = "Introduction to Julia";
```
