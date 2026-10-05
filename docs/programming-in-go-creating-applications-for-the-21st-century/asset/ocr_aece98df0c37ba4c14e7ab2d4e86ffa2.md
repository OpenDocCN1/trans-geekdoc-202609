# 2.4. Example: Statistics

```
func processRequest(*http.Request) ([]float64, string, bool) {
	var numbers []float64
	if slice, found := request.Form("numbers"); found && len(slice) > 0 {
		text := strings.Replace(slice[0], "", "", -1)
		for field := range strings.Fields(text) {
			if x, err := strconv.ParseFloat(field, 64); err != nil {
				return numbers, "" + field + " is invalid", false
			} else {
				numbers = append(numbers, x)
		}
		}
	if len(numbers) == 0 {
		return numbers, "", false // no data first time form is shown
}
	return numbers, "", true
}
```

This function reads the data from the request value. If the form is shown for the first time the "numbers" text <input> element is empty. This isn't an error we return an empty slice of float64s, an error message, and false to indicate that there are no statistics to gather—in the empty form being shown. If the user has entered some numbers we return a slice of float64s, an error message, and true; if one or more numbers are invalid, a possibly empty, an error message, and false.

The request value has a Form field of type map[string][]string($4.3 ► 164). This means that the map's keys are strings and its values are slices of strings. Any one key may have any number of strings as its value. For example, if the user has entered the numbers "5 8.2 13 6", the map will have a "numbers" key with a value of []string{"5 8.2 13 6" that is, its value is a slice of strings (For comparison, this is an example of a slice of strings: []123", "ab c") We check if the "numbers" key is present (it out to), and if it is—its value has at least one string—we know that we have numbers to read.

We use the strings.Replace() function to obtain the string of numbers that the user entered but with commas replaced by spaces. The third argument is the number of replacements to perform;-1 means as many as possible). Having the string of whitespace-separated numbers we use the strings.Fields() function to split the string (on any amount of whitespace) to a slice of strings which we iterate over straight away using for range loop. (The strings package's functions are covered in $3.6, ► 106; for the range loop is covered in $5.3, ► 203.) For each string ("5", "8", etc.) we attempt to convert to a float64 using the strconv.ParseFloat() function which takes a string to parse and a bit size of 32 or 64 ($3.6, ► 14). If the conversion fails imme-