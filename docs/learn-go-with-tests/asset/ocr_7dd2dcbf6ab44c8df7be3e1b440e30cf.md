```
}
}
```

# And then update the caller

```
t.Run("Withdraw insufficient funds", func(t *testing.T) {
    startingBalance := Bitcoin(20)
    wallet := Wallet{startingBalance}
    err := wallet.Withdraw(Bitcoin(100))

    assertError(t, err, "cannot withdraw, insufficient funds")
    assertBalance(t, wallet, startingBalance)
})
```

We've introduced t.Fatal which will stop the test if it is called. This is because we don't want to make any more assertions on the error returned if there isn't one around. Without this the test would carry on to the next step and panic because of a nil pointer.

# Try to run the test

```
wallet_test.go:61: got err 'oh no' want 'cannot withdraw, insufficient funds'
```

# Write enough code to make it pass

```
func (w *Wallet) Withdraw(amount Bitcoin) error {
    if amount > w.balance {
        return errors.New("cannot withdraw, insufficient funds")
    }

    w.balance -= amount

    return nil
}
```