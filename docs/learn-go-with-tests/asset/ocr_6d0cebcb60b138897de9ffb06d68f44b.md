```
    return ErrWordExists
default:
    return err
}

    return nil
}
```

Here we are using a `switch` statement to match on the error. Having a `switch` like this provides an extra safety net, in case `Search` returns an error other than `ErrNotFound`.

# Refactor

We don't have too much to refactor, but as our error usage grows we can make a few modifications.

```
const (
    ErrNotFound    = DictionaryErr("could not find the word you w
    ErrWordExists = DictionaryErr("cannot add word because it al
)

type DictionaryErr string

func (e DictionaryErr) Error() string {
    return string(e)
}
```

We made the errors constant; this required us to create our own `DictionaryErr` type which implements the `error` interface. You can read more about the details in [this excellent article by Dave Cheney](...). Simply put, it makes the errors more reusable and immutable.

Next, let's create a function to `Update` the definition of a word.

# Write the test first