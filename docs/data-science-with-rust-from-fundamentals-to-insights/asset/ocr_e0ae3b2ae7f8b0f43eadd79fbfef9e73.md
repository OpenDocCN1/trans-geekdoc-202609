```
let theoretical_quantiles = (1..=data.len())
.map(|i| normal_dist.sample(&mut rand::thread_rng()))
.collect::<Vec<f64>>();

let mut chart = ChartBuilder::on(&drawing_area)
.caption("QQ Plot", ("sans-serif", 50).into_font())
.margin(5)
.x_label_area_size(30)
.y_label_area_size(30)
.build_cartesian_2d(-3.0..3.0, -3.0..3.0)?;

chart.configure_mesh().draw()?;

chart.draw_series(data.iter().zip(theoretical_quantiles.iter()).map(|(&data, &theor)| {
Circle::new((data, theor), 5, RED.filled())
}));?;

Ok(())
}
...
```

This QQ plot compares the sample data against a normal distribution. The points should lie approximately along the line ( y = x ) if the data distribution is similar to the theoretical distribution.

# # Practical Applications of Distribution Visualization

# ## Healthcare Analytics

Understanding patient data distributions is vital for diagnosing, treating, and researching diseases. Visualizations can reveal trends and anomalies in patient demographics, treatment outcomes, and other critical metrics.

```
...rust use plotters::prelude::*;
```