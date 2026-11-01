
# Monte Carlo Simulation and Game AI History

## Monte Carlo Tree Search Origins

Monte Carlo simulation was pioneered by Metropolis and Ulam (1949) for calculations related to the development of the atomic bomb. Monte Carlo tree search (`MCTS`) was introduced by Abramson (1987). Tesauro and Galperin (1997) showed how a Monte Carlo search could be combined with an evaluation function for the game of backgammon. Early playout termination is studied by Lorentz (2015). `ALPHAGO` terminated playouts and applied an evaluation function (Silver et al., 2016). Kocsis and Szepesvari (2006) refined the approach with the “Upper Confidence Bounds applied to Trees” selection mechanism. Chaslot et al. (2008) show how `MCTS` can be applied to a variety of games and Browne et al. (2012) give a survey.

## Partially Observable Games

Koller and Pfeffer (1997) describe a system for completely solving partially observable games. It handles larger games than previous systems, but not the full version of complex games like poker and bridge. Frank et al. (1998) describe several variants of Monte Carlo search for partially observable games, including one where MIN has complete information but MAX does not. Schofield and Thielscher (2015) adapt a general game-playing system for partially observable games.

## Kriegspiel

Ferguson hand-derived randomized strategies for winning Kriegspiel with a bishop and knight (1992) or two bishops (1995) against a king. The first Kriegspiel programs concentrated on finding endgame checkmates and performed AND–OR search in belief-state space (Sakuta and Iida, 2002; Bolognesi and Ciancarini, 2003). Incremental belief-state algorithms enabled much more complex midgame checkmates to be found (Russell and Wolfe, 2005; Wolfe and Russell, 2007), but efficient state estimation remains the primary obstacle to effective general play (Parker et al., 2005). Ciancarini and Favini (2010) apply `MCTS` to Kriegspiel, and Wang et al. (2018b) describe a belief-state version of `MCTS` for Phantom Go.

## Chess

### Chess Milestones and Fredkin Prize

Chess milestones have been marked by successive winners of the Fredkin Prize: `BELLE` (Condon and Thompson, 1982), the first program to achieve master status; `DEEP THOUGHT` (Hsu et al., 1990), the first to reach international master status; and `Deep Blue` (Campbell et al., 2002; Hsu, 2004), which defeated world champion Garry Kasparov in a 1997 exhibition match. `Deep Blue` ran `alpha–beta` search at over 100 million positions per second, and could generate singular extensions to occasionally reach a depth of 40 ply.

### Modern Chess Engines

The top chess programs today (e.g., `STOCKFISH`, `KOMODO`, `HOUDINI`) far exceed any human player. These programs have reduced the effective branching factor to less than 3 (compared with the actual branching factor of about 35), searching to about 20 ply at a speed of about a million nodes per second on a standard 1-core computer. They use pruning techniques such as the `null move` heuristic, which generates a good lower bound on the value of a position, using a shallow search in which the opponent gets to move twice at the beginning. Also important is `futility pruning`, which helps decide in advance which moves will cause a beta cutoff in the successor nodes. `SUNFISH` is a simplified chess program for teaching purposes; the core is less than 200 lines of Python.

`null move`
`futility pruning`

### Retrograde Analysis and Endgame Tablebases

The idea of retrograde analysis for computing endgame tables is due to Bellman (1965). Using this idea, Ken Thompson (1986, 1996) and Lewis Stiller (1992, 1996) solved all chess endgames with up to five pieces. Stiller discovered one case where a forced mate existed but required 262 moves; this caused some consternation because the rules of chess require a capture or pawn move to occur within 50 moves, or else a draw is declared. In 2012 Vladimir Makhnychev and Victor Zakharov compiled the Lomonosov Endgame Tablebase, which solved all endgame positions with up to seven pieces—some require over 500 moves without a capture. The 7-piece table consumes 140 terabytes; an 8-piece table would be 100 times larger.

### AlphaZero vs Stockfish

In 2017, `ALPHAZERO` (Silver et al., 2018) defeated `STOCKFISH` (the 2017 `TCEC` computer chess champion) in a 1000-game trial, with 155 wins and 6 losses. Additional matches also resulted in decisive wins for `ALPHAZERO`, even when it was given only 1/10th the time allotted to `STOCKFISH`.

Grandmaster Larry Kaufman was surprised at the sucess of this Monte Carlo program and noted, “It may well be that the current dominance of minimax chess engines may be at an end, but it’s too soon to say so.” Garry Kasparov commented “It’s a remarkable achievement, even if we should have expected it after `ALPHAGO`. It approaches the Type B human-like approach to machine chess dreamt of by Claude Shannon and Alan Turing instead of brute force.” He went on to predict “Chess has been shaken to its roots by `ALPHAZERO`, but this is only a tiny example of what is to come. Hidebound disciplines like education and medicine will also be shaken” (Sadler and Regan, 2019).

## Checkers

Checkers was the first of the classic games played by a computer (Strachey, 1952). Arthur Samuel (1959, 1967) developed a checkers program that learned its own evaluation function through self-play using a form of reinforcement learning. It is quite an achievement that Samuel was able to create a program that played better than he did, on an IBM 704 computer with only 10,000 words of memory and a 0.000001 GHz processor. `MENACE`—the Machine Educable Noughts And Crosses Engine (Michie, 1963)—also used reinforcement learning to become competent at tic-tac-toe. Its processor was even slower: a collection of 304 matchboxes holding colored beads to represent the best learned move in each position.

In 1992, Jonathan Schaeffer’s `CHINOOK` checkers program challenged the legendary Marion Tinsley, who had been world champion for over 20 years. Tinsley won the match, but lost two games—the fourth and fifth losses in his entire career. After Tinsley retired for health reasons, `CHINOOK` took the crown. The saga was chronicled by Schaeffer (2008).

In 2007 Schaeffer and his team “solved” checkers (Schaeffer et al., 2007): the game is a draw with perfect play. Richard Bellman (1965) had predicted this: “In checkers, the number of possible moves in any given situation is so small that we can confidently expect a complete digital computer solution to the problem of optimal play in this game.” Bellman did not anticipate the scale of the effort: the endgame table for 10 pieces has 39 trillion entries. Given this table, it took 18 CPU-years of `alpha–beta` search to solve the game.

## Go

I. J. Good, who was taught the Game of Go by Alan Turing, wrote (1965a) “ I think it will be even more difficult to programme a computer to play a reasonable game of Go than of chess.” He was right: through 2015, Go programs played only at an amateur level. The early literature is summarized by Bouzy and Cazenave (2001) and Müller (2002).

Visual pattern recognition was proposed as a promising technique for Go by Zobrist (1970), while Schraudolph et al. (1994) analyzed the use of reinforcement learning, Lubberts and Miikkulainen (2001) recommended neural networks, and Brügmann (1993) introduced Monte Carlo tree search to Go. `ALPHAGO` (Silver et al., 2016) put those four ideas together to defeat top-ranked professionals Lee Sedol (by a score of 4–1 in 2015) and Ke Jie (by 3–0 in 2016).

Ke Jie remarked “After humanity spent thousands of years improving our tactics, computers tell us that humans are completely wrong. I would go as far as to say not a single human has touched the edge of the truth of Go.” Lee Sedol retired from Go, lamenting, “Even if I became the number one, there is an entity that cannot be defeated.”
