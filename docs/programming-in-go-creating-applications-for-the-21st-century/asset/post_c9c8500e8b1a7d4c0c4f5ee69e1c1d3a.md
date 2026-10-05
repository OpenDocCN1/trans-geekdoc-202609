
Once the first map is complete we output the first report: an alphabetical list of all the unique words encountered and their corresponding frequencies. Then we create an inverted version of the map and output the second report: a numerically ordered list of frequencies and their associated words.

```go
func commandLineFiles(files []string) []string {
	if runtime.GOOS == "windows" {
		args := make([]string, 0, len(files))
		for _, name := range files {
			if matches, err := filepath.Glob(name); err != nil {
				args = append(args, name) // Invalid pattern
			} else matches != nil { // At least one match
				args = append(args, matches...)
			}
		}
		return args
	}
}
```

The commandLineFiles() function simply returns the []string it is given on Unix platforms such as Linux and Mac OS X, since on these platforms the shell automatically does file globbing (i.e., replaces *.txt with any matching text files, e.g., README.txt, INSTALL.txt, etc.). Windows shell (cmd.exe) does not do globbing, so if the user enters, *.txt on the command line, what will the program return? To provide reasonable cross-platform uniformity, we do the globbing whenever we are on Windows. Another way to handle cross-platform differences is to have platform-specific .go files—this is covered in a later chapter, 9.1.1.1, ➤ 410.)

```go
func updateFrequencies(filename string, frequencyForWord map[string]int) {
	var file *os.File
	var err error
	if file, err = os.Open(filename); err != nil {
		log.Println("failed to open the file: %v", err)
		return
	}
	defer file.Close()
	readAndUpdateFrequencies(bufio.NewReader(file), frequencyForWord)
}
```

This function is used purely for the file handling. It opens the closing of the file when the function returns, and passes on the actual work to the readAndUpdateFrequencies() function. By passing the file reader as a *bufio.Reader (produced by the bufio.NewReader() call), we ensure that the called function can read the file as strings line by line rather than having to read raw bytes.

## 4.4. Examples

```go
func readAndUpdateFrequencies(reader *bufio.Reader,
    frequencyForWord map[string]int) {
    for {
		line, err := reader.ReadString('\n')
		for _, word := range SplitOnNonLetters(strings.TrimSpace(line)) {
			if len(word) > utf8.UTFMax ||
				utf8.RuneCountIn(word) > 1 {
				frequencyForWord[strings.ToLower(word)] += 1
			}
		}
		if err != nil {
			if err != io.EOF {
				log.Println("failed to finish reading the file: ", err)
			}
			break
		}
	}
}
```

The first part of this function should be very familiar by now. We create an infinite loop and read the file by line, breaking out of the loop when we reach the end of the file or if an error occurs (in which case we report the error to the user). We do not terminate the program when we hit an error because there might be many files to read and for which we prefer to do as much work as possible and report any problems that were encountered rather than stopping at the first error.

The inner loop is where the interesting processing is done. Any given line might have punctuation, numbers, symbols, and other nonword characters, so we iterate by word by having splitting the line into words and discarding any non-word characters using a custom SplitOnNonLetters() function. And the string we fetch that function in the first place has trimmed off both ends.

We only want to include words that contain at least two letters. The easiest way to do this is to use a one-clause statement, that is, if utf8.RuneCountIn(word) > 1, which works fine.

The simple test just described is potentially bit expensive because it will parse the entire word. So in the program we use a two-clause statement if the first clause takes a much cheaper approach. The first clause checks to see if the number of bytes in the word is greater than utf8.UTFMax (which is a constant of value 4, the maximum number of bytes required to represent a single UTF-8 character). This is a really fast test because Go strings know how many bytes they contain and Go’s binary Boolean operators (&& and ||) short-circuiting (2.2, 56). Of course, others consist of four or fewer bytes (e.g., for 7-bit ASCII characters or a couple of 2-byte UTF-8 characters) will fail this first check, but that isn’t a problem because the second check (the rune) will be fast because it will always have four or fewer characters to count.

Is it worth using the two-clause in this situation? It really depends on the input—the more words that need processing and the longer they are, more potential for savings. The only way to know for certain is to benchmark using real or at typical data.

```go
func SplitOnNonLetters(s string) string {
	notLetter := func(char rune) bool { return unicode.IsLetter(char) }
	return strings.FieldsFunc(s, notLetter)
}
```

This function is used to split a string on nonletters. First we create an anonymous function that returns true for letters and false for nonletters. We then use strings.FieldsFunc() with this function.

```go
func reportByWords(frequencyForWord map[string]int) {
	words := make([]string, 0, len(frequencyForWord))
	wordWidth, frequencyWidth := 0, 0
	for word, frequency := range frequencyForWord {
		words = append(words, word)
		if width := utf8.RuneCountIn(word); width > wordWidth {
			wordWidth = width
		}
		if width := len(fmt.Sprint(frequency)); width > frequencyWidth {
			frequencyWidth = width
		}
	}
	sort.Strings(words)
	fmt.Printf("%s   %s\n", "Word", "Frequency")
	for _, word := range words {
		fmt.Printf("%-*s%d\n", wordWidth, word, frequencyForWord[word])
	}
}
```

The reportWords() function is called to output its data. We want the output to be in alphabetical (eventually, Unicode code point) order, so we begin by creating an empty []string to hold the words. We also want to know the width in characters of the longest word and of the highest frequency (i.e., how many digits it has) so that we can produce our output in neat columns.

Once the slice has been populated we set it. We don't have to worry about case-sensitivity because all the words are lowercase (this was done in the readUpdateFrequencies() function).
