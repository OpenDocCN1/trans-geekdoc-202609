```
```rust
impl GradientBoostingRegressor {
    fn new(learning_rate: f64, n_estimators: usize) -> Self {
        GradientBoostingRegressor {
            learning_rate,
            n_estimators,
            base_learners: Vec::new(),
        }
    }

    fn fit(&mut self, x: &Array1<f64>, y: &Array1<f64>) {
        let mut predictions = Array1::zeros(y.len());
        for _ in 0..self.n_estimators {
            let residuals = y - &predictions;
            let new_learner = self.train_base_learner(x, &residuals);
            predictions = predictions + self.learning_rate * &new_learner;
            self.base_learners.push(new_learner);
        }
    }

    fn train_base_learner(&self, x: &Array1<f64>, residuals: &Array1<f64>) ->
    Array1<f64> {
        let mut rng = rand::thread_rng();
        residuals.mapv(|_| rng.gen_range(-1.0..1.0))
    }

    fn predict(&self, x: &Array1<f64>) -> Array1<f64> {
        let mut predictions = Array1::zeros(x.len());
        for learner in &self.base_learners {
            predictions = predictions + self.learning_rate * learner;
        }
        predictions
    }
}

fn main() {
    let x = Array1::linspace(0., 10., 100);
    let y = x.mapv(|x| 2.0 * x + 3.0 + rand::thread_rng().gen_range(-1.0..1.0));
```
```