# # Practical Applications of Scatter Plots and Correlation Analysis

# ## Healthcare Analytics

Scatter plots and correlation analysis can reveal relationships between various health metrics, such as the correlation between exercise frequency and cholesterol levels.

```
use plotters::prelude::*;

fn main() -> Result<(), Box<dyn std::error::Error>> {
    let drawing_area = BitMapBackend::new("exercise_cholesterol_scatter.png",
        (800, 600)).into_drawing_area();
    drawing_area.fill(&WHITE)?;

    let data = vec![
        (30, 200), (40, 195), (50, 180), (60, 170),
        (70, 160), (80, 150), (90, 140), (100, 130),
        (110, 120), (120, 110)
    ];

    let mut chart = ChartBuilder::on(&drawing_area)
        .caption("Exercise Frequency vs Cholesterol Levels", ("sans-serif",
        50).into_font())
        .margin(5)
        .x_label_area_size(30)
        .y_label_area_size(30)
        .build_cartesian_2d(0..130, 100..210)?;

    chart.configure_mesh().draw()?;

    chart.draw_series(
        data.iter().map(|(x, y)| {
            Circle::new((*x, *y), 5, GREEN.filled())
        })
    )?;
}
```