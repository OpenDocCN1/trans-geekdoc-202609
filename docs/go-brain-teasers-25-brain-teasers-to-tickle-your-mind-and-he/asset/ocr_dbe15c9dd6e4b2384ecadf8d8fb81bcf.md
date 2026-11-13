This code will print: false

You might expect this code to fail since there’s no time type in the JSON format, or you might expect the comparison to succeed.

Go’s encoding/json lets you define custom JSON serialization for types that are not supported by JSON. You do that by implementing json.Marshaler and json.Unmarshaler interfaces. Go’s time.Time implements these interfaces by marshaling itself to an RFC 3339 formatted string and back.

JSON has a very limited set of types. For example it only has floating-point numbers. Which can lead to surprising results if you use the empty interface when unmarshaling.

Listing 14. json_float.go

```
package main

import (
	"encoding/json"
	"fmt"
	"log"
)

func main() {
	n1 := 1
	data, err := json.Marshal(n1)
	if err != nil {
		log.Fatal(err)
	}

	var n2 interface{}
	if err := json.Unmarshal(data, &n2); err != nil {
```