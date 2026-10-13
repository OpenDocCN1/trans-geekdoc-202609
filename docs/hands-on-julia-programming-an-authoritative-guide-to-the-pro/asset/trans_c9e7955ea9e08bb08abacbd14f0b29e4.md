

# 9. 使用 Documenter.jl 构建文档

现在，在 docs 目录下运行 `make.jl`。您将在 build 目录中看到 HTML 模式下的文档。

```julia
julia> include("make.jl")
[Info: SetupBuildDirectory: 正在设置构建目录。
[Info: Doctest: 正在运行文档测试。
[Info: ExpandTemplates: 正在扩展 Markdown 模板。
[Info: CrossReferences: 正在构建交叉引用。
[Info: CheckDocument: 正在运行文档检查。
┌ Warning: 2 个文档字符串未包含在手册中：
│     PointLib.PointLib
│     PointLib.greet :: Tuple{}
│ 这些是受检查模块中的文档字符串（通过 modules 关键字配置）
│ 未包含在 @docs 或 @autodocs 块中。
└ @ Documenter.DocChecks D:\Users\sambi\.julia\packages\Documenter\FuXcO\src\DocChecks.jl:69
[Info: Populate: 正在填充索引。
[Info: RenderDocument: 正在渲染文档。
[Info: HTMLWriter: 正在渲染 HTML 页面。
┌ Warning: Documenter 无法自动检测构建环境，跳过部署。
└ @ Documenter D:\Users\sambi\.julia\packages\Documenter\FuXcO\src\deployconfig.jl:75
```

在流程结束时，我们将看到 *Reference API* 页面已填充在 `build/index.html` 页面中：

![](n4upl4fndrv.jpeg)

**图 13.4：** PointLib 的示例 API 参考

文档可以使用像 GitHub Actions 这样的持续集成工具部署到 GitHub Pages。

## 10. 为源代码控制做准备

然而，在继续之前，请确保您已将所有源文件添加到源代码控制中。

1.  向您的包 `PointLib` 添加一个包含 `docs/build/*` 的 `.gitignore` 文件。此文件夹作为 Documenter 的输出被创建，无需同步到源代码控制。
2.  运行 `git add .`，以便将所有其他源文件添加到您的仓库中。
3.  现在使用 `git commit` 命令或您习惯的任何其他 GUI 工具提交您的源代码。
4.  将您的更改推送到 GitHub 仓库以完全更新它。

现在所有源代码都已在源代码控制中，您将希望确保触发持续集成工作流，以便在创建文档的同时进行自动化测试。文档也必须发布到预定义的位置。

# 使用 GitHub Actions 进行持续集成

市场上有许多持续集成平台。GitHub Actions 是 GitHub 环境中使用最广泛的框架之一。我们将使用 GitHub Actions 来自动化 Julia 项目的测试、覆盖率和文档创建任务的执行。

1.  GitHub Actions 位于一个名为 `.github/workflows` 的文件夹中，以 yaml 文件的形式存在。我们将创建一个名为 `ci.yml` 的文件并研究集成框架的各个方面。
2.  **事件**：yaml 文件的第一部分是触发 action 的事件。

    ```yaml
    name: CI
    on:
      push:
        branches: [master]
        tags: ["*"]
    ```

3.  **作业**：接下来我们指定作为 action 触发一部分运行的作业。作业的 id 可以是任何名称，如 `myjob`。我们使用 `test` 和 `doc` 来表示我们想要执行的两类作业。
4.  **测试作业**：测试作业所做的远不止运行单元测试。它们有助于设置环境、检出代码、运行相关的单元测试，并将覆盖率结果提交到 `codecov.io` 以进行可视化。
5.  **设置操作环境**：

    ```yaml
    jobs:
      test:
        name: Julia ${{matrix.version}} - ${{matrix.os}} - ${{matrix.arch}} - ${{github.event_name}}
        runs-on: ${{matrix.os}}
        strategy:
          fail-fast: false
          matrix:
            version:
              - '1.0'
              - '1' # 自动扩展到最新的稳定 1.x 版本 Julia
              - nightly
            os:
              - ubuntu-latest
            arch:
              - x64
            include:
              # 仅使用最新 Julia 测试 macOS 和 Windows
              - os: macOS-latest
                arch: x64
                version: 1
              - os: windows-latest
                arch: x64
                version: 1
    ```

    您可以选择指定操作系统版本、Julia 版本，也可以指定特定操作系统与 Julia 版本的细粒度组合。最好选取一个示例 `ci.yml` 并根据需要进行修改，而不是从头编写。

6.  **步骤**：测试作业要执行的步骤如下：

    ```yaml
    steps:
      - uses: actions/checkout@v2
      - uses: julia-actions/setup-julia@v1
        with:
          version: ${{matrix.version}}
          arch: ${{matrix.arch}}
      - uses: actions/cache@v1
        env:
          cache-name: cache-artifacts
        with:
          path: ~/.julia/artifacts
          key: ${{runner.os}}-test-${{env.cache-name}}-${{hashFiles('**/Project.toml')}}
          restore-keys: |
            ${{runner.os}}-test-${{env.cache-name}}-
            ${{runner.os}}-test-
            ${{runner.os}}-
      - uses: julia-actions/julia-buildpkg@v1
      - uses: julia-actions/julia-runtest@v1
      - uses: julia-actions/julia-processcoverage@v1
      - uses: codecov/codecov-action@v1
        with:
          file: lcov.info
    ```

    步骤不必在 steps 部分定义。相反，它们是从 GitHub Actions 和 Julia Actions 项目中开发的几个预定义脚本中获取的。这使得步骤具有声明性。

7.  **文档作业**：调用 `makedocs` 并作为文档构建过程的一部分创建文档，这是我们之前见过的。

    ```yaml
    docs:
      name: Documentation
      runs-on: ubuntu-latest
      steps:
        - uses: actions/checkout@v2
        - uses: julia-actions/setup-julia@v1
          with:
            version: '1'
        - run: |
            julia --project=docs -e '
            using Pkg
            Pkg.develop(PackageSpec(path=pwd()))
            Pkg.instantiate()'
        - run: julia --project=docs docs/make.jl
          env:
            GITHUB_TOKEN: ${{secrets.GITHUB_TOKEN}}
            DOCUMENTER_KEY: ${{secrets.DOCUMENTER_KEY}}
    ```

