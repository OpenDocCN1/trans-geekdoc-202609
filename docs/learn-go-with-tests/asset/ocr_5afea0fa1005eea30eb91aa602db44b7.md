```
```go
func TestWallet(t *testing.T) {
    wallet := Wallet{}
    wallet.Deposit(Bitcoin(10))
    got := wallet.Balance()
    want := Bitcoin(10)
    if got != want {
        t.Errorf("got %d want %d", got, want)
    }
}
```
```

To make `Bitcoin` you just use the syntax `Bitcoin(999)`.

By doing this we're making a new type and we can declare *methods* on them. This can be very useful when you want to add some domain specific functionality on top of existing types.

# Let's implement Stringer on Bitcoin

```
```go
type Stringer interface {
    String() string
}
```
```

This interface is defined in the `fmt` package and lets you define how your type is printed when used with the `%s` format string in prints.

```
```go
func (b Bitcoin) String() string {
    return fmt.Sprintf("%d BTC", b)
}
```
```

As you can see, the syntax for creating a method on a type declaration is the same as it is on a struct.

Next we need to update our test format strings so they will use `String()` instead.