# 410

# Chapter 9. Packages

by creating the file `aGoPath/src/my_package/my_package.go`. See the source code’s
image package for an example of this.

Go packages are imported from under GOROOT (specifically, $GOROOT/pkg/${GOOS}_
${GOARCH}, e.g., /opt/go/pkg/linux_amd64), and from under the directory or-
ries the GOPATH environment. This means that name conflicts are
sible. The easiest way to avoid name conflicts is to ensure that GOPATH paths have
a unique directory, such as a domain name as we used for the omap package.

The go program works seamlessly with packages from the standard library and
from GOPATH paths, as well as understanding the platform-specific source files
discussed in the following subsection.

# ### 9.1.1. Platform-Specific Code

In situations we need to have code that differs between platforms. For
example, on Unix-like systems the shell does wildcard expansion (expanded glob-
bing), by * on the command line might be received by the program as, say,
"README.txt","INSTALL.txt" in the os.Args[1:] slice. But on Windows the pro-
gram would just get *. We can get the program to do such globbing using
filepath.Glob(), of course, we only do this on Windows.

One solution is to decide whether to use filepath.Glob() at runtime by using
the test if runtime.GOOS == "windows" { }, and this is what most of the book’s
examples (e.g., cgrep1/cgrep.go). Another solution is to use platform-specific
code into its .go file or files. For example, the cgrep3 program consists of
three files, cgrep.go, util_linux.go, and util_windows.go. Inside util_linux.go
there is a single function defined.

```
func commandLineFiles(files []string)string { return files }
```

Clearly, this function doesn't do any globbing since there is no need to on
Linux. The util_windows.go file defines a different function that has the same
name.

```
func commandLineFiles(files []string)string {
  args := make([]string, 0, len(files))
  for _, name := range files {
    if matches, err := filepath.Glob(name); err != nil {
      args = append(args, name) // Invalid pattern
    } else if matches != nil { // At least one match
      args = append(args, matches...)
    }
  }
  return args
}
```