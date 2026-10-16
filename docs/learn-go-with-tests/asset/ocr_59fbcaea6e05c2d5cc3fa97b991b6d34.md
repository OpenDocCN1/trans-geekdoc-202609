```
```go
{70 * time.Minute, 1000},
{80 * time.Minute, 2000},
{90 * time.Minute, 4000},
{100 * time.Minute, 8000},
```
```

```
```go
for i, want := range cases {
	t.Run(fmt.Sprintf(want), func(t *testing.T) {
		if len(blindAlerter.alerts) <= i {
			t.Fatalf("alert %d was not scheduled %v", i, bli
		}
		got := blindAlerter.alerts[i]
		assertScheduledAlert(t, got, want)
	})
}
```
```

# Implement assertScheduledAlert yourself.

We've spent a fair amount of time here writing tests and have been somewhat naughty not integrating with our application. Let's address that before we pile on any more requirements.

Try running the app and it won't compile, complaining about not enough args to NewCLI.

Let's create an implementation of BlindAlerter that we can use in our application.

Create BlindAlerter.go and move our BlindAlerter interface and add the new things below

```
```go
package poker

import (
	"fmt"
	"os"
	"time"
)
```
```