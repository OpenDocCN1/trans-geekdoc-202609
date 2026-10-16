The iterative approach has given us fast feedback that our understanding of the requirements is incomplete.

fs.FS gives us a way of opening a file within it by name with its Open method. From there we read the data from the file and, for now, we do not need any sophisticated parsing, just cutting out the Title: text by slicing the string.

# Refactor

Separating the 'opening file code' from the 'parsing file contents code' will make the code simpler to understand and work with.

```
func getPost(fileSystem fs.FS, f fs.DirEntry) (Post, error) {
	postFile, err := fileSystem.Open(f.Name())
	if err != nil {
		return Post{}, err
	}
	defer postFile.Close()
	return newPost(postFile)
}
```

```
func newPost(postFile fs.File) (Post, error) {
	postData, err := io.ReadAll(postFile)
	if err != nil {
		return Post{}, err
	}
	post := Post{Title: string(postData)[:7]}
	return post, nil
}
```

When you refactor out new functions or methods, take care and think about the arguments. You're designing here, and are free to think deeply about what is appropriate because you have passing tests. Think about coupling and cohesion. In this case you should ask yourself: