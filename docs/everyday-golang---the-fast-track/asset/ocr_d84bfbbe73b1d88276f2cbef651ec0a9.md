```
```
}
return todos, nil
}
```
```

Then it’s over to you, to try it out:

```
```shell
$ go build && ./todo \
  -user doadmin \
  -password ildkg2my7g7lqqxh \
  -host todo-pg11-do-user-2197152-0.b.db.ondigitalocean.com \
  -port 25060 \
  -dbname defaultdb \
  -todo "Publish this book" \
  -action create
```
```

Now list your todo items:

```
```shell
$ go build && ./todo \
  -user doadmin \
  -password ildkg2my7g7lqqxh \
  -host todo-pg11-do-user-2197152-0.b.db.ondigitalocean.com \
  -port 25060 \
  -dbname defaultdb \
  -action list

- "Publish this book"   2021-06-21 10:57:04.374785 +0000 +0000
```
```

Next, you could explore adding the missing functionality, and consider using a table and adding some colour. You may also want to filter out all items which have a completed date. Check out the tabwriter package for formatting your CLI output.

A CLI framework like Cobra, could improve usability by making the actions into verbs such as:

```
```shell
$ ./todo list
$ ./todo create "Publish the next version of this eBook"
$ ./todo close "Weekly shopping"
```
```

Find out more about the two libraries we used below:

+   - lib/pq
+   - database/sql

For a more complete example of data-access including a schema with a foreign key relationship and custom database functions, see my example on the OpenFaaS blog: How to build a Serverless Single Page App