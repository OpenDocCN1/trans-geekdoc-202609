# 4.4. Examples

| ability, about, absence, absolute, absolutely, abuse, accessible, ... |
| accept, acquired, after, against, applies, arrange, assumptions, ... |

128 you
151 or
192 to
221 of
345 the

Even for a small file the number of words and the number of different frequencies can be quite large, so here we have elided most of the output.

Producing the first part of the output is straightforward. We can use a map of type map[string] with word keys and frequency values. But to get the second part of the output we will need to invert the map—and this isn't quite easy because it is likely that more than one word will have the same frequency. The solution is to invert a multivalued map of type map[int][]string, that is, a map whose keys are frequencies and whose values are all the words that have the corresponding frequency.

We will begin with the program's main() function and work top-down, as usual, we will omit the imports.

```
func main() {
	if len(os.Args) == 1 || os.Args[1] == "-h" || os.Args[1] == "--help" {
	fmt.Printf("usage: %<file1> %<file2> [...<fileN>]\n",
	filepath.Base(os.Args[0]))
	os.Exit(1)
	}

requencyForWord := map[string]int // Same as: make(map[string]int)
	for _, filename := range commandLineFiles(os.Args[1:]) {
	updateFrequencyForWord(filename, frequencyForWord)
	}
	reportByWords(frequencyForWord)
	wordsFrequency := invertStringMap(frequencyForWord)
	reportByFrequency(wordsFrequency)
}
```

The main() function starts dealing with the command line and then gets down to work.

We begin by creating the simple map that will keep track of the frequency of each unique word in the files read in. We have used the composite literal syntax to create the empty map, just to show how it does. Once the map iterate over each filename given the command line and for each attempt to update the frequencyForWord map.