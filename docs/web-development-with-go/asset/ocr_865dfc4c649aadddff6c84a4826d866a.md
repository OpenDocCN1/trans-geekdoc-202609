# 14.10. VIEWING ALL OWNED GALLERIES

```
$ atom main.go
```

Add the following route where all the existing gallery routes are.

```
r.Handle("/galleries", requireUserMw.ApplyFn(galleriesC.Index).Methods("GET")
```

Restart your server and head to the localhost:3000/galleries page. While the page won't look very pretty, we can see that our view is indeed receiving a slice of galleries. In the next section we will learn how to iterate over the elements of a slice inside a template, allowing us to render each gallery individually and making our index page more usable.

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/14.10.2

Changes - book.usegolang.com/14.10.2-diff

# 14.10.3 Iterating over slices in Go templates

We now have all the code in place to render our index page, but our template could use some updating. Rather than just dumping that data on the screen, it would be nice if we could instead iterate over each gallery, possibly displaying each as a row in a table.