```
```bash
$ curl -L https://github.com/golang-
migrate/migrate/releases/download/v4.14.1/migrate.linux-amd64.tar.gz | tar
xzv
$ mv migrate.linux-amd64 $GOPATH/bin/migrate
```
```

Before you continue, please check that it’s available and working on your machine by trying to execute the `migrate` binary with the `-version` flag. It should output the current version number similar to this:

```
```bash
$ migrate -version
4.14.1
```
```