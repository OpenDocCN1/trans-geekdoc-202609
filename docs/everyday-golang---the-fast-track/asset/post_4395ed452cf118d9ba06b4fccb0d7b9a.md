
```
return "", fmt.Errorf("no title found")
}
```

We then add a workQueue concept and a number of workers (Goroutines) which read from the queue. A WaitGroup then allows each worker to signal when it has completed processing.

```go
package main

import (
    "context"
    "flag"
    "fmt"
    "io"
    "log"
    "net/http"
    "os"
    "strings"
    "sync"
    "time"
)

func main() {
    uris := []string{"https://github.com/alexellis",
        "https://github.com/openfaas",
        "https://github.com/inlets",
        "https://github.com/docker",
        "https://github.com/kubernetes",
        "https://github.com/moby",
        "https://github.com/hashicorp",
        "https://github.com/civo",
    }

    var w int
    flag.IntVar(&w, "w", 1, "amount of workers")
    flag.Parse()

    titleMap, errs := fetch(uris, w)
    if len(errs) > 0 {
        for _, err := range errs {
            fmt.Fprintf(os.Stderr, "error %s", err.Error())
        }
        os.Exit(1)
    }

    for k, v := range titleMap {
        fmt.Printf("%s has %s\n", k, v)
    }
}

func fetch(uris []string, workers int) (map[string]string, []error) {
    titles := make(map[string]string)

    var errs []error

    workQueue := make(chan string)

    wg := sync.WaitGroup{}
    wg.Add(workers)
    for i := 0; i < workers; i++ {
        worker := i
        go func(worker int, workQueue chan string) {
            log.Printf("[Worker: %d] Started work.", worker)

            for uri := range workQueue {
                log.Printf("[Worker: %d] Getting: %s", worker, uri)

                start := time.Now()
                title, err := titleOf(uri, time.Second*5)
                if err != nil {
                    errs = append(errs, err)
                }
                log.Printf("[Worker: %d] Got: %s (%.2fs)",
                    worker,
                    uri,
                    time.Since(start).Seconds())

                titles[uri] = title
            }
            log.Printf("[Worker: %d] Finished work.", worker)
            wg.Done()
        }(worker, workQueue)
    }

    go func() {
        for _, u := range uris {
            workQueue <- u
        }
        close(workQueue)
    }()

    wg.Wait()
    return titles, errs
}
```

The -w flag controls concurrency.

Observe the difference in output and time taken with a single worker and with 4.

```
$ time go run main.go -w 1
2021/06/18 18:42:30 [Worker: 0] Started work.
2021/06/18 18:42:30 [Worker: 0] Getting: https://github.com/alexellis
2021/06/18 18:42:32 [Worker: 0] Got: https://github.com/alexellis (1.82s)
2021/06/18 18:42:32 [Worker: 0] Getting: https://github.com/openfaas
2021/06/18 18:42:33 [Worker: 0] Got: https://github.com/openfaas (0.60s)
2021/06/18 18:42:33 [Worker: 0] Getting: https://github.com/inlets
2021/06/18 18:42:33 [Worker: 0] Got: https://github.com/inlets (0.44s)
2021/06/18 18:42:33 [Worker: 0] Getting: https://github.com/docker
2021/06/18 18:42:34 [Worker: 0] Got: https://github.com/docker (0.70s)
2021/06/18 18:42:34 [Worker: 0] Getting: https://github.com/kubernetes
2021/06/18 18:42:34 [Worker: 0] Got: https://github.com/kubernetes (0.55s)
2021/06/18 18:42:34 [Worker: 0] Getting: https://github.com/moby
2021/06/18 18:42:35 [Worker: 0] Got: https://github.com/moby (0.47s)
2021/06/18 18:42:35 [Worker: 0] Getting: https://github.com/hashicorp
2021/06/18 18:42:35 [Worker: 0] Got: https://github.com/hashicorp (0.45s)
2021/06/18 18:42:35 [Worker: 0] Getting: https://github.com/civo
2021/06/18 18:42:36 [Worker: 0] Got: https://github.com/civo (0.86s)
2021/06/18 18:42:36 [Worker: 0] Finished work.
https://github.com/openfaas has    <title>OpenFaaS · GitHub</title>
https://github.com/inlets has      <title>inlets · GitHub</title>
https://github.com/docker has      <title>Docker · GitHub</title>
https://github.com/kubernetes has  <title>Kubernetes · GitHub</title>
https://github.com/moby has        <title>Moby · GitHub</title>
https://github.com/hashicorp has   <title>HashiCorp · GitHub</title>
https://github.com/civo has        <title>Civo · GitHub</title>
https://github.com/alexellis has   <title>alexellis (Alex Ellis) · GitHub</title>

real    0m6.206s
user    0m0.556s
sys     0m0.188s
```

