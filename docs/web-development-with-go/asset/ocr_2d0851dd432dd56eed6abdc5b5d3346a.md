# 6.5. CLEANING UP OUR CODE

**Listing 6.28:** Writing the layoutFiles() function.
```go
func layoutFiles() []string {
    files, err := filepath.Glob(LayoutDir + "*" + TemplateExt)
    if err != nil {
        panic(err)
    }
    return files
}
```

Let's take a moment to review what is happening in Listing 6.28.

First we declare our function - layoutFiles - and state that it will return a string slice. Inside our function we call the Glob function provided by the path/filepath package and pass in a string that we create by combining a few variables and a hard-coded asterisk string.

Assuming we don't change our variables, the glob pattern we are using will evaluate to:

```
"views/layouts/*.gohtml"
```

This will match all files ending in .gohtml in the layouts directory, which is what we wanted.

If some reason our call to Glob fails, we will panic with whatever error we received. Otherwise we return all of the file paths we receive from our call to Glob.

**Box 6.6. Why so many panics?**

At this point I want to address the question, “Why are we panicking so much in view.go?” Aren’t panics be bad?