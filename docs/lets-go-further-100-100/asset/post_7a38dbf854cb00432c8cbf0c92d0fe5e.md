
**Important:** This part of the book is only really relevant if you use Git. If you don’t, then that’s absolutely fine and you can skip ahead to the next chapter with no issues.

Otherwise, if you’re following along (and haven’t done it already), please go ahead and initialize a new Git repository in the root of your project directory:

```
$ git init
Initialized empty Git repository in /home/alex/Projects/greenlight/.git/
```

Then make a new commit containing all the files in your project directory, like so:

```
$ git add .
$ git commit -m "Initial commit"
```

If you look at your commit history using the `git log` command, you’ll see the *hash* for this commit.

```
$ git log
commit 0f8573aab79f3cbee17d39901d5cb200121c7ed1 (HEAD -> master)
Author: Alex Edwards <alex@alexedwards.net>
Date:   Sun Apr 18 18:29:48 2021 +0200

    Initial commit
```

In my case the commit hash is `0f8573aab79f3cbee17d39901d5cb200121c7ed1` — but yours will be a different value.

It’s also possible to use the `git describe` command to get a ‘human-readable’ descriptor for the current state of the repository. Like so:

```
$ git describe --always --dirty
0f8573a
```

In this case, we can see that `git describe` returns an *abbreviated version of the commit hash*. We’re also using the `--dirty` flag, which means that the descriptor will be suffixed with "`-dirty`" if there are any uncommitted changes in the repository. For example `0f8573a-dirty`.

Let’s update our project so that the output from `git describe` is burnt-in to our binaries as the application ‘version number’ when building the executable.

To do this, the first thing that we need to do is switch the `version` constant in our `cmd/api/main.go` file to be a variable, because it’s not possible to ‘burn-in’ a value to a constant.

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
git_description = $(shell git describe --always --dirty)
linker_flags = '-s -X main.buildTime=${current_time} -X main.version=${git_description}'

## build/api: build the cmd/api application
.PHONY: build/api
build/api:
    @echo 'Building cmd/api...'
    go build -ldflags=${linker_flags} -o=./bin/api ./cmd/api
    GOOS=linux GOARCH=amd64 go build -ldflags=${linker_flags} -o=./bin/linux_amd64/api ./cmd/api
```

At this point, let’s quickly run `git describe` again:

```
$ git describe --always --dirty
0f8573a-dirty
```

This output makes sense — the hash of the last commit was `0f8573a...`, and the `-dirty` suffix indicates that our repository now contains uncommitted changes (we've altered the `cmd/api/main.go` and `Makefile` files since the previous commit).

Let’s commit these recent changes, run `make build/api` again, and then check the version number in our binaries. Like so:

```
$ git add .
$ git commit -m "Generate version number automatically"
[master 76c976a] Generate version number automatically
  2 files changed, 6 insertions(+), 7 deletions(-)
```

```
$ make build/api
Building cmd/api...
go build -ldflags='-s -X main.buildTime=2021-04-18T18:43:32+02:00 -X main.version=76c976a' -o=./bin/api ./cmd/api
GOOS=linux GOARCH=amd64 go build -ldflags='-s -X main.buildTime=2021-04-18T18:43:32+02:00 -X main.version=76c976a' -o=./bin/linux_amd64/api ./cmd/api

$ ./bin/api -version
Version:      76c976a
Build time:   2021-04-18T18:43:32+02:00
```

We can see that our binary is now reporting that it was been built from a *clean version of the repository with the commit hash* 76c976a. Let’s cross check this against the `git log` output for the project:

```
$ git log
commit 76c976a07d0fce3d813f3a4748574f81b1e24226 (HEAD -> master)
Author: Alex Edwards <alex@alexedwards.net>
Date:   Sun Apr 18 18:39:17 2021 +0200

    Generate version number automatically

commit 0f8573aab79f3cbee17d39901d5cb200121c7ed1
Author: Alex Edwards <alex@alexedwards.net>
Date:   Sun Apr 18 18:29:48 2021 +0200

    Initial commit
```

That's looking good — the commit hash in our Git history aligns perfectly with our application version number. And that means it’s now easy for us to identify exactly what code a particular binary contains — all we need to do is run the binary with the `-version` flag and then cross-reference it against the Git repository history.

## Using Git tags

In some projects you may want to annotate certain Git commits with tags, often to denote a formal release number.

To illustrate this, let’s add the `v1.0.0` tag to our latest commit like so:

```
$ git tag v1.0.0
$ git log
commit 76c976a07d0fce3d813f3a4748574f81b1e24226 (HEAD -> master, tag: v1.0.0)
Author: Alex Edwards <alex@alexedwards.net>
Date:   Sun Apr 18 18:39:17 2021 +0200

    Generate version number automatically

...
```

If you’re tagging your commits in this way, then it’s a good idea to use the `--tags` and `--long` flags when calling `git describe` to generate the version number for your application. This will force the output to be in the following format:

```
{tag}-{number of additional commits}-g{abbreviated commit hash}
```

Let’s take a quick look at what this currently looks like for our project:

```bash
$ git describe --always --dirty --tags --long
v1.0.0-0-g76c976a
```

So, in this case, we can see from the version number that the repository is based on `v1.0.0`, has 0 additional commits on top of that, and the latest commit hash is `76c976a`. The `g` character which prefixes the commit hash stands for ‘git’, and exists to help distinguish the hash from any hashes generated by other version-control systems.

Let’s update our `Makefile` to use these additional flags when generating the version number, like so:

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
git_description = $(shell git describe --always --dirty --tags --long)
linker_flags = '-s -X main.buildTime=${current_time} -X main.version=${git_description}'

...
```

Then go ahead and commit this change, rebuild the binaries, and check the version number. Your output should look similar to this:

```
$ git add .
$ git commit -m "Use --tags and --long flags when generating version number"
$ make build/api
$ ./bin/api -version
Version:      v1.0.0-1-gf27fd0f
Build time:   2021-04-18T18:54:05+02:00
```

The version number has now been changed to v1.0.0-1-gf27fd0f, indicating that the binary was built using the repository code from commit f27fd0f, which is 1 commit ahead of the v1.0.0 tag.

In terms of infrastructure and architecture, we’ll run everything on a single Ubuntu Linux server. Our stack will consist of a PostgreSQL database and the executable binary for our Greenlight API, operating in much the same way that we have seen so far in this book. But in addition to this, we’ll also run Caddy as a *reverse proxy* in front of the Greenlight API.

Using Caddy has a couple of benefits. It will automatically handle and terminate HTTPS connections for us — including automatically generating and managing TLS certificates via Let’s Encrypt — and we can also use Caddy to easily restrict internet access to our metrics endpoint.

In this section you’ll learn how to:

- Commission an Ubuntu Linux server running on Digital Ocean to host your application.
- Automate the configuration of the server — including creating user accounts, configuring the firewall and installing necessary software.
- Automate the process of updating your application and deploying changes to the server.
- How to run your application as a background service using systemd, as a non-root user.
- Use Caddy as a reverse proxy in front of your application to automatically manage TLS certificates and handle HTTPS connections.
