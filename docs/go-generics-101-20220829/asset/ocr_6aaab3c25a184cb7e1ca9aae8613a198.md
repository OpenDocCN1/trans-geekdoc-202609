```
type M interface {
    Run() error
    Stop()
    Step() error
}

type N interface {
    Run() error
    Stop()
    Step() error
    Resume()
    ~map[int]bool
    ~[]byte | string
}

type O interface {
    Run() error
    Stop()
    Step() error
    Pause()
    Resume()
    ~map[int]bool
    ~[]byte | string
    string
    int64 | ~chan int | any
}
```

We could view a single type literal, type name or tilde form as a term union with only one term. So simply speaking, since Go 1.18, an interface type may specify some methods and embed some term unions.

An interface type without any embedding elements is called an empty interface. For example, the predeclared any type alias denotes an empty interface type.

# 5.2 Type sets and method sets

Before Go 1.18, an interface type is defined as a method set. Since Go 1.18, an interface type is defined as a type set. A type set only consists of non-interface types.

+   - The type set of a non-interface type literal or type name only contains the type denoted by the type literal or type name.
+   - As just mentioned above, the type set of a tilde form ~T is the set of types whose underlying types are T. In theory, this is an infinite set.
+   - The type set of a method specification is the set of non-interface types whose method sets include the method specification. In theory, this is an infinite set.
+   - The type set of an empty interface is the set of all non-interface types. In theory, this is an infinite set.
+   - The type set of a union of terms T1 | T2 | . . . | Tn is the union of the type sets of the terms.
+   - The type set of a non-empty interface is the intersection of the type sets of its interface elements.

As the type set of an empty interface type (for example, the predeclared any) contains all non-