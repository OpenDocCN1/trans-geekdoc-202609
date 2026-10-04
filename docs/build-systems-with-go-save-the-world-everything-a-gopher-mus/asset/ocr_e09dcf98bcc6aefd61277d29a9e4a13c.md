```
package main

import (
	"github.com/rs/zerolog"
	"github.com/rs/zerolog/log"
	"math/rand"
)

type ComponentHook struct {
	component string
}

func (h ComponentHook) Run(e *zerolog.Event, level zerolog.Level, msg string) {
	if level == zerolog.DebugLevel {
		e.Str("component", h.component)
	}
}

type RandomHook struct{}

func (r RandomHook) Run(e *zerolog.Event, level zerolog.Level, msg string) {
	e.Int("random", rand.Int())
}

func main() {
	logger := log.Hook(ComponentHook("moduleA"))
	logger = logger.Hook(RandomHook())
	logger.Info().Msg("Info message")
	logger.Debug().Msg("Debug message")
}
```

| {\level":"info","time":"2021-02-08T16:37+01:00","random":"5577006791947794140","message":"Info message"} |
| {\level":"debug","time":"2021-02-01"} |
| 0813:16:36:37+01:00,"component":"moduleA","random":"8674652238082153551","message":"Debug message" |

# 16.4.Sampling

Logging messages can be particularly disturbing when executed inside loops. It becomes worse for a large number of iterations. Zerolog provides sampling loggers that can be configured to adequate the number of generated log messages. The log Sample function returns a Logger based on a Sample type. The sampler only contains a sample method that returns true when a message has been sampled.

The basicSampler samples a message every N calls. This is particularly useful inside loops, like in Example 16.14, where a message is printed every 200 iterations inside a loop of 1000 iterations.

Example 16.14: Logger using basic sampler.