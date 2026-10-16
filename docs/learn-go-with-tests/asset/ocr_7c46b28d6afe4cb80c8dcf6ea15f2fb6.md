The tests should now compile and run

```
wallet_test.go:15: got 0 want 10
```

# Write enough code to make it pass

We will need some kind of *balance* variable in our struct to store the state

```
type Wallet struct {
    balance int
}
```

In Go if a symbol (variables, types, functions et al) starts with a lowercase symbol then it is private *outside the package it's defined in.*

In our case we want our methods to be able to manipulate this value, but no one else.

Remember we can access the internal balance field in the struct using the "receiver" variable.

```
func (w Wallet) Deposit(amount int) {
    w.balance += amount
}
```

```
func (w Wallet) Balance() int {
    return w.balance
}
```

With our career in fintech secured, run the test suite and bask in the passing test

```
wallet_test.go:15: got 0 want 10
```

# That's not quite right