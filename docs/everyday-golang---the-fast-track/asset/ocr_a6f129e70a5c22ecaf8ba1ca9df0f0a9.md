```
```go
}
defer res.Body.Close()

body, err := io.ReadAll(res.Body)
if err != nil {
	return []byte{}, err
}

return body, nil
}
```
```

Next, let’s write the new main.go file that uses the interface and the real LiveGetWebRequest implementation:

```
```go
package main

import (
	"encoding/json"
	"fmt"

	"github.com/alexellis/isolate-astros/astros"
)

func getAstronauts(getWebRequest astros.GetWebRequest) (int, error) {
	url := "http://api.open-notify.org/astros.json"
	body, err := getWebRequest.FetchBytes(url)
	if err != nil {
		return 0, err
	}
	peopleResult := astros.People{}

	if err := json.Unmarshal(body, &peopleResult); err != nil {
		return 0, err
	}
	return peopleResult.Number, err
}

func main() {
	liveClient := astros.LiveGetWebRequest{}
	number, err := getAstronauts(liveClient)
	if err != nil {
		panic(err)
	}
	fmt.Println(number)
}
```
```

Test it out to make sure it all works:

```
```text
go run .
7
```
```

Next create the unit test main_test.go:

```
```go
package main

import "testing"
```
```