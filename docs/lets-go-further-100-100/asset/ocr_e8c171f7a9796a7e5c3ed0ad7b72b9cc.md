```
...
#
================================================================================
====== #
# BUILD
#
================================================================================
====== #

current_time = $(shell date --iso-8601=seconds)
linker_flags = '-s -X main.buildTime=${current_time}'

## build/api: build the cmd/api application
.PHONY: build/api
build/api:
    @echo 'Building cmd/api...'
    go build -ldflags=${linker_flags} -o=./bin/api ./cmd/api
    GOOS=linux GOARCH=amd64 go build -ldflags=${linker_flags} -o=./bin/linux_amd64/api ./cmd/api
```

# Automated version numbering with Git

If you’re using Git to version control your source code, then it’s possible to extend the ideas we’ve talked about in this chapter to create *automated version numbers* for your application based on your Git commits.