8.  部署后，文档需要作为 GitHub Pages 显示。您需要使用以下代码创建一对密钥：

    ```julia
    julia> using DocumenterTools
    julia> DocumenterTools.genkeys()
    [Info: 将下面的公钥添加到 https://github.com/$USER/$REPO/settings/keys 并授予读/写权限：
    …
    [Info: 添加一个名为 'DOCUMENTER_KEY' 的安全环境变量到 https://travis-ci.com/$USER/$REPO/settings (如果使用 Travis CI 部署) 或 https://github.com/$USER/$REPO/settings/secrets (如果使用 GitHub Actions 部署)，值为：
    …
    ```

    您需要将公钥添加到 `keys` 部分。您可以使用 DOCUMENTER 作为标题。现在将私钥添加到 GitHub GUI 中项目设置的 `secrets` 部分，名称为 `DOCUMENTER_KEY`。

    **gh-pages 分支：** GitHub Pages 通常从与 master 分支分离的单独分支填充。这被称为 `gh-pages` 分支。该分支是从 master 分离创建的。命令可以从 `PointLib` 目录运行。由于代码运行是为了创建一个分离分支，请确保在继续之前已将所有代码更改提交到 master 分支。

    以下是手动创建 `gh-pages` 分支的命令：

    ```bash
    # 创建 gh-pages 分支
    git checkout --orphan gh-pages
    git rm -rf .
    touch README.md
    git add README.md
    git commit -m 'initial gh-pages commit'
    git push origin gh-pages
    ```

9.  配置带有 GitHub Pages 的 gh-pages 分支：在 PointLib 设置页面的 `GitHub Pages` 部分，您可以将 `gh-pages` 配置为网页的来源：

    ![](n4upl4fndrw.jpeg)

    **图 13.5：** GitHub Pages 配置为 gh-pages 分支

10. 所有配置就绪后，下一次推送到 GitHub 仓库时，GitHub Actions 将被触发，运行结果可从项目的 `Actions` 选项卡报告：

    ![](n4upl4fndrx.jpeg)

    **图 13.6：** Actions 选项卡显示作业状态和每个步骤的详细信息

11. 最终文档将可从以下位置访问：`https://<USER>.github.io/PointLib.jl/dev/`

# 使用 Codecov.io 进行代码覆盖率

前面我们已经看到了如何为测试用例生成覆盖率数据。我们可以使用像 `codecov.io` 这样的工具查看可视化结果，并希望在成功的测试运行结束时更新它们。

