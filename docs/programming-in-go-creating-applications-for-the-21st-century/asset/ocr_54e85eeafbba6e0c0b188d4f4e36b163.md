# 3.7. Example: M3u2pls

This function accepts the contents of an .m3u file as a single string and returns a slice of all the songs it is able to parse from the string. It begins by declaring an empty Song variable called song. Thanks to Go's practice of always initializing things to their zero value, song's initial contents are empty strings and a Song. Seconds value of 0.

At the heart of the function is a for range loop ($5.3, ➤ 203). The strings.Split() function is used to split the single string that holds the entire .m3u file's data into separate lines, and the for loop iterates over each of these lines. If a line is empty or the first line (i.e., starts with the string literal "#EXT3U", the continue statement remains; this simply passes back to the for loop to find the next iteration—or the end of the file if there are no more lines.

If the line begins with the "#EXTINF: string literal, it is passed to a custom parseExtfinLine() function for parsing: This function returns a string and an int which are immediately assigned to the current song's Title and Song.Seconds fields. Otherwise, it is assumed that the line holds the filename (including the path) of the current song.

Rather than using the filename as is, the strings.Map() function is called with a custom mapPlatformDirSeparator() function to convert directory separators into those native for the platform the program is running, and the result is stored as the current song's Song.Filename. The strings.Map() passed a mapping function with signature func(rune) rune and a string. For every character in the string mapping function is called with the character replaced by the character returned by passed-in function—which may be the same as the original one, of course. As usual with Go, a character is a rune whose value is the character's Unicode code point.

If the current song's filename and title are both nonempty, and if the song's duration isn't zero, the current song is appended to the returns value (of type []Song) and the current song is set to its zero value (empty strings and 0) by assigning any song to it.

```
func parseExtfinLine(line string) (title string, seconds int) {	if i := strings.Index(line, "-0123456789"); i > -1 {
	const separator = ","
	line = line[i:]
	if j := strings.Index(line, separator); j > -1 {
		title = line[j:len(separator)]
		var error
		if seconds, err := strconv.Atoi(line[j]); err != nil {
			log.Printf("failed to read the duration for '%s': %v\n", title, err)
			seconds = -1
	}
}
}
```