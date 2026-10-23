```
File: cmd/api/main.go

package main

...

// Remove the hardcoded version number and make version a variable instead of a constant.
var (
    buildTime string
    version   string
)

...
```

And then let's update our Makefile to burn-in the git describe output to the version variable in our application, using the same pattern that we did for the build time. Like so:

```
File: Makefile

...

#
================================================================================
====== #
# BUILD
#
================================================================================
====== #

current_time = $(shell date --iso-8601=seconds)
```