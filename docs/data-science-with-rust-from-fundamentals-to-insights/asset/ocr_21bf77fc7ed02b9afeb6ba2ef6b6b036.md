```
let trend: Vec<(NaiveDate, f64)> = data.iter().map(|(date, &value)| (*date,
value * 0.8)).collect();
let seasonality: Vec<(NaiveDate, f64)> = data.iter().map(|(date, &value)|
(*date, value * 0.2)).collect();

let mut chart = ChartBuilder::on(&drawing_area)
    .caption("Trend Decomposition", ("sans-serif", 50).into_font())
    .margin(5)
    .x_label_area_size(40)
    .y_label_area_size(40)
    .build_cartesian_2d(
        start_date..start_date + Duration::days(364),
        0.0..100.0,
    )?;

chart.configure_mesh().draw()?;
chart.draw_series(LineSeries::new(data.clone(), &BLUE))?;
chart.draw_series(LineSeries::new(trend, &GREEN))?;
chart.draw_series(LineSeries::new(seasonality, &RED))?;

Ok(())
}
```

This code produces a plot with the original data, trend, and seasonality components shown in blue, green, and red, respectively. It helps in visualizing how each component contributes to the overall pattern.

# Interactive Time Series Visualizations

Creating interactive plots allows users to explore data dynamically. While Rust's capabilities for interactive plots are growing, integrating with web technologies like WebAssembly can enhance interactivity.