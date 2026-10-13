
当两点之间的距离小于某个称为 `point coincident tolerance`（点重合公差）的微小值时，这两点被称为重合点。[^6] 鉴于上述条件，我们如何判断三个这样的点是共线的或构成一条直线？

![Figure 13.3](n4upl4fndrr.jpeg)

**Figure 13.3:** (a) 如果 –ε < δ < ε，则点 A 和 B 为同一点。(b) 如果 AB、BC 或 AC 中任意两点过于接近，则三点 ABC 共线。(c) 但 (b) 不充分，如图所示 B 点可以非常接近直线 AC。

从图中显然可知，要使 ABC 共线，三角形面积必须非常小：

![Triangle area formula](n4upl4fndrs.jpeg)

其中 δ 为高，L 为最长边的长度（在本例中为 BC）。如果

![Collinearity condition](n4upl4fndrt.jpeg)

其中 ϵ 为点重合公差，则我们知道这些点是共线的。三角形面积（可使用行列式计算[^7]）：

![Determinant formula](n4upl4fndru.jpeg)

---

我们将该包命名为 `PointLib`，并通过以下步骤进行初始化：

1.  将目录切换到您想要创建 `PointLib` 包的工作区。
2.  在 Julia REPL 提示符 `julia>` 下输入字符 `]`。提示符将变为 `(@1.6) pkg>`。此提示符称为包模式。
3.  使用命令：`generate PointLib`。
4.  将创建一个名为 PointLib 的新目录，包含以下文件：

    ```
    shell> tree /F[^8]
    Folder PATH listing
    Volume serial number is E285-F8B9
    C:.
    │   Project.toml
    └───src
            PointLib.jl
    ```

5.  `Project.toml` 将包含以下元数据：

    ```
    shell> more Project.toml
    name = "PointLib"
    uuid = "7de1f589-fb91-4994-b265-ccfc43c44ada"
    authors = ["Sambit Kumar Dash <sambitdash@gmail.com>"]
    version = "0.1.0"
    ```

6.  `src/PointLib.jl` 是包的代码入口点，将包含以下代码。一个与包名匹配的默认模块。一个作为示例代码的 greet 函数。

    ```julia
    module PointLib
    greet() = print("Hello World!")
    end # module
    ```

7.  使用 `cd("PointLib")` 进入该文件夹，并使用命令 `]activate .`。activate 后面的点 (`.`) 确保在当前目录中激活环境。这会将提示符更改为 `(PointLib) pkg>`，确认正在使用 `PointLib/Project.toml` 中定义的环境。

8.  向 `PointLib` 包添加 `LinearAlgebra` 库。根据注册表更新情况，这可能需要一些时间。

    ```
    (PointLib) pkg> add LinearAlgebra
     Updating registry at `D:\Users\sambi\.julia\registries\General`
    Resolving package versions…
     Updating `C:\Users\sambi\PointLib\Project.toml`
    [37e2e46d] + LinearAlgebra
     Updating `C:\Users\sambi\PointLib\Manifest.toml`
    [8f399da3] + Libdl
    [37e2e46d] + LinearAlgebra
    ```

    `Project.toml` 将包含一个依赖项条目。并将创建一个新文件 `Manifest.toml`，用于解析所需的完整包列表。例如，`LinearAlgebra` 需要 `Libdl`，该信息将更新在 `Manifest.toml` 中。

    ```
    shell> more Project.toml
    name = "PointLib"
    uuid = "7de1f589-fb91-4994-b265-ccfc43c44ada"
    authors = ["Sambit Kumar Dash <sambitdash@gmail.com>"]
    version = "0.1.0"
    [deps]
    LinearAlgebra = "37e2e46d-f89d-539d-b4ee-838fcccc9c8e"

    shell> more Manifest.toml
    # This file is machine-generated - editing it directly is not advised
    [[Libdl]]
    uuid = "8f399da3-3557-5675-b5ff-fb832c97cbdb"
    [[LinearAlgebra]]
    deps = ["Libdl"]
    uuid = "37e2e46d-f89d-539d-b4ee-838fcccc9c8e"
    ```

因此，我们得到了一个用于开发所需功能的包，也可以将其添加到源代码控制中，以便更好地维护和共享代码。Git 管理的包可以通过 Julia 包管理器进行分发。

---

以下代码足以满足我们想要开发的功能。虽然这是初始代码，但我们将把增强功能、添加更多用例作为练习留给读者。

```julia
module PointLib
greet() = print("Hello World!") # Created by generate command
using LinearAlgebra
export Point2D, iscollinear, ϵ

struct Point2D
    x::Float64
    y::Float64
end

function ϵ end
let _epsilon = 1e-5
    global ϵ() = _epsilon
end

function length(pA::Point2D, pB::Point2D)
    x1, y1, x2, y2 = pA.x, pA.y, pB.x, pB.y
    dx, dy = x1 - x2, y1 - y2
    return sqrt(dx*dx + dy*dy)
end

∆(pA::Point2D, pB::Point2D, pC::Point2D) =
    0.5 * det([pA.x pA.y 1; pB.x pB.y 1; pC.x pC.y 1])

L(pA::Point2D, pB::Point2D, pC::Point2D) =
    max(length(pA, pB), length(pB, pC), length(pC, pA))

function iscollinear(pA::Point2D, pB::Point2D, pC::Point2D)
    l = L(pA, pB, pC)
    # The longest length is too small if all the points
    # are coincident
    # This a special case to avoid divide by zero.
    l <= ϵ() && return true
    return 2∆(pA, pB, pC) / l <= ϵ()
end

end # module
```

模块一旦加载后不会自动更新。您需要关闭 Julia 会话，或使用像 `Revise.jl`[^9] 这样的包，才能在包内重新加载新的符号。

---

程序开发完成后，理想情况下应将其签入源代码控制系统的项目中。我们建议为此使用基于 Git 的在线仓库，如 GitHub。请遵循以下步骤操作：

1.  登录 GitHub：<https://www.github.com>
2.  创建一个名为 `PointLib.jl` 的新仓库。按照惯例，Julia 包的名称通常带有 `.jl` 后缀。
3.  您可以使用 GitHub Desktop 将 `PointLib` 文件夹添加到仓库，
    或
    在 `PointLib` 文件夹中执行以下 `git` 命令：

    ```bash
    echo "# PointLib.jl" >> README.md
    git init
    git add .[^10]
    git commit -m "first commit"
    # U 为 GitHub 用户名
    git remote add origin https://github.com/U/PointLib.jl.git
    git push -u origin master
    ```
