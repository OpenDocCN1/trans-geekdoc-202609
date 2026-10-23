We can see here that the `CreatedAt` struct field no longer appears in the JSON at all, and the `Year` field (which had the value `0`) doesn't appear either thanks to the `omitempty` directive. The other fields that we used `omitempty` on (`Runtime` and `Genres`) are unaffected.

> **Note:** You can also prevent a struct field from appearing in the JSON output by simply making it unexported. But using the `json:"-"` struct tag is generally a better choice: it's an explicit indication to both Go and any future readers of your code that you don't want the field included in the JSON, and it helps prevents problems if someone changes the field to be exported in the future without realizing the consequences.
> 
> Old versions of `go vet` used to raise an error if you tried to use a struct tag on an unexported field, but this has now been fixed in Go 1.16.

# Additional Information

# The string struct tag directive

A final, less-frequently-used, struct tag directive is `string`. You can use this on individual struct fields to force the data to be represented as a string in the JSON output.