# 4.4. Examples

tually, Unicode code point) order, so we begin by creating an empty []string to hold the words that is enough to hold all the words in the map. We also want to know the width in characters of the longest word and of the highest frequency (i.e., how many digits it has) so that we can produce our output in neat columns: TheWidth and frequencywidth variables are used to record these widths.

The first loop iterates over the items in the map. Each word is appended to the words []string, a very cheap operation because words's capacity is large enough so that the append() function is do to put the given word at the len(words) index position and increment the words's slice by one.

For each word we count the number of characters it contains and set wordwidth to this amount if it is larger than the existing value. Similarly, we count the number of characters needed to represent the frequency—we can use len() for this count bytes since the fmt.Sprint() takes a number and returns a string with decimal digits of all are 7-bit ASCII characters. At the end of the first loop we have the widths of the two columns we want to output.

Once the slice has populated we set it. We don't have to worry about case-sensitivity because all the words are lowercase (this was done in the readUpdateFrequencies() function; 177).

And finally, we print the words and their frequencies in two columns with appropriate widths in ascending alphabetical word order.

```
func invertStringIntMap(intForString string) map[int][]string {
	stringsFor := make(map[int][]string, len(intForString))
	key, value := range intForString {
		stringsFor[value] = append(stringsFor[value], key)
	}
	return stringsFor
}
```

The function begins by creating an empty map. Although we don't know how many items there will be, we have assumed that there will be about the same number as in the original map—after all, there can't be more. The processing is straightforward: We simply iterate over the original map and use each value as a key in the inverted map, and add each key to the inverted map's