1.  进入 `PointLib.jl` 的设置并将其标记为公开包。
2.  使用 GitHub 凭据登录 **[https://codecov.io](https://codecov.io)**。确保您的包 `PointLib.jl` 在您的个人资料中显示为列出的包。如果尚未配置，您将需要使用用户界面为该包设置 codecov。
3.  等待持续集成被触发并完成。
4.  如果您登录 **[https://codecov.io](https://codecov.io)**，您将看到带有丰富多彩可视化的代码覆盖率统计：

    ![](n4upl4fndry.jpeg)

    **图 13.7：** 测试用例未覆盖 `greet()` 而覆盖了 `ϵ()`。由 codecov.io 报告

因此，我们生成了包代码，创建了测试用例，创建了相关文档。我们在每次测试运行时将覆盖率数据更新到可视化工具，并将文档作为持续集成的一部分部署到 `GitHub Pages`。这确保了源代码的每次更改都能在适当的测试用例运行中得到反映，在覆盖率工具的帮助下确保为新引入的功能添加测试用例，并保持文档是最新的。

# 构建步骤和二进制依赖

当部署包时，会运行一个可选的预部署构建步骤，以下载包外部的数据文件、执行构建过程或将构建的二进制文件放在正确的位置等。某些构建步骤可能相当复杂；我们将以 PDFIO 包为例，看看其中执行的一些构建步骤。

*   `PDFIO` 依赖于来自 OpenSSL 库的二进制库 `zlib` 和 `libcrypto`。
*   这些库可能在操作系统中可用。库的名称可能因操作系统或发行版而异。Julia 提供 `library_dependency` 工具来解决此类问题。
*   采取的行动可能因操作系统而异。
    *   **Windows**：从特定 URL 下载预构建的二进制文件。
    *   **非 Windows**：从源代码构建库并部署到特定位置，以便只有 PDFIO 可以使用它们。

该过程可能相当复杂，但在解决所有可能的构建和部署需求方面具有高度灵活性。

然而，如果您仔细查看 `PDFIO` 的 `build.jl` 第 3 行，对于 Julia 1.3 或更高版本，构建步骤会被完全忽略。这之所以成为可能，是因为 Julia 社区现在为许多知名的二进制库提供预构建的二进制文件，并用像 `<libraryname>_jll` 这样的包名进行封装。

`PDFIO` 依赖于：

*   OpenSSL_jll
*   Zlib_jll

这些包是使用一个名为 *BinaryBuilder* 的构建模板生成工具构建的。如果您需要预构建的二进制文件，可以参考 *JuliaBinaryWrappers* 组织并查找您感兴趣的仓库，或在项目 `JuliaPackaging/Yggdrasil` 中提交 issue。您也可以使用 `BinaryBuilder` 模板构建二进制文件并为该项目做贡献。

# 调用 C 和 Fortran 代码

在 Julia 中使用原生二进制库要求 Julia 和原生库之间具有兼容的 `应用程序二进制接口` (`ABI`)。最常见的二进制文件具有 C 兼容接口，可从 Julia 访问。此类函数可以使用关键字 `ccall()` 调用。

```julia
_zlibVersion() = ccall((:zlibVersion, libz), Ptr{Cstring}, ())
```

库 `libz` 有一个名为 `zlibVersion` 的方法符号，它没有输入参数，但返回一个指向 `Cstring` 的指针。`Cstring` 是 C 风格字符串的表示，即字节数组。

或者，C 中的函数可以使用宏 `@cfunction` 调用 Julia 函数作为回调。建议感兴趣的读者查阅关于调用 C 和 Fortran 代码的手册。调用约定要求正确设置类型映射，以便能够在 C 中使用 Julia 中分配的对象，反之亦然。

`CXX.jl` 可用于将 C++ 代码与 Julia 集成。同样，`PyCall.jl` 提供 Python 库与 Julia 的集成。`JavaCall.jl` 提供从 Julia 调用 Java 代码的方法。

# 包环境：Project.toml 和 Manifest.toml

项目环境由文件 `Project.toml` 和 `Manifest.toml` 控制。`Project.toml` 包含包名、UUID、版本和直接依赖。每个依赖可能进一步依赖其他包。依赖包可能依赖于特定版本的包。

![](n4upl4fndrz.jpeg)

**图 13.8：** 包 A 依赖 B 的 v1。A 依赖 F，而 F 需要 B 的版本 3。因此，B 的 v3 将是 A 最终使用的包

在上面的示例中，假设包具有完美的向前兼容性。因此，包的任何更高版本都可以提供该包较低版本的所有功能。情况并不总是如此。有时，包会指定其依赖包的版本范围。在这种情况下，必须决定最有用或兼容的包版本。`A.jl` 的 `Project.toml` 将列出 `B.jl`、`C.jl` 和 `F.jl` 的依赖。然而，`Manifest.toml` 将在解析特定版本后计算得出，并将包含 `B.jl v3`、`C.jl v1`、`D.jl v1`、`E.jl v1`、`F.jl v2` 的信息。每当您需要复现环境时，共享 `Project.toml` 和 `Manifest.toml` 会有所帮助。然而，在大多数源代码控制 (Git) 的包中，只签入 `Project.toml`，因为 `Manifest.toml` 保持灵活，可根据环境中的其他包进行更新。虽然我们意识到包具有版本信息，但我们迄今为止尚未讨论包管理器如何知道包的位置。此类信息保存在中央注册表中。

# Julia 包注册表

包是交付功能的核心单元。一旦您开发了这样的包，自然希望将其推广给外部世界，以便能够访问和使用它。传达包信息的最佳方式是使其可供所有人使用，并通过交付生态系统进行分发。GitHub 是实现这一目标的非常有用的机制。高质量的文档充当最低限度的广告媒介。第二部分是通过 Julia 的包注册表使其可用。Julia 包生态系统拥有超过 4000 个包。这些包大多是托管在 GitHub 或 GitLab 等公共 Git 仓库中的 Git 包。注册包会被分析并变得易于搜索，文档会发布到 JuliaHub 以便于访问和云部署。每个 Julia 安装都有一个本地注册表，它会定期或在请求包更新时按需与 Julia 全局注册表同步：

![](n4upl4fndr0.jpeg)

**图 13.9：** Julia 注册表的运作。本地注册表拥有未向全局注册表注册的包的信息。然而，它会为所有已注册的包进行同步

假设在上面的示例中，我们在本地系统上开发 `A.jl` 包。因此，关于 `A.jl` 的信息目前仅在本地注册表中可用。它依赖于包 `F.jl`，后者在 GitHub 上但未向 Julia 注册表注册。当您使用 GitHub URL 而非注册包名添加包时，这是可能的。

```julia
(dir) pkg> add https://github.com/user_name/F.jl
```

然而，关于 B、C、D 和 E 包的信息都在全局云注册表中可用。注册表拥有关于包的以下信息：

1.  包的版本
2.  包的位置：这可以是带有版本标签的 Git 地址或文件系统路径
3.  包对其他包的依赖：即通常在 `Project.toml` 文件中找到的信息。

位置和依赖按包的每个版本存储。例如，如果您想在 `A.jl` 中使用 `C.jl` 时修改它，您将需要制作一个开发副本。这是使用 develop 或 `dev` 命令完成的。

```julia
(A) pkg> dev C
```

`C.jl` 的 GitHub 仓库将被克隆到本地的 `$JULIA_DEPOT_PATH/dev` 中。包管理器与本地注册表交互，在需要更新此类信息时用云注册表的内容更新它。它还确保包与项目的环境要求一致。`Manifest.toml` 也是由包管理器在为项目解析依赖后生成的：

![](n4upl4fndr1.jpeg)

**图 13.10：** Julia depot 文件夹结构

`JULIA_DEPOT_PATH` 是一个有用的目录，所有包及其相关信息都驻留于此。它们还包含包的预编译副本和构建的二进制文件。默认配置为 `$USER_HOME/.julia` 文件夹。必须注意，无论项目环境的数量如何，Julia 安装中只存在一个 depot。相关版本的包会根据各种环境的需要下载并在它们之间共享。Julia depot 或任何其他文件或包相关的数据结构不应直接操作。Julia 提供了广泛的命令行接口和 API 来帮助满足此类需求。

# 包管理器 REPL 模式

可以使用字符 `]` 切换到 REPL 的 pkg 模式。进入 pkg 模式后，您可以使用 `add` 向项目添加包，使用 `rm` 从项目中移除包。`update` 命令更新注册表并从全局服务器下载最新注册表。像包一样，注册表在 Julia 中也是一个 Git 仓库。就像方法和类型一样，可以通过在前面加上问号 (`?`) 来请求包命令的帮助。`?add` 将在 REPL 上打印命令行帮助。

# 使用 Pkg.jl 进行编程式包管理

虽然 REPL 命令对交互式会话非常有帮助，但在脚本或包含在 Julia 程序中时可能并不完全有用。在这种情况下 `Pkg` 模块非常方便。像 `add()`、`rm()` 等方法提供了与命令行类似的功能。就像命令行的参数一样，参数可以提供给函数调用。

Julia 中的包管理非常详尽。然而，我们只是通过概览触及了表面。用户应该习惯使用包，并在使用 Julia 的过程中学习复杂操作。由于 Julia 包管理的许多方面都是使用 Git 实现的，良好的 Git 知识也会非常有帮助。

# 章节总结

在本章中，我们从理解模块、包和项目开始。我们扩展了 8 皇后谜题以包含用户界面和图形。我们还创建了一个示例包，开发了测试用例、文档，并确保代码覆盖率相对于测试用例是充分的。然后我们讨论了 Julia 包注册的工作原理。简而言之，我们讨论了开发生产就绪 Julia 应用程序所需的初始级别细节。在下一章中，我们将学习在云环境中部署应用程序。

# 练习

1.  选择一个您想解决的实际问题。研究您想如何解决该问题的设计。Julia 中是否有解决该问题的所有功能？您是否知道有任何原生库可以解决此类问题？创建您的项目并开始构建您的解决方案。
2.  一旦您构建了解决方案并使其达到合理的形状，将其注册为 Julia 生态系统的包。其他人使用它真的需要注册包吗？
3.  您开发的 `PointLib` 包中是否有足够的测试用例？如何扩展测试用例？添加一些相关的用例，并确保添加了更好的用例。
4.  `PointLib` 中的 `iscollinear` 函数接受三个点作为参数。是否有办法将其扩展到 N 个点，其中 N 大于 3？
5.  开发一个项目，利用您已有的 PointLib。

---

# 参考文献

[1] 作者开发了一个 PDF 读取库 (PDFIO) 作为他的第一个实际 Julia 项目。虽然第一个项目可能有一定的局限性和不足，但它提供了一个从错误中学习并从社区用户和贡献者那里获得反馈的绝佳机会。

Dash, Sambit Kumar, PDFIO: PDF Reader Library for native Julia, The Journal of Open Source, Nov. 2019, **[https://doi.org/10.21105%2Fjoss.01453](https://doi.org/10.21105%2Fjoss.01453)**

[2] 与其他 Git 仓库（如 GitLab 或任何私有仓库）的集成也存在。

[3] 启动代码可在关联目录 Chaper-13/NQueens 中找到。

[4] Packages, JuliaHub, **[https://juliahub.com/ui/Packages](https://juliahub.com/ui/Packages)**。还有其他一些可以搜索 Julia 包的位置。 **[https://julialang.org/packages/](https://julialang.org/packages/)**

[5] VS Code IDE 不受支持。 **[https://github.com/JuliaGizmos/WebIO.jl/issues/168](https://github.com/JuliaGizmos/WebIO.jl/issues/168)**

[6] 浮点数本质上是不精确的。您无法在有限的二进制系统中精确表示 0.1。它将是无限级数：0.000110011… 这类似于十进制浮点系统中 ⅓ 表示为 0.333…。因此，大多数浮点比较都在容差范围内进行，而不是判断相等。当 –ε < a-b < ε 时，您说 a = b，其中 a 和 b 是浮点数。这里将其扩展到 CAD 系统中的二维。

[7] 通常使用代数表达式 1 ⁄ 2 *\[(x[A] - x[B]) (y[B] - y[C]) - (x[B] - x[C]) (y[A] - y[B])*\]。我们使用行列式表达式只是为了给项目增加额外的模块。

[8] `trees` 命令仅在 Windows 中可用。对于 Linux 和 Mac OS X，可以使用 `ls –lR`。

[9] Revise.jl, GitHub Repository, **[https://github.com/timholy/Revise.jl](https://github.com/timholy/Revise.jl)**

[10] `git add .` 将整个目录及其内容添加到 Git 仓库。如果您想排除某些文件，请有选择地将它们从同步中移除。

[11] `sambitdash/PointLib.jl` 是供参考的示例项目副本。这不是解决方案。读者应开发自己的个人仓库并进行扩展。 **[https://github.com/sambitdash/PointLib.jl](https://github.com/sambitdash/PointLib.jl)**

[12] Documenter.jl: A Documentation Generator for Julia, GitHub Repository, **[https://github.com/JuliaDocs/Documenter.jl](https://github.com/JuliaDocs/Documenter.jl)**

[13] 与其从头编写 ci.yml，不如查看 `Example.jl` 包中包含的一个： **[https://github.com/JuliaLang/Example.jl](https://github.com/JuliaLang/Example.jl)**

[14] GitHub Actions Scripts, **[https://github.com/actions](https://github.com/actions)**

[15] Julia Actions, **[https://github.com/julia-actions](https://github.com/julia-actions)**

[16] 您可以暂时向您的包添加 `DocumenterTools` 包，并在生成密钥对后从包依赖中移除该包。

[17] **[https://gist.github.com/skratchdot/1ef433c666066389201a](https://gist.github.com/skratchdot/1ef433c666066389201a)**

[18] Codecov 为 GitHub 公共包提供免费集成。此外，公共仓库无需配置任何仓库密钥。

[19] 构建步骤在文件 `deps/build.jl` 中描述，可通过包模式命令 `build` 调用。该文件可从以下链接引用： **[https://github.com/sambitdash/PDFIO.jl/blob/v0.1.12/deps/build.jl](https://github.com/sambitdash/PDFIO.jl/blob/v0.1.12/deps/build.jl)**

[20] 高级用户请参考 `BinDeps` 包以获取更多详情。 **[https://github.com/JuliaPackaging/BinDeps.jl](https://github.com/JuliaPackaging/BinDeps.jl)**

[21] BinaryBuilder, GitHub Repository, **[https://github.com/JuliaPackaging/BinaryBuilder.jl](https://github.com/JuliaPackaging/BinaryBuilder.jl)**

[22] JuliaBinaryWrappers, GitHub Organization, **[https://github.com/JuliaBinaryWrappers/](https://github.com/JuliaBinaryWrappers/)**

[23] Yggdrasil, GitHub Repository, **[https://github.com/JuliaPackaging/Yggdrasil/](https://github.com/JuliaPackaging/Yggdrasil/)**

[24] `Inflate.jl`, `PDFIO` GitHub Repository, **[https://github.com/sambitdash/PDFIO.jl/blob/v0.1.12/src/Inflate.jl](https://github.com/sambitdash/PDFIO.jl/blob/v0.1.12/src/Inflate.jl)**

[25] Calling C and Fortran Code, Julia Documentation Manuals, **[https://docs.julialang.org/en/v1/manual/calling-c-and-fortran-code/](https://docs.julialang.org/en/v1/manual/calling-c-and-fortran-code/)**

[26] `Cxx.jl`, GitHub Repository, **[https://github.com/JuliaInterop/Cxx.jl](https://github.com/JuliaInterop/Cxx.jl)**

[27] `PyCall.jl`, GitHub Repository, **[https://github.com/JuliaPy/PyCall.jl](https://github.com/JuliaPy/PyCall.jl)**

[28] `JavaCall.jl`, GitHub Repository, **[https://github.com/JuliaInterop/JavaCall.jl](https://github.com/JuliaInterop/JavaCall.jl)**

# 第 14 章：在云端部署 Julia 应用程序

我们已经了解了开发 Julia 应用程序所使用的工具。现在我们将在云环境中部署我们的应用程序。Julia 适合基于服务器的计算，云是此类系统的自然部署选择。

## 本章我们将学习以下主题：

*   云环境
*   部署 Julia
*   Kubernetes
*   公共云基础设施

您将大致了解如何将 Julia 应用程序作为 Web 服务部署在 Docker 容器中，然后使用 Julia 命令将容器带到 Kubernetes 服务进行部署和编排。您还可以使用 Julia 命令作为集成平台来管理 *AWS*、*Azure* 和 *Google Cloud* 服务。因此，您可以将 Julia 用作许多云部署活动的客户端接口。

## JuliaHub：原生 Julia 云环境

Julia 是为科学计算设计的环境。它广泛用于基于服务器的计算。因此，许多生产 Julia 部署都在云环境中进行。云环境有其独特的挑战。Julia 作为一种语言不限制自己于任何特定的云平台。然而，与云提供商的集成程度在不断演变，并且在任何时间点能力各异。Julia Computing 提供了一个 *JuliaHub* 环境，它与 Julia 开发环境紧密集成。我们之前已经看到了与 VS Code IDE 的集成。提供了一个详尽的教程，通过该教程可以将工作负载部署到 *JuliaHub* 并作为分布式应用程序运行。

*JuliaHub* 提供用户界面来搜索和发现包，并允许开发和注册自己的包。包可以构建并注册为应用程序，这本质上意味着添加 main 方法并指定环境，然后可以多次运行或与 *JuliaHub* 的其他用户共享。*JuliaHub* 还提供企业计划，用户可以拥有私有注册表和包，并对包有更严格的控制以符合公司政策。分布式应用程序可以按需扩展，只需按一下按钮即可从单节点扩展到数百个节点。*JuliaHub* 可以是使用纯 Julia 环境的人的一个好选择。但对于不同类型的应用程序、大型基础设施，甚至纯粹的商业原因，人们可能更倾向于其他知名的 IaaS 或 PaaS 解决方案。

*JuliaHub* 界面简单，只需要最少的资源配置，如下截图所示：

![](n4upl4fndql.jpeg)

**图 14.1：** JuliaHub 提供一个简单的分布式环境，可配置 CPU 和内存数量

在后台，*JuliaHub* 以透明的方式管理日志监控、调度和分布式处理。这显著减少了复杂系统的管理和部署开销。建议读者参考文档以详细了解 *JuliaHub*。

## Docker：容器化 Julia 应用程序

如果您查看任何 Julia 包的 GitHub Actions，您会意识到大多数都遵循以下高级步骤：

1.  **安装 Julia**：根据平台和操作系统，需要下载并安装正确的二进制文件。
2.  **设置 Julia**：安装需要配置在路径中，以便相关用户可以使用。
3.  检出要测试的包。
4.  **实例化包环境**：这可能会安装运行应用程序所需的所有依赖包。
5.  启动环境并测试包。

虽然大多数这些可以通过自定义脚本实现，但考虑到工作的重复性和部署平台的广泛多样性，这可能并不理想。基于 Docker 的包被视为部署交付的事实标准。然而，自己维护此类镜像可能很困难。Julia 的自定义包管理参考实现 `PkgServer` 是一个了解使用 Docker 脚本部署完整服务器配置的好包。在下面的示例中，我们将看看更简单的示例，并将 `NQueens` 问题作为服务暴露。

### 将 Julia 函数作为 REST API 暴露

Julia 是基于服务器计算的首选环境。如果 Julia 方法可以作为 REST 端点暴露，并可从浏览器或普通 HTTP 客户端访问，那将是理想的。我们将从第 13 章中选取 N-queens 问题，尝试将计算元素作为服务器部署，而我们在本地渲染客户端，这将是典型的部署方式。`JuliaWebAPI` 提供了将 API 作为 Web 接口暴露的完美接口。

```julia
webqueens(N) = queens(parse(Int, N))

process(
    JuliaWebAPI.create_responder([
        (webqueens, true)
    ], "tcp://127.0.0.1:9999", true, ""), async=true
)

const apiclnt = APIInvoker("tcp://127.0.0.1:9999")
run_http(apiclnt, 8888)
```

这只是暴露 `queens(N)` 函数的相关代码片段。让我们详细看看：

*   服务器应用程序在端口 8888 上监听 HTTP 请求。
*   当它收到有效的 REST 请求时，它使用 JMQ 传输和 JSON 格式通过 `APIInvoker` 调用。
*   在端口 9999 上运行的 `APIResponder` 在启动相关函数并将返回值转换为 JSON 格式后进行响应。

客户端将连接到 REST 端点并获取皇后的位置并在画布上渲染。客户端代码的相关部分如下所示：

```julia
using HTTP
using JSON
using Blink
using WebIO

try
    N, W = 8, 30
    resp = HTTP.get("http://172.17.0.2:8888/webqueens/$N")
    json = JSON.parse(String(resp.body))
    allqueens = json["data"]
    w = Window()
    …
    ### 更新画布的代码
catch e
    return "Error occurred : $e"
end
```

### 构建 Docker 镜像

Docker 已成为私有和公共云基础设施容器管理的事实标准。Julia 已经在 Docker Hub 上注册了具有不同基础镜像的 Docker 镜像，可以使用以下命令拉取：

```bash
$ docker pull julia
```

所需的额外包可以在名为 `Dockerfile` 的配置文件中更新。我们现在将服务器代码部署到 Docker 容器中。示例 DockerFile 如下所示：

```dockerfile
FROM julia:latest
COPY Project.toml server.jl nqueens/
WORKDIR nqueens
RUN julia -e "using Pkg; pkg\"activate .\"; pkg\"instantiate\"; "
CMD julia server.jl
```

让我们讨论前面的代码行：

1.  我们采用基础 Julia Docker 容器。
2.  将 `Project.toml` 和 `server.jl` 复制到工作目录。
3.  我们使用 Julia 包管理更新容器。
4.  最后，我们设置容器运行时要启动的命令。

您可以使用以下命令构建 Docker 镜像：

```bash
$ sudo docker build –t queens .
```

可以使用 `docker run queens` 启动容器。您可以使用与之前相同的客户端，但请确保将服务器的 IP 地址更改为 Docker 容器的 IP 地址。`SimpleContainerGenerator` 包有助于根据某些元数据构建 DockerFile 配置。

## Kubernetes：编排容器

虽然 Docker 是容器管理的事实标准，但 Kubernetes 是云部署最常用的编排平台。云原生计算基金会认证了 90 多个支持 Kubernetes 的平台以符合 API 标准。一些知名的产品如下：

*   亚马逊网络服务的 **弹性 Kubernetes 服务 (EKS)**
*   微软 Azure 的 **Azure Kubernetes 服务 (AKS)**
*   Google 的 **Google Kubernetes Engine (GKE)**

因此，使用 Docker 创建的 Julia 容器可以使用 Kubernetes 在几乎所有知名的云平台上进行编排。`Kuber` 包提供了管理 Kubernetes 编排环境的 Julia API。关于在 Azure AKS 上使用 Kuber 编排容器的教程已经可用。该教程提供了创建新节点、启动它们的方法，并提供了删除和清理资源的步骤。各种 Kubernetes 节点和 Pod 的指标也可以从 Julia 查询。我们将尝试使用以下步骤将我们之前创建的容器部署到 **Azure Kubernetes 服务 (AKS)**：

我们需要安装 Azure **命令行界面 (CLI)**。这适用于 Windows、Mac OS X 和 Linux。

1.  使用管理员登录和以下命令登录 Azure 环境：
    ```bash
    $ az login
    ```
2.  使用以下命令在 Azure 门户中创建资源组：
    ```bash
    az group create --name HOJP --location centralindia
    ```
    您也可以使用门户执行相同操作。
3.  在 HOJP 资源组中创建 Kubernetes 集群，如下所示：
    ```bash
    $ az aks create --resource-group HOJP --name hojpcluster --node-count 1 --enable-addons monitoring --generate-ssh-keys
    ```
    对于这个实验性集群，我们仅使用一个节点。
4.  我们需要使用以下命令缓存凭据以供将来使用：
    ```bash
    $ az aks get-credentials --resource-group HOJP --name hojpcluster
    ```
5.  此外，我们需要 AKS 客户端进行某些操作，必须使用以下命令安装它：
    ```bash
    $ sudo az aks install-cli
    ```
    您将能够使用 `kubectl` 执行许多 Kubernetes 命令。
6.  `kubectl proxy` 对于通过 Web 服务连接到 Azure Kubernetes 服务很有用。
7.  您需要将 Docker 容器安装到 AKS 中。镜像必须驻留在 AKS 环境中，并必须在 Azure 容器注册表中注册，以便它们可以被拉取到容器中。您可以使用以下命令执行此操作：
    ```bash
    $ az acr create -n hojpreg -g HOJP --sku Standard
    ```
8.  注册表可能需要身份验证才能推送和拉取镜像。一种为注册表提供 Azure 管理员访问权限的方法是将注册表附加到集群。但这不建议用于真正的生产 Azure 部署。
    ```bash
    $ az aks update -n hojpcluster -g HOJP --attach-acr hojpreg
    ```
9.  现在您可以使用以下命令创建 Docker 镜像并将其推送到 Azure 容器注册表：
    ```bash
    $ docker build . -f Dockerfile -t hojpreg.azurecr.io/kubqueens
    $ docker push hojpreg.azurecr.io/kubqueens
    ```
    考虑到您的网络连接，这可能需要一些时间。镜像大小可能有几百兆字节。

### 使用 Kuber.jl 部署

现在镜像已在 AKS 注册表中注册，我们将使用 `Kuber` 包部署服务，如下所示：

1.  启动一个通过代理连接 AKS 的上下文：
    ```julia
    using Kuber
    ctx = Kuber.KuberContext()
    ```
2.  从 kubqueens 镜像获取由一个或多个容器服务的 Pod，如下所示：
    ```julia
    kubqueens_pod = kuber_obj(ctx, """
    {
    "kind": "Pod",
    "metadata":{
    "name": "kubqueens-pod",
    "namespace": "default",
    "labels": {
    "name": "kubqueens-pod"
    }
    },
    "spec": {
    "containers": [{
    "name": "kubqueens",
    "image": "hojpreg.azurecr.io/kubqueens",
    "ports": [{"containerPort": 8888}]
    }]
    }
    }""")
    ```
3.  创建一个负载均衡器服务，以便容器可以通过公共 URL 暴露。
    ```julia
    kubqueens_service = kuber_obj(ctx, """
    {
    "kind": "Service",
    "metadata": {
    "name": "kubqueens-service",
    "namespace": "default",
    "labels": {"name": "kubqueens-service"}
    },
    "spec": {
    "type": "LoadBalancer",
    "ports": [{"port": 8888}],
    "selector": {"name": "kubqueens-pod"}
    }
    }""")
    ```
4.  两个对象都必须附加到上下文以将它们部署到 AKS 集群，如下所示：
    ```julia
    put!(ctx, kubqueens_pod);
    put!(ctx, kubqueens_service);
    ```
5.  现在等待负载均衡器启动：
    ```julia
    while true
        println("waiting for loadbalancer to be configured…")
        status = get(ctx, :Service, "kubqueens-service").status
        if nothing !== status.loadBalancer.ingress &&
            !isempty(status.loadBalancer.ingress)
            println(status.loadBalancer.ingress[1])
            break
        end
        sleep(5)
    end
    ```
6.  我们可以通过使用公共 IP 地址访问 REST 端点来访问 AKS 部署的服务，如下所示：
    ```bash
    C:\>curl http://<public_IP>:8888/webqueens/8
    {"data":[4,2,7,3,6,8,5,1],"code":0}
    ```
    您也可以使用前面提到的客户端代码连接到 AKS 并渲染 UI。完整的 Kubernetes 编排器代码可以在 `Chapter-14/kubernetes/kubserver.jl` 中看到。可以通过调用 `delete!` 方法轻松移除服务，如下所示：
    ```julia
    delete!(ctx, kubqueens_service)
    delete!(ctx, kubqueens_pod)
    ```

## 公共云提供商：AWS、Azure 和 GCP

亚马逊网络服务、微软 Azure 和 Google Cloud Platform 几乎是当今可用的默认公共云基础设施。Julia 包可以连接到所有这些平台并提供服务管理 API。在大多数情况下，它们是使用这些平台的 Web 服务架构生成的，因此可以扩展以适应新开发的 API。

### AWS.jl

虽然我们可以使用 Kubernetes 编排工作负载，但原生平台提供细粒度的控制，并能跨更大的服务堆栈使用。它们不局限于基于容器的工作负载。Julia 使用包 `AWS` 提供了管理基于 AWS 服务的广泛覆盖。在所有公共云基础设施中，AWS 对 Julia 的集成迄今为止是最全面的。这很大程度上归功于使用 *GitHub Action* 的自动化代码生成，该操作每天 UTC 时间上午 6:00 执行。它查询 *GitHub* 仓库 `aws-sdk-js` 以获取基于 REST 的 API。此操作为 Julia 中的 AWS 服务生成包装函数。文档也从 AWS 文档中提取并作为 Juliadocs 展示。这确保了源代码可以适应 AWS API 和文档的所有变更。API 通常设计为两类：

*   低级 API
*   高级 API

低级 API 将 AWS 作为 URL 和 GET 或 POST 等命令进行查询。高级 API 是函数调用。每当为 AWS 函数生成 Julia 函数时，函数的驼峰命名会被修改为小写，单词以下划线 (`_`) 分隔。例如，`S3` 函数调用 `ListObjectsV2` 将变为 `list_objects_v2`。

### Azure.jl

就像 AWS 一样，`Azure` 包提供了从 Julia 客户端连接到 Azure 云基础设施的功能。客户端具有与 AWS 非常相似的架构。它使用 Swagger Java 库为 Azure 框架暴露的 REST API 生成 Julia 签名。与 AWS 不同，Azure API 的 Julia 签名是间歇性生成的，并不是自动化 GitHub Action 的一部分。我们建议读者探索这些 API 并将其用于他们的 Azure 管理需求。

### GoogleCloud.jl

`GoogleCloud` 提供了连接到 `Google Cloud Platform` (`GCP`) 的功能。它封装了 Google JSON API 并提供了一个轻量级框架来调用 GCP API。就像 AWS 和 Azure 一样，这使用 Web 服务连接框架提供了到 GCP 的连接。

## 总结

我们了解了 JuliaHub，一个简单而理想的环境，供 Julia 程序利用并行执行环境运行原生 Julia 应用程序。随后，我们创建了 Docker 容器来部署 Julia 服务。这些 Docker 容器可以使用 Julia 客户端部署在 Kubernetes 环境中，并使用 Kubernetes API 进行编排。最后，我们讨论了连接到 AWS、Azure 和 GCP 等原生公共云平台的 Julia 客户端。云环境多样且庞大。它们可能极其复杂。虽然我们只是蜻蜓点水，但我们期望读者深入研究他/她关注的特定领域，并最大程度地使用 Julia。至此，第二模块结束，在后续模块中，我们将回顾一些用于数据分析、文本分析和深度学习的库。

# 练习

1.  使用多个工作负载在分布式模式下启动 JuliaHub 教程。估算计算 π 值所需的时间。
2.  在上一章中，我们创建了一个解决点共线性问题的应用程序。现在创建一个可以部署在另一台机器上的 Docker 容器。
3.  使用 Kuber 教程在您选择的 Kubernetes 平台上编排工作负载。
4.  使用 Julia AWS 启动任何 AWS 服务并在您的应用程序中使用它。
5.  Azure 和 Google Cloud 有连接器吗？

---

# 参考文献

[1] Running a JuliaHub job script from your local Julia IDE, **[https://docs.juliahub.com/run_tutorials/basics/](https://docs.juliahub.com/run_tutorials/basics/)**

[2] JuliaHub, **[https://docs.juliahub.com/](https://docs.juliahub.com/)**

[3] PkgServer, **[https://github.com/JuliaPackaging/PkgServer.jl](https://github.com/JuliaPackaging/PkgServer.jl)**

[4] JuliaWebAPI, Julia package for deploying APIs, **[https://github.com/JuliaWeb/JuliaWebAPI.jl](https://github.com/JuliaWeb/JuliaWebAPI.jl)**

[5] The complete code is available at Chapter-14/server/server.jl

[6] The complete code is available at Chapter-14/client/client.jl

[7] Docker Hub, **[https://hub.docker.com/](https://hub.docker.com/)**

[8] `docker network ls` and `docker network inspect` can be utilized to find the container IP address.

[9] SimpleContainerGenerator, create container images for using Julia packages (especially useful in environments without Internet access), **[https://github.com/bcbi/SimpleContainerGenerator.jl](https://github.com/bcbi/SimpleContainerGenerator.jl)**

[10] Software Conformance (Certified Kubernetes), Cloud Native Computing Foundation, **[https://www.cncf.io/certification/software-conformance/](https://www.cncf.io/certification/software-conformance/)**

[11] Kuber, Julia Kubernetes Client, **[https://github.com/JuliaComputing/Kuber.jl](https://github.com/JuliaComputing/Kuber.jl)**

[12] Tanmay Mohapatra, Kubernetes in Julia with Kuber.jl, **[https://juliacomputing.com/blog/2018/12/kuber/](https://juliacomputing.com/blog/2018/12/kuber/)**

[13] Kuber.jl, Julia Kubernetes Client, **[https://github.com/JuliaComputing/Kuber.jl](https://github.com/JuliaComputing/Kuber.jl)**

[14] AWS, Julia interface to AWS, **[https://github.com/JuliaCloud/AWS.jl](https://github.com/JuliaCloud/AWS.jl)**

[15] aws-sdk-js, AWS SDK for JavaScript in the browser and Node.js, **[https://github.com/aws/aws-sdk-js](https://github.com/aws/aws-sdk-js)**

[16] Azure, Julia interface to Azure API, **[https://github.com/JuliaComputing/Azure.jl](https://github.com/JuliaComputing/Azure.jl)**

[17] GoogleCloud, Google Cloud APIs for Julia, **[https://github.com/JuliaCloud/GoogleCloud.jl](https://github.com/JuliaCloud/GoogleCloud.jl)**

# 第 15 章：数据分析与可视化

Julia 是一个为科学计算和从事数据中心应用的人员设计的系统。在本章中，我们将学习如何使用该语言从结构化和非结构化源获取所需的有用数据。它们还需要获取数据并对其进行处理，以便从数据中获得有用的见解。

## 本章我们将涵盖以下主题：

*   设置环境
*   FileIO
*   文本数据
*   分隔文件
*   XML 文件
*   HTML 文件
*   PDF 文件
*   Microsoft Office 文档
*   图像数据
*   表格数据
*   数据可视化

我们将研究访问各种文件类型，访问文本和图像类型的数据。我们将把它们表示在数据框中，用于类似数据库的集体计算。然后我们将回顾一些绘图和可视化技术。所有这些都是不断增长的添加到 Julia 生态系统中的包的一部分。

我们意识到 Julia 是一门强大的编程语言。我们还看到了在解决许多程序员挑战时的优势和集成体验。现在是时候使用 Julia 访问各种数据源并从中收集有用的见解了。此类应用程序由 Julia 社区开发者在其持续开发新包以巩固 Julia 包生态系统的兴趣中得到支持。虽然我们将只是在识别和使用其中一些方面蜻蜓点水，但还有许多有趣的包要么在计划中，要么正在积极开发中。因此建议读者定期查看包以了解新增功能。

## 设置环境

启动 Julia REPL 并执行以下命令：

```julia
julia> cd("<sample_code>\\Chapter-15")
(@v1.5) pkg> activate .
Activating environment at `Chapter-15\Project.toml`
(Chapter-15) pkg> instantiate
```

如果您是第一次运行，可能需要大量时间。最后，您将拥有运行本章中使用的示例代码所需的所有相关包。您可以继续在 REPL 中运行示例，或启动 Jupyter Notebook（推荐）来尝试本章中的示例。

## FileIO：统一的文件接口

Julia 在概念上倾向于使用类似驱动程序的架构来解决一类问题。在第 13 章中，我们看到了 `WebIO` 框架，其中 HTML5 可以利用一组通用的函数 API 在各种前端上渲染。`FileIO` 本质上是一个类似的 API 框架。它使用框架方法 `load` 和 `save` 来加载完整文件的内容或将其保存出去。根据底层文件类型，将调用相关的读取器和写入器，并将文件加载到内存中。该框架目前支持许多文件类型。其中一些包括：PBM、PGM、PPM、NRRD、AVI、JPG、PDF、TIFF，或大量的图像、声音和视频格式。以下代码将在 Jupyter Notebook 中显示一张图像：

```julia
using FileIO
using ImageShow

tiff = joinpath(pathof(FileIO), "..", "..", "test", "files", "magic2.tiff")
image = load(tiff)
```

您不需要对 `ImageMagick` 库有任何复杂的理解。由于 `.tiff` 文件在 `FileIO` 注册表中注册为受支持的文件类型，并由 `ImageMagick` 库处理，一个简单的 `load` 方法就可以调用必要的模块和函数并提供所需的图像。同样，使用文件名调用 `save` 方法可以将文件转换为 `.jpg` 文件。

```julia
save("magic2.jpg", image)
```

## 文本数据

文本数据是迄今为止最简单的数据形式，只有在有一致的表示时才易于访问和操作。普通文本文件并不常见，因为它们没有任何格式或样式信息。文本数据的格式化以及将它们与图像和表格内容交织在一起，使得访问变得繁琐且通常不可访问。文本数据通常可分为两类。结构化文本数据，如分隔文件、Excel 和 XML；或非结构化数据，如 Word 和 PDF 文件。

### 分隔文件

我们已经在第 13 章中讨论了这些特定的文件类型，在那里我们写了一个带有表头的 CSV 文件。随后，我们读取该文件并将数据作为数组提取。

### XML 文件

没有提到 XML 的结构化数据讨论是不完整的。Julia 中同时提供了 **文档对象模型 (DOM)** 树和基于流事件的解析器。您可以依赖的 XML 包有：基于 `libxml2` 的 `LightXML` 和 `EzXML`，或基于 `libexpat` 的 `LibExpat`。`LightXML` 是最简单的 DOM API，它将 XML 读入树并提供遍历它的接口。

```julia
using LightXML

xdoc = parse_file("books.xml")
xroot = root(xdoc)
println("Root Name: ", name(xroot))
```

上述表达式将打印 `Root Name: bookstore`。进一步查询可以从 `xroot` 对象访问完整的 DOM。

```julia
julia> for c in child_nodes(xroot)
           println("Node type:", nodetype(c))
           if is_elementnode(c)
               e = XMLElement(c)
               println("Element Name: ", name(e))
           end
       end
Node type:3
Node type:1
Element Name: book
Node type:3
Node type:1
Element Name: book
Node type:3
```

可以使用 xpath 搜索文档，或使用 `EzXML` API 验证 DTD。

```julia
julia> using EzXML;
julia> doc = readxml("books.xml");
julia> validate(doc);
julia> for author in nodecontent.(findall("//author/text()", doc))
           println(author)
       end
Giada De Laurentiis
J K. Rowling
```

您也可以使用 `LibExpat` 库加载文档并从文档中搜索 xpath。

```julia
julia> using LibExpat
julia> esm = xp_parse(read("books.xml", String));
julia> authors = LibExpat.find(esm, "//author")
2-element Array{ETree,1}:
 <author>Giada De Laurentiis</author>
 <author>J K. Rowling</author>
```

### HTML 文件

虽然 HTML 文档可以像 XML 文档一样解析，但也有可用的 HTML 解析器，它们可以修复格式不良的文档并优雅地处理它们。

`Gumbo.jl` 是一个建立在 Google Gumbo 库之上的 HTML 5 包。我们将从这个基于 DOM 的解析器中看到一些示例用法。一个简单的 HTML 字符串将被读取为完整的 HTML 文档，库将添加所有缺失的标签。API 的简洁性使其成为阅读大型 HTML 文档（如网页扫描期间的文档）的非常容易使用的工具。

```julia
julia> doc = parsehtml("<h1> Hello, world! </h1>")
HTML Document:
<!DOCTYPE >
HTMLElement{:HTML}:<HTML>
<head></head>
<body>
<h1>
Hello, world!
</h1>
</body>
</HTML>
```

由于元素是具有 `parent` 和 `children` 属性的 `HTMLNode` 类型，您将能够使用 `AbstractTrees` 接口遍历它们。

```julia
julia> for elem in PreOrderDFS(doc.root) println(hasmethod(tag, (typeof(elem),)) ? tag(elem) : elem) end
HTML
head
body
h1
Hello, world!
```

元素也可以通过 `getindex` 接口访问。

```julia
julia> doc.root[2][1][1]
HTML Text: ` Hello, world! `
```

这不意味着是 HTML 的 XML 表示。因此，此包不支持 `CDATA`。

### PDF 文件

`PDFIO` 是牢记 PDF 规范而开发的。虽然目前作为读取器 API 开发，但其意图也一直是将其扩展为写入器以写入 PDF 内容。因此，API 中使用的 PDF 对象可以紧密映射到规范。与 `FileIO` 的文件加载机制不同，`PDFIO` 利用对象句柄来存储对象引用，这些引用可以稍后访问以在需要时获取文件信息。对于许多程序员来说，加载 PDF 文件中的所有文本可能就足够了。使用 `PDFIO` 实现此目的的代码块如下：

```julia
julia> using PDFIO
julia> """
```

