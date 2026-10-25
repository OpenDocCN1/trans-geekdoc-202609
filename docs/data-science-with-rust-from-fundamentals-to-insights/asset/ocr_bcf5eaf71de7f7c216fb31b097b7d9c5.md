# Creating Scatter Plots

Scatter plots plot individual data points on a two-dimensional graph, with one variable on the x-axis and the other on the y-axis.

# Example: Creating a Scatter Plot

```
```rust use plotters::prelude::*;

fn main() -> Result<(), Box<dyn std::error::Error>> {
    let drawing_area = BitMapBackend::new("scatter_plot.png", (800,
600)).into_drawing_area();
    drawing_area.fill(&WHITE)?;

    let data = vec![
        (1.0, 2.0), (2.0, 3.5), (3.0, 4.0), (4.0, 4.5),
        (5.0, 5.5), (6.0, 7.0), (7.0, 7.5), (8.0, 9.0),
        (9.0, 9.5), (10.0, 10.5)
    ];

    let mut chart = ChartBuilder::on(&drawing_area)
        .caption("Scatter Plot Example", ("sans-serif", 50).into_font())
        .margin(5)
        .x_label_area_size(30)
        .y_label_area_size(30)
        .build_cartesian_2d(0.0..12.0, 0.0..12.0)?;

    chart.configure_mesh().draw()?;

    chart.draw_series(
        data.iter().map(|(x, y)| {
            Circle::new((*x, *y), 5, BLUE.filled())
        })
    )?;

    Ok(())
}
```
```