data streams, ensuring that the vehicle has a comprehensive understanding of its surroundings.

```
extern crate rand;

use rand::Rng;
use std::thread;

fn main() {
    let handle_camera = thread::spawn(|| generate_camera_data());
    let handle_lidar = thread::spawn(|| generate_lidar_data());
    let handle_radar = thread::spawn(|| generate_radar_data());

    let camera_data = handle_camera.join().unwrap();
    let lidar_data = handle_lidar.join().unwrap();
    let radar_data = handle_radar.join().unwrap();

    let fused_data = fuse_sensor_data(camera_data, lidar_data, radar_data);
    println!("Fused sensor data: {:?}", fused_data);
}

fn generate_camera_data() -> Vec<f64> {
    let mut rng = rand::thread_rng();
    (0..100).map(|_| rng.gen_range(0.0..1.0)).collect()
}

fn generate_lidar_data() -> Vec<f64> {
    let mut rng = rand::thread_rng();
    (0..100).map(|_| rng.gen_range(0.0..1.0)).collect()
}

fn generate_radar_data() -> Vec<f64> {
    let mut rng = rand::thread_rng();
    (0..100).map(|_| rng.gen_range(0.0..1.0)).collect()
}

fn fuse_sensor_data(camera_data: Vec<f64>, lidar_data: Vec<f64>, radar_data: Vec<f64>) -> Vec<f64> {
    // Simplified sensor fusion logic
    camera_data.iter().zip(lidar_data.iter()).zip(radar_data.iter()).map(|((&c, &l),
```