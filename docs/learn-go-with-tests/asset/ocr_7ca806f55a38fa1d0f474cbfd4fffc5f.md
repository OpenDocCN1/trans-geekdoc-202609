```
want := Bitcoin(10)

if got != want {
    t.Errorf("got %s want %s", got, want)
}
})
}
```

# Try to run the test

./wallet_test.go:26:9: wallet.Withdraw undefined (type Wallet has no field or method Withdraw)

# Write the minimal amount of code for the test to run and check the failing test output

```
func (w *Wallet) Withdraw(amount Bitcoin) {

}
```

wallet_test.go:33: got 20 BTC want 10 BTC

# Write enough code to make it pass

```
func (w *Wallet) Withdraw(amount Bitcoin) {
    w.balance -= amount
}
```

# Refactor

There's some duplication in our tests, lets refactor that out.