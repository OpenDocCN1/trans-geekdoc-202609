

# Julia 包文档开发

文档并非包管理的核心功能。然而，要使包对受众有用，文档起着重要作用。因此，我们在此讨论如何为 Julia 包开发和传播文档。

Julia 文档字符串可以作为简单字符串或三重引用字符串块添加在任何函数或类型定义之前。文档字符串可以包含用于文档标记的 Markdown 语法，如标题、粗体、斜体或表格等。让我们为 `PointLib` 包的所有公共 API 添加一些此类文档字符串。

```julia
"Sample module to show how packages are built"
module PointLib
    …
    """
    Point2D

    ``` 
    x: Float64 x-cordinates
    y: Float64 y-cordinates
    ```
    """
    struct Point2D
        …
    end

    "Returns the point coincident tolerance value"
    function ϵ end
    …
end
```

你可以通过在帮助模式下输入函数或类型名称来测试文档字符串。当你输入字符 `?` 时，REPL 会切换到帮助模式。

```julia
julia> using PointLib
help?> Point2D
search: Point2D pointer PointLib pointer_from_objref codepoint unsafe_pointer_to_objref
Point2D
  x: Float64 x-coordinates
  y: Float64 y-coordinates

help?> PointLib
search: PointLib
Sample module to show how packages are built
```

虽然文档字符串对于查找特定方法和类型的帮助很有用，但你也需要为整个包提供详尽的文档。这通过一个名为 `Documenter.jl` 的包来实现。

## 文档构建流程

按照惯例，文档在包下的 `docs` 文件夹中创建。在我们的示例中：

1. 我们将创建一个 `PointLib/docs` 文件夹。
2. 进入该文件夹并启动 Julia。
3. 我们需要通过命令 `]activate` 实例化项目。这会将包模式提示符更改为 `(docs) pkg>`。
4. 在包模式下，我们需要使用以下命令：
   ```julia
   (docs) pkg> add ..
   (docs) pkg> add Documenter
   ```
   `add ..` 命令将添加未在 Julia 注册表中注册但文档交叉引用所需的 `PointLib` 包。
5. 在 `docs` 文件夹中，我们将创建一个包含以下内容的 `make.jl` 文件：
   ```julia
   if Base.HOME_PROJECT[] !== nothing
       # JuliaLang/julia/pull/28625
       Base.HOME_PROJECT[] = abspath(Base.HOME_PROJECT[])
   end
   using Documenter, PointLib
   makedocs(
       format = Documenter.HTML(),
       modules = [PointLib],
       sitename = "PointLib",
       pages = [
           "README.md",
           "API Reference" => "index.md"
       ]
   )
   deploydocs(
       repo = "github.com/sambitdash/PointLib.jl.git",
   )
   ```
6. `makedocs` 方法中引用的页面在 `PointLib/docs/src` 目录中查找。用户必须创建此目录。并且应将以下文件放置在 `src` 目录中。
7. `README.md` 文件包含项目的标准 README。
8. `index.md` 文件包含 API 参考。相关文档字符串将从源代码中提取并插入到参考位置。`index.md` 包含代码 ```` ```@docs <methods or types> ``` ````，文档字符串将在构建过程中嵌入其中。

   ```markdown
   # Reference
   This page has references to all the exported types and functions.
   ## Types
   ```@docs
   Point2D
   ```
   ## Functions
   ```@docs
   ϵ
   iscollinear
   ```
   ```
