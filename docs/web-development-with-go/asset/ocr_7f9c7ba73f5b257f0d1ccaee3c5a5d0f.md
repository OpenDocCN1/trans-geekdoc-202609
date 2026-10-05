```
db.LogMode(true)
db.AutoMigrate(&User)
}
```

With logging enabled we will start to see output like the following when SQL statements are run.

```
(/Users/jon/go/src/lenslocked.com/exp/main.go:35)
[2017-07-18 17:04:12] [6.85ms] CREATE TABLE "users" ...

(/Users/jon/go/src/lenslocked.com/exp/main.go:35)
[2017-07-18 17:04:12] [1.18ms] CREATE INDEX ...

(/Users/jon/go/src/lenslocked.com/exp/main.go:35)
[2017-07-18 17:04:12] [1.00ms] CREATE UNIQUE INDEX ...
```

You will only see output this when SQL statements are actually run, so if you have already created your users table you won't see this output. If you would like, you can drop the users table and then rerun your code to see output like above.

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/8.4.4

Changes - book.usegolang.com/8.4.4-diff