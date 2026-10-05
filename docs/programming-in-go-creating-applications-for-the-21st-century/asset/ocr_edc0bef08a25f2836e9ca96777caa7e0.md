# Chapter 4. Collection Types

completes without setting same to false, and the count is greater than zero, we have found what we want and immediately return it. If no separator matches we return an empty string—this is our convention to make the fields are whitespace-separated, or not separated at all

```
func report(separator string) {
    switch separator {
    case "":
        fmt.Println("whitespace-separated or not separated at all")
    case "\t":
        fmt.Println("tab-separated")
    default:
        fmt.Printf("%s-separated\n", separator)
    }
}
```

The report() function is trivial, writing a simple description of the separator used by the file that was read.

This example has shown both one- and two-dimensional slices (separators, lines, and counts) in typical use. In the next example we we will look at maps, slices, and sorting.

# 4.4.2. Example: Word Frequencies

Textual analysis has a variety of uses, from data mining to the study of language itself. In this subsection we will review an example that performs one of the most basic forms of textual analysis: It counts the frequencies of words in the file it is given.

Frequency data can be presented in two different but equally sensible ways—as an alphabetical list of words with their frequencies, and as an ordered list of frequency values and the words that have the corresponding frequencies. The wordfrequency program (in file wordfrequency/wordfrequency.go) produces both kinds of output, as illustrated below.

```
$ ./wordfrequency small-file.txt
Word Frequency
ability 1
about 1
above 3
...
years 1
you 128
Frequency → Words
```