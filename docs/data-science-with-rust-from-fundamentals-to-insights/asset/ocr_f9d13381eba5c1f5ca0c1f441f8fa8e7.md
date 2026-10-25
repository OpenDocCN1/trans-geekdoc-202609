# # Types of Probability

There are several types of probability, each serving different purposes in various applications.

+   1. **Theoretical Probability**: Based on known possible outcomes. For example, rolling a fair six-sided die.
+   2. **Experimental Probability**: Based on actual experiments and observed outcomes. For instance, flipping a coin 100 times and observing the results.
+   3. **Subjective Probability**: Based on personal judgment or experience, rather than exact calculations.

To illustrate experimental probability in Rust, consider a simple dice roll simulation:

```
```rust
use rand::Rng;

fn main() {
    let mut rng = rand::thread_rng();
    let mut counts = [0; 6];

    for _ in 0..1000 {
        let roll: usize = rng.gen_range(0..6);
        counts[roll] += 1;
    }

    for (i, count) in counts.iter().enumerate() {
        println!("P({}): {}", i + 1, *count as f64 / 1000.0);
    }
}
```
```