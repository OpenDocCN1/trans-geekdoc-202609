At this point you’ll see that a `go.mod` file has been created in the root of your project directory. If you open it up, it should look similar to this:

```
File: go.mod

module greenlight.alexedwards.net

go 1.16
```

We talked about modules in detail as part of the first *Let’s Go* book, but as a quick refresher let’s recap the main points here.

+   - When there is a valid `go.mod` file in the root of your project directory, your project *is a module*.
+   - When you’re working inside your project directory and download a dependency with `go get`, then the exact version of the dependency will be recorded in the `go.mod` file. Because the exact version is known, this makes it much easier to ensure reproducible builds across different machines and environments.
+   - When you run or build the code in your project, Go will use the exact dependencies listed in the `go.mod` file. If the necessary dependencies aren’t already on your local machine, then Go will automatically download them for you — along with any recursive dependencies too.
+   - The `go.mod` file also defines the *module path* (which is `greenlight.alexedwards.net` in my case). This is essentially the