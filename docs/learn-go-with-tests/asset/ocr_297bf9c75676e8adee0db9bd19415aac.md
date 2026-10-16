```
}
func NewTransaction(from, to Account, sum float64) Transaction {
    return Transaction{From: from.Name, To: to.Name, Sum: sum}
}

type Account struct {
    Name    string
    Balance float64
}

func NewBalanceFor(account Account, transactions []Transaction)
    return Reduce(
        transactions,
        applyTransaction,
        account,
    )
}

func applyTransaction(a Account, transaction Transaction) Accour
    if transaction.From == a.Name {
        a.Balance -= transaction.Sum
    }
    if transaction.To == a.Name {
        a.Balance += transaction.Sum
    }
    return a
}
```

I feel this really shows the power of using concepts like `Reduce`. The `NewBalanceFor` feels more _declarative_, describing _what_ happens, rather than _how_. Often when we're reading code, we're darting through lots of files, and we're trying to understand _what_ is happening, rather than _how_, and this style of code facilitates this well.

If I wish to dig in to the detail I can, and I can see the _business logic_ of `applyTransaction` without worrying about loops and mutating state; `Reduce` takes care of that separately.