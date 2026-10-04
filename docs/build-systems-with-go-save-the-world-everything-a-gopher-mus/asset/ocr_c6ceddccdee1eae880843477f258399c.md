Log levels help identify the severity of messages and can be set on the fly using the global level variable. Example 16.4 changes the global level from Debug to Info. Notice that after setting the info level, debug messages are discarded.

# Example 16.4: Set global level zerolog.

```
package main

import (
	"github.com/rs/zerolog/log"
	"github.com/rs/zerolog"
)

func main() {
	zerolog.SetGlobalLevel(zerolog.DebugLevel)
	log.Debug().Msg("Debug message is displayed")
	log.Info().Msg("Info message is displayed")

	zerolog.SetGlobalLevel(zerolog.InfoLevel)
	log.Debug().Msg("Debug message is no longer displayed")
	log.Info().Msg("Info message is displayed")
}
```

```
{"level":"Debug","time":"2021-02-08T12:56:01.000Z","message":"Debug message is displayed"}
{"level":"info","time":"2021-02-08T12:56:01.000Z","message":"Info message is displayed"}
{"level":"info","time":"2021-02-08T12:56:01.000Z","message":"Info message is displayed"}
```

Zerolog provides messages within a context. This context has zero or more variables accompanying the logging message. Variables are typed and can be added on the fly as like shown in Example 16.5. A complete list of available types can be found at the official documentation 45.

# Example 16.5: Set message context.

```
package main

import(
	"github.com/rs/zerolog/log"
)

func main() {
	log.Info().Str("mystr","this is a string").Msg("")
	log.Info().Int("myint",1234).Msg("")
	log.Info().Int("myint",1234).Str("str","some string").Msg("And a regular message")
}
```