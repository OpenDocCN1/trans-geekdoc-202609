You may be asking yourself why I am doing `league[i].Wins++` rather than `player.Wins++`.

When you `range` over a slice you are returned the current index of the loop (in our case `i`) and a *copy* of the element at that index. Changing the `Wins` value of a copy won't have any effect on the `league` slice that we iterate on. For that reason, we need to get the reference to the actual value by doing `league[i]` and then changing that value instead.

If you run the tests, they should now be passing.

# Refactor

In `GetPlayerScore` and `RecordWin`, we are iterating over `[]Player` to find a player by name.

We could refactor this common code in the internals of `FileSystemStore` but to me, it feels like this is maybe useful code we can lift into a new type. Working with a "League" so far has always been with `[]Player` but we can create a new type called `League`. This will be easier for other developers to understand and then we can attach useful methods onto that type for us to use.

Inside `league.go` add the following

```
```go
//league.go
type League []Player

func (l League) Find(name string) *Player {
    for i, p := range l {
        if p.Name == name {
            return &l[i]
        }
    }
    return nil
}
```
```