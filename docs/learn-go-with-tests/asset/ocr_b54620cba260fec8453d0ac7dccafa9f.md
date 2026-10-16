collection of A into a B. In our case from Transaction to float64.

This makes Reduce more general-purpose and reusable, and still type-safe. If you try and run the tests again they should compile, and pass.

# Extending the bank

For fun, I wanted to improve the ergonomics of the bank code. I've omitted the TDD process for brevity.

```
func TestBadBank(t *testing.T) {
    var (
        riya  = Account{Name: "Riya", Balance: 100}
        chris = Account{Name: "Chris", Balance: 75}
        adil  = Account{Name: "Adil", Balance: 200}

        transactions = []Transaction{
            NewTransaction(chris, riya, 100),
            NewTransaction(adil, chris, 25),
        }
    )

    newBalanceFor := func(account Account) float64 {
        return NewBalanceFor(account, transactions).Balance
    }

    AssertEqual(t, newBalanceFor(riya), 200)
    AssertEqual(t, newBalanceFor(chris), 0)
    AssertEqual(t, newBalanceFor(adil), 175)
}
```

And here's the updated code

```
package main

type Transaction struct {
    From string
    To   string
    Sum  float64
```