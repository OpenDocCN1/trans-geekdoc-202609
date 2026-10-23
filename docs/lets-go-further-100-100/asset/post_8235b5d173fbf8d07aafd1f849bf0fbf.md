
{"level":"INFO","time":"2021-04-18T11:17:49Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-18T11:17:49Z","message":"starting server","properties":{"addr":":4000","env":"development"}}

**Hint:** If you’re not comfortable with the DSN value (which contains a password) being displayed on your screen when you type `make run/api`, remember that you can use the `@` character in your makefile to suppress that command from being echoed.

## Using a .envrc file

If you like, you could also *remove* the `GREENLIGHT_DB_DSN` environment variable from your `$HOME/.profile` or `$HOME/.bashrc` files, and store it in a `.envrc` file in the root of your project directory instead.

If you’re following along, go ahead and create a new `.envrc` file like so:

```
$ touch .envrc
```

```
File: .envrc

export GREENLIGHT_DB_DSN=postgres://greenlight:pa55word@localhost/greenlight
```

You can then use a tool like `direnv` to automatically load the variables from the `.envrc` file into your current shell, or alternatively, you can add an `include` command at the top of your `Makefile` to load them instead. Like so:

```
File: Makefile

# Include variables from the .envrc file
include .envrc

## help: print this help message
.PHONY: help
help:
    @echo 'Usage:'
    @sed -n 's/^##//p' ${MAKEFILE_LIST} | column -t -s ':' | sed -e 's/^/ /'
...
```

This approach is particularly convenient in projects where you need to make frequent changes to your environment variables, because it means that you can just edit the `.envrc` file without needing to reboot your computer or run `source` after each change.

Another nice benefit of this approach is that it provides a degree of separation between variables if you’re working on multiple projects on the same machine.

**Important:** If you use this approach and your `.envrc` file contains any secrets, you must be careful to not commit the file into a version control system (like Git or Mercurial).

In a few chapters time we’ll start version controlling our codebase with Git, so let’s preemptively add an ignore rule so that the `.envrc` file is never committed.

```
$ echo '.envrc' >> .gitignore
```

## Quality Controlling Code

In this chapter we’re going to focus on adding an `audit` rule to our `Makefile` to check, test and tidy up our codebase automatically. In particular, the rule will:

