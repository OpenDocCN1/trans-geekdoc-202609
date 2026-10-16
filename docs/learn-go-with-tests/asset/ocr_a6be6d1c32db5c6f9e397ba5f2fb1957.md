```
```go
func BalanceFor(transactions []Transaction, name string) float64
return 0.0
}
```
```

When you run the test you should see the following:

```
```
=== RUN TestBadBank
bad_bank_test.go:19: got 0, want 100
bad_bank_test.go:20: got 0, want -75
bad_bank_test.go:21: got 0, want -25
--- FAIL: TestBadBank (0.00s)
```
```

# Write enough code to make it pass

Let's write the code as if we didn't have a Reduce function first.

```
```go
func BalanceFor(transactions []Transaction, name string) float64
var balance float64
for _, t := range transactions {
	if t.From == name {
		balance -= t.Sum
	}
	if t.To == name {
		balance += t.Sum
	}
}
return balance
}
```
```



At this point, have some source control discipline and commit your work. We have working software, ready to challenge Monzo, Barclays, et al.