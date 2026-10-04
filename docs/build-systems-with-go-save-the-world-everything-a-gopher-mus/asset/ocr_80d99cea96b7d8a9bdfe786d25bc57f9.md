Certain tests can be utilized test particular code properties. permit triggering other tests using the t.Run() function.

```
func TestFoo(t *testing.T) {
	//
	t.Run("A1", func(t *testing.T) { - })
	t.Run("A2", func(t *testing.T) { - })
	t.Run("B1", func(t *testing.T) { - })
n}
```

In the example below, TestFoo invokes three functions. Subsequently, these testing functions invoke others. The first argument is a string that can be conveniently set as key=value format. This identifies the test and permits us to isolate what tests to be run in the go command.

We show how to work with subtests with a practical example. Because the code can be a bit large to show at once, we split it into two sections for better readability. In this example, we want to test a user type that can be defined in XML and JSON formats. Check Chapter B if you are not familiar with encoders.

# Example 11.4: Subtests in practice (part I).

```
package example_03

import (
	"encoding/json"
	"encoding/xml"
	"errors"
	"fmt"
	"io/ioutil"
	"os"
	"testing"
)

type Encoding int

const (
	XML_Encoding = iota
	JSON
)

type User struct {
	UserID string `xml:"id" json:"userId"`
	Email string `xml:"email" json:"email"`
	Score int `xml:"score" json:"score"`
}

var Users []User

func (u *User) Equal(v User) bool(
```