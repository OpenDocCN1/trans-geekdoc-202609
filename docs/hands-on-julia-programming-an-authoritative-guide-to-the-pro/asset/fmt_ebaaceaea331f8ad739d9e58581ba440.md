
Two points are said to be coincident when the distance between them is less than a certain small value called the `point coincident tolerance`.[^6] Given the above condition, how do we know 3 such points are collinear or form a straight line?

![Figure 13.3](n4upl4fndrr.jpeg)

**Figure 13.3:** (a) Points AB are the same point if –ε < δ < ε. (b) 3 points ABC are collinear if either AB, BC, or AC are too close to each other. (c) But (b) is not sufficient as shown in B can be very close to the line AC.

It is clear from the figure that for ABC to be collinear the triangle area must be very small:

![Triangle area formula](n4upl4fndrs.jpeg)

where δ is the height and L is the length of the longest side (BC in our example). If

![Collinearity condition](n4upl4fndrt.jpeg)

where ϵ is the point coincidence tolerance we know the points are collinear. The triangle area (can be computed using the determinant[^7]):

![Determinant formula](n4upl4fndru.jpeg)

---

We will call the package `PointLib` and initialize it using the following steps:

1.  Change the directory to your work area where you want to create the `PointLib` package.
2.  Type the character `]` on the Julia REPL prompt `julia>`. The prompt shall change to `(@1.6) pkg>`. This prompt is called the package mode.
3.  Use the command: `generate PointLib`.
4.  A new directory shall be created by the name PointLib with the following files:

    ```
    shell> tree /F[^8]
    Folder PATH listing
    Volume serial number is E285-F8B9
    C:.
    │   Project.toml
    └───src
            PointLib.jl
    ```

5.  The `Project.toml` will have the following metadata:

    ```
    shell> more Project.toml
    name = "PointLib"
    uuid = "7de1f589-fb91-4994-b265-ccfc43c44ada"
    authors = ["Sambit Kumar Dash <sambitdash@gmail.com>"]
    version = "0.1.0"
    ```

6.  `src/PointLib.jl` is the entry point of the code for the package and will contain the following code. A default module matching the name of the package. A greet function as a sample code.

    ```julia
    module PointLib
    greet() = print("Hello World!")
    end # module
    ```

7.  Use `cd("PointLib")` and get inside the folder and use the command `]activate .`. The dot (`.`) following activate ensures the environment is activated in the current directory. That will change the prompt to `(PointLib) pkg>` confirming the environment defined in the `PointLib/Project.toml` is being used.

8.  Add the `LinearAlgebra` library to the `PointLib` package. This can take some time depending on the registry update.

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

    The `Project.toml` will have a dependency entry. And a new file `Manifest.toml` is created, that resolves the complete list of packages needed. For example, `LinearAlgebra` requires `Libdl` and that information is updated in the `Manifest.toml`.

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

Thus we have a package to develop the functionalities we wanted and we can also add it to source control for better maintenance and sharing of our code. Git managed packages can be delivered through Julia package management.

---

The following code should suffice for the code we will like to develop. While this is a starter code, we will leave it as an exercise for the readers to enhance the functionality with more use cases to add.

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

Updated modules do not get updated once they are loaded. You will need to close the Julia session or use a package like `Revise.jl`[^9] to be able to reload the new symbols inside a package.

---

Once the program is developed, it is ideal to check-in to a project in a source control. We will suggest a git-based online repository like GitHub be used for this purpose. Please follow the following steps for the same:

1.  Login to GitHub at <https://www.github.com>
2.  Create a new repository with the name `PointLib.jl`. It’s customary to name Julia packages with an extension of `.jl`.
3.  You can use the GitHub Desktop to add your folder `PointLib` to the repository
    or
    follow the `git` commands below in the folder `PointLib`:

    ```bash
    echo "# PointLib.jl" >> README.md
    git init
    git add .[^10]
    git commit -m "first commit"
    # U is the GitHub username
    git remote add origin https://github.com/U/PointLib.jl.git
    git push -u origin master
    ```
