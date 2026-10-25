```
.y_label_area_size(30)
.build_cartesian_2d(0..10, 0..100)?;

chart.configure_mesh().draw()?;

chart.draw_series(LineSeries::new(
    (0..10).map(|x| (x, x * x)),
    &RED,
))?;

Ok(())
}
...
```

+   1. Create Bar Charts:
+   2. Write Rust code to create a bar chart: ... rust use
+   plotters::prelude::*;

```
fn main() -> Result<(), Box<dyn std::error::Error>> {
let root_area = BitMapBackend::new("bar_chart.png", (640,
480)).into_drawing_area();
root_area.fill(&WHITE)?;

let mut chart = ChartBuilder::on(&root_area)
.caption("Bar Chart", ("sans-serif", 50).into_font())
.margin(5)
.x_label_area_size(30)
.y_label_area_size(30)
.build_cartesian_2d(0..10, 0..100)?;

chart.configure_mesh().draw()?;

chart.draw_series((0..10).map(|x| {
    Rectangle::new([(x, 0), (x + 1, x * 10)], RED.filled())
}))?;

Ok(())
}
...
```