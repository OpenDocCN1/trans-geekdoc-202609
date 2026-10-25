# CHAPTER 4: PROBABILITY AND STATISTICS

Probability is a measure of the likelihood that an event will occur. It ranges from 0 (impossible event) to 1 (certain event). The most basic form of probability is the ratio of the number of favorable outcomes to the total number of possible outcomes. This is expressed mathematically as: [ P(A) = \frac{\text{Number of favorable outcomes}}{\text{Total number of outcomes}} ]

Let's consider an example: flipping a fair coin. The probability of getting heads (favorable outcome) is: [ P(\text{Heads}) = \frac{1}{2} ]

In Rust, we can simulate this using the rand crate:

```
```rust
use rand::Rng;

fn main() {
    let mut rng = rand::thread_rng();
    let flip: bool = rng.gen_bool(0.5);
    println!("Coin flip result: {}", if flip { "Heads" } else { "Tails" });
}
```
```