```
fn main() -> Result<(), Box<dyn std::error::Error>> {
let drawing_area = BitMapBackend::new("bar_chart.png", (800,
600)).into_drawing_area();
drawing_area.fill(&WHITE)?;
let data = vec![("Jan", 30), ("Feb", 40), ("Mar", 60), ("Apr", 70), ("May", 80)];
let mut chart = ChartBuilder::on(&drawing_area)
.caption("Monthly Sales", ("sans-serif", 50).into_font())
.margin(5)
.x_label_area_size(30)
.y_label_area_size(30)
.build_cartesian_2d(0.5, 0..100)?;
chart.configure_mesh().draw()?;
chart.draw_series(
data.iter().enumerate().map(|(i, &(month, sales))| {
Rectangle::new(
[(i, 0), (i + 1, sales)],
RED.filled(),
)
.label(month)
.legend(move |(x, y)| Rectangle::new([(x - 5, y - 5), (x + 5, y + 5)],
RED.filled()))
})
)?
.label("Sales")
.legend(|(x, y)| Rectangle::new([(x - 5, y - 5), (x + 5, y + 5)], RED.filled()));
chart.configure_series_labels().draw()?;
Ok(())
}
...
```

This script generates a bar graph showing monthly sales. The data is represented by a vector of tuples, with each tuple containing a