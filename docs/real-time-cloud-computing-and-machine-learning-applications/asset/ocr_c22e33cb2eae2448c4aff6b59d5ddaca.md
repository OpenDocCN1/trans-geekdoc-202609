# Data Capture and Client Architecture for a Cloud-Based Real-Time ... 653

# 6.4.4.3. The MainFrame Constructor

When the application is first started, the MainFrame () constructor is called which performs the following tasks:

+   - Initialises the Swing components using the auto-generated code in the initComponents() method.
- Creates a Chart Panel and adds it to the current JFrame.

The code for the constructor is given in Listing 6.25.

# Listing 6.25. MainFrame Constructor

```
public MainFrame() {
  //initialize the GUI with the auto-generated code
  initComponents();
  /* Dynamically adding the JFreeChart to the JFrame*/
  //creates a new chart createXYLineChart(String title, String xAxisLabel, String
yAxisLabel, XYDataset dataset)
  //Represents a collection of XYSeries objects that can be used as a dataset
  // XYSeriesCollection dataset from JFreeChart library
XYSeriesCollection dataset = new XYSeriesCollection(xy_series);
chart = ChartFactory.createXYLineChart("Current Weather Readings", "End", dataset);
  //A Swing component for displaying a JFreeChart library
  //ChartPanel Object from JFreeChart library
  final ChartPanel chartPanel = new ChartPanel(chart);
  //Sets the preferred size of this component.
  chartPanel.setPreferredSize(new Dimension(550, 440));
  //Enables mouse wheel support for the panel.
  chartPanel.setMouseEnabled(true);
  //Create a new JPanel as the parent of the ChartPanel
  JPanel graphPanel = new JPanel();
  //Sets the bound of the JPanel on the JFrame
  graphPanel.setBounds(265, 40, 550, 550);
  //add the chart panel to the JPanels
  graphPanel.add(chartPanel);
  //add the JPanel to the JFrame
  add(graphPanel);
  //update the JFrame with the added JPanel
  revalidate();
  /*End */
```