- Use the `go mod tidy` command to prune any unused dependencies from the `go.mod` and `go.sum` files, and add any missing dependencies.
- Use the `go mod verify` command to check that the dependencies on your computer (located in your module cache located at `$GOPATH/pkg/mod`) haven’t been changed since they were downloaded and that they match the cryptographic hashes in your `go.sum` file. Running this helps ensure that the dependencies being used are the exact ones that you expect.
- Use the `go fmt ./...` command to format all `.go` files in the project directory, according to the Go standard. This will reformat files ‘in place’ and output the names of any changed files.
- Use the `go vet ./...` command to check all `.go` files in the project directory. The `go vet` tool runs a variety of *analyzers* which carry out static analysis of your code and warn you about things which might be wrong but won’t be picked up by the compiler — such as unreachable code, unnecessary assignments, and badly-formed build tags.
- Use the `go test -race -vet=off ./...` command to run all tests in the project directory. By default, `go test` automatically executes a small subset of the `go vet` checks before running any tests, so to avoid duplication we’ll use the `-vet=off` flag to turn this off. The `-race` flag enables Go’s [race detector](#), which can help pick up certain classes of race conditions while tests are running.
- Use the third-party `staticcheck` tool to carry out some additional [static analysis checks](#).

If you’re following along, you’ll need to install the `staticcheck` tool on your machine at this point. The simplest way to do this is by running the `go install` command like so:

```shell
$ go install honnef.co/go/tools/cmd/staticcheck@latest
go: downloading honnef.co/go/tools v0.1.3
go: downloading golang.org/x/tools v0.1.0
go: downloading github.com/BurntSushi/toml v0.3.1
go: downloading golang.org/x/sys v0.0.0-20210119212857-b64e53b001e4
go: downloading golang.org/x/xerrors v0.0.0-20200804184101-5ec99f83aff1
go: downloading golang.org/x/mod v0.3.0
$ which staticcheck
/home/alex/go/bin/staticcheck
```

> **Note:** If nothing is found by the `which` command, check that your `$GOPATH/bin` directory is on your system path. If you’re not sure where your `$GOPATH` directory is, you can find out by running `go env GOPATH` from your terminal.

Once that’s installed, let’s go ahead and create a new audit rule in our makefile. While we’re at it, let’s also add some comment blocks to help organize and clarify the purpose of our different makefile rules, like so:

```
File: Makefile

include .envrc

#
================================================================================
====== #
# HELPERS
#
================================================================================
====== #

## help: print this help message
.PHONY: help
help:
    @echo 'Usage:'
    @sed -n 's/^##//p' ${MAKEFILE_LIST} | column -t -s ':' |  sed -e 's/^/ /'

.PHONY: confirm
confirm:
    @echo -n 'Are you sure? [y/N] ' && read ans && [ $${ans:-N} = y ]

#
================================================================================
====== #
# DEVELOPMENT
#
================================================================================
====== #
```

```
## run/api: run the cmd/api application
.PHONY: run/api
run/api:
    go run ./cmd/api -db-dsn=${GREENLIGHT_DB_DSN}

## db/psql: connect to the database using psql
.PHONY: db/psql
db/psql:
    psql ${GREENLIGHT_DB_DSN}

## db/migrations/new name=$1: create a new database migration
.PHONY: db/migrations/new
db/migrations/new:
    @echo 'Creating migration files for ${name}...'
    migrate create -seq -ext=.sql -dir=./migrations ${name}

## db/migrations/up: apply all up database migrations
.PHONY: db/migrations/up
db/migrations/up: confirm
    @echo 'Running up migrations...'
    migrate -path ./migrations -database ${GREENLIGHT_DB_DSN} up

#
================================================================================
====== #
# QUALITY CONTROL
#
================================================================================
====== #

## audit: tidy dependencies and format, vet and test all code
.PHONY: audit
audit:
    @echo 'Tidying and verifying module dependencies...'
    go mod tidy
    go mod verify
    @echo 'Formatting code...'
    go fmt ./...
```

```
@echo 'Vetting code...'
go vet ./...
staticcheck ./...
@echo 'Running tests...'
go test -race -vet=off ./...
```

Now that’s done, all you need to do is type make audit to run these checks before you commit any code changes into your version control system or build any binaries.

Let’s give it a try. If you’ve been following along closely, the output should look very similar to this:

```
$ make audit
Tidying and verifying module dependencies...
go mod tidy
go: finding module for package gopkg.in/mail.v2
go: downloading gopkg.in/mail.v2 v2.3.1
go: found gopkg.in/mail.v2 in gopkg.in/mail.v2 v2.3.1
go mod verify
all modules verified
Formatting code...
go fmt ./...
Vetting code...
go vet ./...
staticcheck ./...
Running tests...
go test -race -vet=off ./...
?       greenlight.alexedwards.net/cmd/api          [no test files]
?       greenlight.alexedwards.net/cmd/examples/cors/preflight  [no test files]
?       greenlight.alexedwards.net/cmd/examples/cors/simple      [no test files]
?       greenlight.alexedwards.net/internal/data          [no test files]
```

```
?  greenlight.alexedwards.net/internal/jsonlog  [no test files]
?  greenlight.alexedwards.net/internal/mailer  [no test files]
?  greenlight.alexedwards.net/internal/validator  [no test files]
```

That's looking good. The `go mod tidy` command resulted in some additional packages needing to be downloaded, but apart from that, all the checks completed successfully without any problems.

## Additional Information

## Testing

We covered the topic of testing in a lot of detail in the first *Let's Go* book, and the same principles apply again here. If you like, feel free to revisit the testing section of *Let's Go* and re-implement some of those same patterns in your API. For example, you might like to try:

- Creating an end-to-end test for the `GET /v1/healthcheck` endpoint to verify that the headers and response body are what you expect.
- Creating a unit-test for the `rateLimit()` middleware to confirm that it sends a `429 Too Many Requests` response after a certain number of requests.
- Creating an end-to-end integration test, using a test database instance, which confirms that the `authenticate()` and
