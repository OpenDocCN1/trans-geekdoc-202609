I alluded to this at the start of the chapter, but it’s possible for an embed path to point to a *specific file*. Embedding isn’t just limited to directories.

For example, let’s pretend that our `ui/static/css` directory contains some additional assets that we don’t want to embed, such as Sass or Less files. In that case, we could embed just the `ui/static/css/main.css` file like so:

```
//go:embed "static/css/main.css" "static/img" "static/js"
var Files embed.FS
```

# Wildcard paths

The character * can be used as a ‘wildcard’ in an embed path. Continuing with the example above, we could rewrite the embed directive so that only .css files under `ui/static/css` are embedded:

```
//go:embed "static/css/*.css" "static/img" "static/js"
var Files embed.FS
```

Related to that, if you use the wildcard path "*" without any qualifiers, like this:

```
//go:embed "*"
var Files embed.FS
```

... then it will embed everything in the current directory, including the .go file that contains the embed directive itself! Most of the time you don’t want that, so it’s more common to explicitly embed specific subdirectories or files instead.

# The all prefix

Finally, if a path is to a directory, then all files in that directory are recursively embedded — except for files with names that begin with . or _ characters. If you want to include those files too, then you should use the `all:` prefix at the start of the path.

```
//go:embed "all:static"
var Files embed.FS
```