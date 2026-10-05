
## 6.4. ADDING A NAVIGATION BAR

Now we are ready to use our navbar template. Open the bootstrap layout and add the code from Listing 6.25 just after the body HTML tag.

```
$ atom views/layouts/bootstrap.gohtml
```

Listing 6.25: Using the navbar template.

```
<body>
  {{template "navbar"}}
  <div class="container-fluid">
    {{template "yield"}}
  </div>
  <!-- ... this is all the same -->
</body>
```

Now stop your server and restart it.

```
$ go run main.go
```

Bam! We have a navbar on all of our pages and it hardly took us any time at all. Neat right?

Before moving on, take a moment to test out all of your links and make sure they work. If you have been doing exercises it might also be a good idea to add links to any custom pages you created, such as the FAQ page.

You can also check out a screenshot of the site with a navbar in Figure 6.3

## CHAPTER 6. CREATING OUR FIRST VIEWS

![](img/d6be51afcf11b16bf97245d05fb9e635_109_0.png)

Figure 6.3: A layout with a navbar

## Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/6.4

Changes - book.usegolang.com/6.4-diff

## 6.5 Cleaning up our code

Now that we have a working Bootstrap layout and with a helpful navbar it is time to take a break from adding new features and to instead spend some time cleaning up our code a bit.

Open views/view.go and check out the append statement. While this is only three lines now, it has grown every single time we added a new template to our application. Over time this is going to get fairly large, and as we remove templates we will need to remove them from this list as well.

Rather than spending our time maintaining this list of templates, we are instead going to dedicate some time to write a function that will simply include all gohtml files in the layouts directory in all of our views. We may not need them all, but this will drastically simplify the task of managing layout templates in our views and will likely prevent a few, “Why isn't my code working-??!” bugs.

To make this change we are going to first discuss Globbing, covering what it is and what we will be using it for.

After that we will explore how to glob files in Go and write some code to glob all of our layout templates.

Then we are going to focus on cleaning up our template execution code. Right now our handlers need to work directly with templates and layouts, but when we are done our handlers won't need to worry themselves with how our views are rendered, they will simply need to call a single render method.

Finally we are going to take a moment to reorganize our templates, moving the footer template call out of the home and contact templates and inserting it into the bootstrap layout.

### 6.5.1 What is globbing?

Globbing is a way of telling a computer which files you want and which files you want to ignore. If you are familiar with the command line, `mv` is a command that lets you move a file from one location to another. For example, you could say `mv x.txt old/x.txt` and it would move the file `x.txt` in your current directory to the `old` directory.

If you wanted to move all `.txt` files to the `old` directory it would be really slow to do this one by one, but with a glob pattern you could instead type `mv *.txt old/` and it would find every file with the `.txt` extension to the `old` folder.

Note: We don't need to specify the files name in the second part of this statement but is instead the way we determine which files get moved because the original name will be used.

Globbing isn't the act of moving the files, but it is the way we determine which files get moved. It is the `*.txt` part of `mv *.txt old/`. It is a simple way of saying “give me all of the files that end in `.txt`

You don't need to be a master with globbing to take advantage of it. For now there are only three big takeaways you need to know:

- 1. The asterisk (*) is used to match against any number of characters, even none, no matter what character they are.
- 2. Most other characters (like each character in .txt) will look for an exact match.
- 3. Globbing requires a complete match. For example, *.txt would not match the file `test.txt` because nothing matches the final “e” in the file. If we added a second asterisk (*) at the end of our pattern would work, but without it we don't have a match.

## 6.5. CLEANING UP OUR CODE

> ### Box 6.5. Glob is not the same as a regular expression.

If you don't have any programming experience and don't know what a regular expressions is you are unlikely to make this mistake, but for those of you who do - Glob is not the same as a regular expression, so don't expect it to work the same!

If you would like to read more about this, you can check out this stack overflow article that discusses the differences between glob-style patterns and regular expressions.

## 6.5.2 Using filepath.Glob

Go's standard library includes the path/filepath package, which is incredibly useful for manipulating and dealing with files without having to write operating-system specific code.

In this library there is a function named Glob, which implements the globbing functionality we talked about in the last section. It doesn't do anything to move files or anything like that, but given a glob pattern it will return a slice of files (in the form of a string slice) that match the glob pattern.

This is incredibly useful when we want to include all of the files in a particular directory that match a specific pattern. Instead of needing to list every single .gohtml file in our layouts directory, we can instead say "grab every .gohtml file in that directory" and be on our merry way.

We are going to use Glob to simplify our NewView function, so we will start by opening the source file.

- 5https://golang.org/pkg/path/filepath/
- 6https://golang.org/pkg/path/filepath#Glob

```
$ atom views/view.go
```

Once you have it open, the first thing we want to do is to add the **path/filepath package to our imports. This is shown in Listing 6.26.

### Listing 6.26: Importing path/filepath

```go
import (
  "html/template"
  "path/filepath"
)
```

Next we are going to create a few global variables that will help us when constructing our glob pattern. This is shown in Listing 6.27.

### Listing 6.27: Adding glob helper variables

```go
var (
  LayoutDir string = "views/layouts/"
  TemplateExt string = ".gohtml"
)
```

LayoutDir will help us by specifying the layout directory, and TemplateExt will tell us what extension we expect all template files to match.

*Note: Technically these could be constants, but we will leave them as variables for now in case we want to test this code with different values in the future.*

Next we need to write some code that uses both of these variables, along with the **Glob** function, and returns a slice of templates to include in our view. We are going to call this function **layoutFiles**, and it is shown in Listing 6.28.

## 6.5. CLEANING UP OUR CODE

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
