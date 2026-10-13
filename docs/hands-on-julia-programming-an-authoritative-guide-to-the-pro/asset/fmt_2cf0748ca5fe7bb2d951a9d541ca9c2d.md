
# References

[21] Tim Holy, Kristoffer Carlsson, Sebastian Pfitzner, Keno Fischer, *A Julia interpreter and debugger*, 19th March 2019, The JuliaLang Blogs, [https://julialang.org/blog/2019/03/debuggers/](https://julialang.org/blog/2019/03/debuggers/) last accessed: 30th Jan 2021

[22] `Revise.jl`, Automatically update function definitions in a running Julia session, [https://github.com/timholy/Revise.jl](https://github.com/timholy/Revise.jl)

# Debugging

An anecdote suggests Grace Hopper's team members discovered and removed a physical bug in a computer circuitry and were able to fix a non-functioning program. The science of finding fault in a computer program and fixing it is thus called **debugging**. Debugging can be a frustrating and challenging process particularly when the code is not written by the developer trying to fix it. At the same time, it is the most rewarding experience for new programmers to learn from other people's code and also understand varieties of styles of programs out there in the wild. A programmer spends about 35–50% of productive time and 50–75% of the cost in software debugging. While tools have reduced the time spent in debugging individual tasks, the overall time spent on such activities remains the same. While the study has emphasized on enhancing learning behavior, it has also been seen debugging requires effective knowledge of the tools.

## Editor Integrations

The Julia plug-in for **vim**, called **julia-vim**, is a *GitHub* project that can be installed in a **vim** set up for Mac OS X, UNIX, and Windows operating systems. The plug-in is a set of vim scripts that provide the following functionalities:

However adept a programmer is, she would like to try the idea in her mind, quickly experience the outcome, fix the changes, and move on with the next chunk of code. Julia's runtime is pre-loaded. As you load more data structures or modules and packages to the system, the older symbols and code blocks get loaded to the runtime. It may not be possible to modify the symbols already defined without affecting the overall working of the runtime elsewhere. For example, changing a function definition in the REPL is straightforward. But, adding or removing an attribute of a `struct` data type is not permitted. When a package is modified, it is not loaded on the subsequent usage of the command using `<<module>>`. To overcome these limitations, `Revise.jl` package may be used. This package can be autoloaded and can update symbols as part of code-run-fix cycles of development. We suggest the readers review the package documentation for a detailed understanding.

While the preceding ones are some of the easier ways to test and use small chunks of code, they are unlike the line debugging used with tools like **gdb** for native binaries. Julia has a fully functional debugger for the command line.

Julia is a relatively newer platform. The ecosystem for all the preceding components existed before Julia became popular as a language. Developers will like to see Julia seamlessly be used along with the tools they are most comfortable with. In the world of text editors in the UNIX environments, there is almost cult following for **vi** vs. **emacs**. JuliaEditorSupport organization under *GitHub* maintains integration with several of the well-known editors at differing levels of capabilities; some such editors being *Vim*, *Emacs*, *Sublime*, *Atom*, *Notepad++*, and *Eclipse*. Some of the integrations are active while many are deprecated due to lack of focus and usage. Julia IDEs are being developed for *Atom* under a project *Juno* and Microsoft **Visual Studio Code** (**VS Code**).

Julia client for Atom is entering maintenance mode, [https://atom.io/packages/julia-client](https://atom.io/packages/julia-client) last accessed: 27th Jan 2021

Visual Studio Code, [https://code.visualstudio.com/](https://code.visualstudio.com/)

Anecdotes, Grace Hopper, Wikipedia, [https://en.wikipedia.org/wiki/Grace_Hopper](https://en.wikipedia.org/wiki/Grace_Hopper)

`Julia-NotepadPlusPlus`, Git Hub Repository, [https://github.com/JuliaEditorSupport/julia-NotepadPlusPlus](https://github.com/JuliaEditorSupport/julia-NotepadPlusPlus)

`julia-intellij`, GitHub Project, [https://github.com/JuliaEditorSupport/julia-intellij](https://github.com/JuliaEditorSupport/julia-intellij)

juliaDT, GitHub Project, [https://github.com/JuliaEditorSupport/JuliaDT](https://github.com/JuliaEditorSupport/JuliaDT)

Julia PRO, [https://juliacomputing.com/products/juliapro/](https://juliacomputing.com/products/juliapro/)

Installation Guideline `julia-vim`, [https://github.com/JuliaEditorSupport/julia-vim/blob/master/INSTALL.md](https://github.com/JuliaEditorSupport/julia-vim/blob/master/INSTALL.md)

Julia-vim tutorial for newbies, Julia Discourse Post, [https://discourse.julialang.org/t/julia-vim-tutorial-for-newbies/36636/6](https://discourse.julialang.org/t/julia-vim-tutorial-for-newbies/36636/6)

Some attempts have been made to run `Notepad++` in Linux using Wine emulator. Editors like `Sublime Text` have Julia integrations as well.

Devon H. O'Dell, *The Debugging Mindset*, acmqueue, Jan-Feb 2017

Tim Holy, Kristoffer Carlsson, Sebastian Pfitzner, Keno Fischer, *A Julia interpreter and debugger*, 19th March 2019, The JuliaLang Blogs, [https://julialang.org/blog/2019/03/debuggers/](https://julialang.org/blog/2019/03/debuggers/) last accessed: 30th Jan 2021

`Revise.jl`, Automatically update function definitions in a running Julia session, [https://github.com/timholy/Revise.jl](https://github.com/timholy/Revise.jl)
