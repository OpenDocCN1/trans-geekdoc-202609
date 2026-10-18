# Chapter 4

# Fetch JSON from a HTTP endpoint

This has to be one of the most common tasks for a new Go programmer. You have installed Go, and have started to develop a CLI, now you need to interface with an external API and make a HTTP “GET” call. It's very likely that the API will be using JSON.

We will be querying an endpoint provided for free that tells us how many astronauts are currently in space and what their names are.

We'll be using HTTP and JSON from Go's standard library, and unlike with other languages, we will not need to install any external packages.

# Get started

Make yourself a folder for a new project (you can use your Github username here):

```
export GH_USERNAME="alexellis"
mkdir -p $GOPATH/src/github.com/$GH_USERNAME/get-json/
cd $GOPATH/src/github.com/$GH_USERNAME/get-json/
```

Now save a new file named main.go:

```
package main

func main() {

}
```

This program is effectively hello-world without any print statements.

Go ahead and run the program, you have two ways to do this:

```
go run main.go
```

Or build a binary, then run it.

```
go build
./get-json
```

Now add a print statement:

```
package main

import "fmt"

func main() {
```