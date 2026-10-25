```
let collaborative_scores = collaborative_recommendations(user_index,
user_item_matrix);

let hybrid_scores: Vec<f64> = content_scores
.iter()
.zip(collaborative_scores.iter())
.map(|(content_score, collaborative_score)| content_score +
collaborative_score)
.collect();

let mut recommendations: Vec<(usize, f64)> = hybrid_scores
.into_iter()
.enumerate()
.collect();
recommendations.sort_by(|a, b| b.1.partial_cmp(&a.1).unwrap());

recommendations.iter().map(|(index, _)| *index).collect()
}
```

```
fn main() {
let user_profile: Array1<f64> = array![0.1, 0.3, 0.5];
let item_profiles = vec![
array![0.2, 0.4, 0.6],
array![0.1, 0.3, 0.5],
array![0.5, 0.2, 0.1],
];

let user_item_matrix: Array2<f64> = array![
[5.0, 3.0, 0.0, 1.0],
[4.0, 0.0, 4.0, 1.0],
[1.0, 1.0, 0.0, 5.0],
[1.0, 0.0, 0.0, 4.0],
[0.0, 1.0, 5.0, 4.0],
];

let user_index = 0;
let recommendations = hybrid_recommendations(&user_profile, &item_profiles,
user_index, &user_item_matrix);
```