stop the execution if x is an even number by skipping the if branch. If the number is odd, x is modified and the continue statement jumps to the next iteration skipping the final break that will be reached in the next iteration. Consider that this is an artefact to demonstrate different flavours of a for construction and may not have a practical sense.

Finally, in line 33 there is an infinite for. These loops are used to declare processes or operations that must be active for an undefined period (e.g. servers waiting for connections). The final break was added to avoid confusion during testing executions.

> Go has no while loops. Actually, all the logic of a while construct can be achieved using for.

# 2.7 ERRORS

All handling operations in Go are based on the type error. An error variable stores a message with information. In situations where an error can occur, the way you want to proceed is to return a filled error information about this. This can be done using the errors.New function.

Assume that there is a situation that may lead to an error, for example accessing a non indexed item from a collection. Example 2.17, the function getMuseteer returns the name of one of the Musketeers. Unfortunately, we cannot control the requested musketeer. If the id argument is outside the limits of the collection, we have an error. Notice that the signature function returns (string, error) types. The way you proceed in these situations is to fill the error with some information and assign the zero value to the return value.

# Example 2.17: Example of error handling.

```
package main

import (
	"errors"
	"fmt"
	"math/rand"
	"time"
)

var Musketeers = []string{
	"Athos", "Porthos", "Aramis", "D'Artagnan",
}

func GetMuseteer(id int) (string, error) {
	if id < 0 || id >= len(Musketeers) {
		return "", errors.New(
		fmt.Sprintf("Invalid id [%d]", id))
	)}
	return Musketeers[id], nil
}
```

| Invalid id [4] |
| [3] D'Artagnan |
| [0] Athos |