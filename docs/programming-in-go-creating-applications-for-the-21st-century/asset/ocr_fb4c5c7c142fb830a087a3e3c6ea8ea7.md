are visible to the caller. The new Entry is added has the given key and value, and its own entry Children. This is the function's recursive outcase.

If the level is greater than 0 we have an indented entry that must be added as a child of the first preceding entry that has one less level of indentation. The code to do this is a single recursive call to the addEntry() function and the last argument is probably the most complicated expression we have seen so far.

The subexpression entries.len() — 1 produces an int that is the index position of the last item in the Entries value that +entries points to. (The Entries.len() method takes an Entries value rather than *Entries, but Go is smart enough to automatically differentiate the entries pointer and call the method on the pointed-Entries value.) The complete expression (from the outer &( ...) part adds the Entry in the Entries' children field (which itself is of type Entries). So, if we consider the expression as a whole we are taking the address of the last entry in the Entries children field—this is of type Entries which is exactly what was needed for the recursive call.

To help clarify what is happening, here is some less compact code that does exactly the same thing as the addEntry() function's recursive call to itself in the else block.

```
theEntries := *entries
lastEntry := &entries[theEntries.Len-1]
addEntry(level-1, key, value, &lastEntry.children)
```

First, we create the Entries value to hold the value pointed to by the *entries pointer—this is cheap since no actual copying is done; in effect, the Entries is set as an alias to the pointed-to Entries value. Next we take the address of (i.e., a pointer to) the last entry. If we didn't take the address we would get a new entry that is a copy of the last entry—and a copy is no use here. Finally, we do the recursive addEntry() call, passing the address of the last entry's children field.

```
func sortedEntries(entries Entries) []string {
  var sortedSlice []string
  sort.Sort(entries)
  for _, entry := range entries {
    populateIndentedStrings(entry, &sortedSlice)
  }
  return sortedSlice
}
```

When this sortedEntries() function is called, the structure of the Entries reflects that of the “Original” strings that the program outputs, with indented strings being children of their parent (as children of type Entries fields), and so on (245◄)