```
$ time go run main.go -w 4
2021/06/18 18:41:56 [Worker: 0] Started work.
2021/06/18 18:41:56 [Worker: 0] Getting: https://github.com/alexellis
2021/06/18 18:41:56 [Worker: 3] Started work.
2021/06/18 18:41:56 [Worker: 3] Getting: https://github.com/openfaas
2021/06/18 18:41:56 [Worker: 2] Started work.
2021/06/18 18:41:56 [Worker: 1] Started work.
2021/06/18 18:41:56 [Worker: 1] Getting: https://github.com/docker
2021/06/18 18:41:56 [Worker: 2] Getting: https://github.com/inlets
2021/06/18 18:41:57 [Worker: 2] Got: https://github.com/inlets (0.55s)
2021/06/18 18:41:57 [Worker: 2] Getting: https://github.com/kubernetes
2021/06/18 18:41:57 [Worker: 3] Got: https://github.com/openfaas (0.65s)
2021/06/18 18:41:57 [Worker: 3] Getting: https://github.com/moby
2021/06/18 18:41:57 [Worker: 1] Got: https://github.com/docker (0.89s)
2021/06/18 18:41:57 [Worker: 1] Getting: https://github.com/hashicorp
2021/06/18 18:41:57 [Worker: 2] Got: https://github.com/kubernetes (0.46s)
2021/06/18 18:41:57 [Worker: 2] Getting: https://github.com/civo
2021/06/18 18:41:58 [Worker: 3] Got: https://github.com/moby (0.70s)
2021/06/18 18:41:58 [Worker: 3] Finished work.
2021/06/18 18:41:58 [Worker: 0] Got: https://github.com/alexellis (1.45s)
2021/06/18 18:41:58 [Worker: 0] Finished work.
2021/06/18 18:41:58 [Worker: 2] Got: https://github.com/civo (0.53s)
2021/06/18 18:41:58 [Worker: 2] Finished work.
2021/06/18 18:41:58 [Worker: 1] Got: https://github.com/hashicorp (1.15s)
2021/06/18 18:41:58 [Worker: 1] Finished work.
https://github.com/docker has    <title>Docker · GitHub</title>
https://github.com/kubernetes has    <title>Kubernetes · GitHub</title>
https://github.com/moby has    <title>Moby · GitHub</title>
https://github.com/alexellis has    <title>alexellis (Alex Ellis) · GitHub</title>
https://github.com/civo has    <title>Civo · GitHub</title>
https://github.com/hashicorp has    <title>HashiCorp · GitHub</title>
https://github.com/inlets has    <title>inlets · GitHub</title>
https://github.com/openfaas has    <title>OpenFaaS · GitHub</title>

real    0m2.319s
user    0m0.545s
sys     0m0.101s
```

That’s a difference of around 4 seconds. We gained that speed simply by implementing concurrency. The work queue then limits the amount of open requests.

To see this pattern in action, within the faas-cli, checkout the build.go command.

## Chapter 8
## Store data with a database

Almost all line of business applications will require a form of storage, so in this chapter I'll show you how to connect to a PostgreSQL database. For other databases, you'll need to find a different library, but the approach will be similar.

Not all Go libraries are equal. Some use pure Go code, and others link to a rich ecosystem of existing C/C++ codebases. The ones which reference Go require CGO, which can introduce a number of other issues and portability problems.

One of the most helpful tools I've found for writing this eBook has been a todo list, so let's start with that example. You can then customise the schema, the fields and operations however you like to suit your own needs.

Create a directory for the exercise:

```
export GH_USERNAME="alexellis"
mkdir -p $GOPATH/src/github.com/$GH_USERNAME/todo-database/
cd $GOPATH/src/github.com/$GH_USERNAME/todo-database/
```

Create schema.sql:

```
CREATE TABLE todo (
  id            INT GENERATED ALWAYS AS IDENTITY,
  description   text NOT NULL,
  created_date  timestamp NOT NULL,
  completed_date timestamp NULL
);
```

We're using a flat schema, with a single table. The id field is generated, and then we have a longer field for the todo text and a created/completed date field. Only the completed_date field can accept a null entry.

Once you have defined a schema, it's time to provision a database or to install PostgreSQL so that you can obtain credentials or a connection string and create the schema.

I decided to create a database using PostgreSQL 11 on DigitalOcean. This is a managed service, and you'll find similar services are available from other cloud providers such as AWS and GCP.

You can use the psql tool to connect and create a database. Alternatively, you could input a CREATE statement at the start of your application. Some authors write code to automate maintenance like database creation and schema migration upon application startup.

My connection string from the dashboard was: postgresql://doadmin:ildkg2my7g7lqqxh@todo-pg11-do-user-2197152-0.b.db.ondigitalocean.com:25060/defaultdb?sslmode=require

When you deploy your application, be careful that you do not hard-code any confidential data. You may want to use a configuration file with strict permissions, or environment variables to read the password and address.
