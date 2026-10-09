# ## Chapter 8.5: Multi-line Delimited Split

A multi-line delimited split is useful for extracting lines of text that are separated by a pattern, such as sections in a configuration. It can be used to enable inventory, auditing, or managing configurations. The multi-line m flag causes the ^ and $ regexp syntax to additionally match the beginning and end of each line.

This example splits the defined configuration into a two-dimensional slice, where each of the configuration sections that are delimited by the ! character is represented by its own slice. Each line of configuration is then represented as a string within the respective configuration section slice.

To begin, the configuration is defined and then the pattern is used as a parameter in the regexp.MustCompile() function to return a regexp.Regexp object. Next, the regexp.Regex.Split() method is called on the object using the configuration and -1 to process unlimited matches. This method splits the configuration into a single slice, where each value is what remains between the pattern matches.

After initializing the two-dimensional slice, the values that are returned from splitting the configuration are iterated over. Finally, within the loop, the trailing new-line character is trimmed with the strings.TrimSuffix() function and then each string is split by their new-line character, returning and then appending a new slice with values returned from splitting each line.

```
```
package main

import (
	"fmt"
	"regexp"
	"strings"
)
```
```