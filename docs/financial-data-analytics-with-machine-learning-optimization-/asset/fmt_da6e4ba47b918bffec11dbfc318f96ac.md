
where `ε′ = ε + (1 + oₙ(1))/n + oₙ(1) log₂ |X|`. Therefore,

`l(1/n l(x⁽ⁿ⁾)) ≤ H(x) + ε.`

By using similar arguments or otherwise, we can easily show that `liminfₙ→∞ E(1/n l(x⁽ⁿ⁾)) ≥ H(x)`, and hence `limₙ→∞ l(1/n l(x⁽ⁿ⁾)) = H(x)`; as a result, one only needs `nH(x)` bits on average to code sequences in `Xⁿ` when `n` is sufficiently large.

### 13.A.2 Solving Wordle with Entropy

Wordle is a web‐based word game developed by Josh Wardle, released regularly by the New York Times as a word puzzle for its readers. Players have six attempts to guess a five‐letter word, with feedback given for each guess: each guessed letter is marked as either green, yellow or gray. Green indicates that the corresponding letter appears in the correct position of the target word; yellow color indicates that the corresponding letter is in the target word but not positioned correctly; while gray color means that the corresponding letter is not in the target word. As a special rule, in the event of multiple copies of a specific letter in the guess, let say `m` of them, appear in a guess, such as the A's and R's in RADAR (where `m` = 2 for both letters) or the M's in MUMMY (where `m` = 3), those in the correct positions, let say `m₀` of them, will first be colored as green, then the leftmost `(m - m₀)₊` among the remaining copies will be colored yellow, while the rest of them are displayed as gray; see [Figure 13.19](#c13.xhtml#c13-fig-0019) for an illustration, where readers can try to recover the color of each position in every attempt based on the aforementioned rules
