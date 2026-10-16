Then, we’ll create a table of the outcomes for several combinations of betting:

```
In [20]:
base_bets = np.arange(1,12,2)
mark_bet, andy_bet = np.meshgrid(base_bets, base_bets)

mark_winnings = .1 * andy_bet + .9 * -mark_bet

df = pd.DataFrame(mark_winnings,
                index =base_bets,
                columns=base_bets)
df.index.name = "Andy Bet"
df.columns.name = "Mark Bet"

print("Best Betting Scenario (for Mark) for These Values:")
print("(Andy, Mark):", df_names(df, simple_argmax(mark_winnings)))

display(df)
```

Best Betting Scenario (for Mark) for These Values:
(Andy, Mark): (11, 1)

| Mark Bet | 1 | 3 | 5 | 7 | 9 | 11 |
|---|---|---|---|---|---|---|
| Andy Bet |  |  |  |  |  |  |
| 1 | -0.8000 | -2.6000 | -4.4000 | -6.2000 | -8.0000 | -9.8000 |
| 3 | -0.6000 | -2.4000 | -4.2000 | -6.0000 | -7.8000 | -9.6000 |
| 5 | -0.4000 | -2.2000 | -4.0000 | -5.8000 | -7.6000 | -9.4000 |
| 7 | -0.2000 | -2.0000 | -3.8000 | -5.6000 | -7.4000 | -9.2000 |
| 9 | 0.0000 | -1.8000 | -3.6000 | -5.4000 | -7.2000 | -9.0000 |
| 11 | 0.2000 | -1.6000 | -3.4000 | -5.2000 | -7.0000 | -8.8000 |

That’s pretty interesting. Recall from our discussion above: if my overall expected winnings are zero, so are Andy’s. The best outcome for me, not surprisingly, is in the lower-left corner of that table. It occurs when I wager $1 and Andy wagers $11. That’s my lowest bet and Andy’s highest bet. Now, if Andy is willing to play a game where I bet $1 and he bets $99, things are looking very different for me. I win 10% of the time, so I’m looking at .1 × $99 + .9 × −$1 = 9. If we played this game with these bets many times, I’d start coming out ahead. Things are looking up for ol’ Marco. What about the break-even point? That’s where the winnings for both of us are the same, $0.00. It’s close to the bottom-left corner: I wager $1 and Andy wagers $9. Compare