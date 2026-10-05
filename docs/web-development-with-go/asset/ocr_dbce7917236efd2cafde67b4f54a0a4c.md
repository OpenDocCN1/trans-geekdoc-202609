# 532 CHAPTER 14. CREATING THE GALLERY RESOURCE

We can achieve this with Go’s html/template package by using the range action^7, which at a high level is similar to the range keyword you have seen in Go code, but isn't exactly the same.

An example of iterating over a slice in a Go template is shown below, assuming that the .Slice field storing a slice.

```
{{range .Slice}}
Item: {{.}} <br/>
{{end}}
```

Inside the range block the dot (.) is replaced with an individual element from the slice, and the range block is run once for each item in the slice. That means that our code above might look like it is only writing a single item, it is similar to a for loop and will be run once for each item in the slice.

For example, if we run the code above with the Slice field set to the integer slice:

```
data.Slice = []int{11, 16, 22}
```

The output of your template would be:

```
Item: 11 <br/>nItem: 16 <br/>nItem: 22 <br/>
```

The range keyword allows us to write code representing how a single item in a slice should look, and then it handles running that portion of the template for each item in the slice.

> ^7https://golang.org/pkg/text/template/#hdr-Actions