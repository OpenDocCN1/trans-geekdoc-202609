```
let mut rng = thread_rng();
let mut centroids = Array2::<f64>::random_using((k, data.ncols()),
Uniform::new(0.0, 1.0), &mut rng);
for _ in 0..max_iters {
let mut clusters = vec![Vec::<f64>::new(); k];
for row in data.genrows().into_iter() {
let distances: Vec<f64> = centroids.genrows().into_iter()
.map(|centroid| euclidean_distance(&row.to_owned(),
&centroid.to_owned()))
.collect();
let min_index = distances.iter().position(|&x| x ==
*distances.iter().min().unwrap()).unwrap();
clusters[min_index].push(row.to_owned());
}
for i in 0..k {
if !clusters[i].is_empty() {
centroids.row_mut(i).assign(&clusters[i].iter().sum::
<Array2<f64>>() / clusters[i].len() as f64);
}
}
}
centroids
}

fn euclidean_distance(a: &Array2<f64>, b: &Array2<f64>) -> f64 {
a.iter().zip(b.iter()).map(|(x1, x2)| (x1 - x2).powi(2)).sum::<f64>()
.sqrt()
}

fn main() {
let data = Array2::<f64>::from_shape_vec((5, 3), vec![
1.0, 2.0, 0.0,
2.0, 3.0, 0.0,
3.0, 4.0, 1.0,
```