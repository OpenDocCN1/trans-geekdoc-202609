# 3.7. Example: M3u2pls

| Length33=251 |
| NumberOfEntries=33 |
| Version=2 |

The .pls file format is slightly more elaborate than the .m3u format. The file begins with the literal string [playlist]. Each song is represented by three key-value entries for the filename, title and duration in seconds. The .pls format is a specialized form of .ini file (Windows initialization format) where each key (within a square-bracket-titled section) must be unique—hence the numbering. The file ends with two lines of metadata.

The m3u2pls program (in file m3u2pls/m3u2pls.go) expects to run with an .m3u file specified on the command line and writes an equivalent .pls file to os.Stdout (i.e., to the console). We can easily use redirection to send the .pls data into an actual file. Here is an example of the program usage:

```
./m3u2pls Bowie-Singles.m3u > Bowie-Singles.pls
```

Here we tell the program to read the Bowie-Singles.m3u file and use console redirection to write the .pls format for the Bowie-Singles.pls. (Of course, it would be nice to be able to convert the other way too—and this is precisely what the exercise that follows this section involves)

We review almost the entire program, skipping only the imports.

```
func main() {
	if len(os.Args) == 1 || !strings.HasSuffix(os.Args[1], ".m3u") {
		fmt.Printf("usage: %s <m3u>\n", filepath.Base(os.Args[0]))
		os.Exit(1)
	}
	ifif rawBytes, err := ioutil.ReadFile(os.Args[1]); err != nil {
		log.Fatal(err)
	} else {
		songs := readM3uPlaylist(string(rawBytes))
		writePlsPlaylist(songs)
	}
}
```

The main() function begins by checking to see if the program has been invoked with an .m3u file specified on the command line. The strings.HasSuffix() function takes two strings and returns true if the first string ends with the second string. If no .m3u file has been specified a usage message is output and the program is terminated. The filepath.Base() function returns the basename (i.e., the filename) of the given path and the os.Exit() function cleanly terminates the