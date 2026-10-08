project's main python file:

```
# -*- coding: utf-8 -*-
import pygal
#create a new line chart.
line = pygal.Line()
line.title = 'Website hits in the past 2 years' #set chart title
line.x_labels = map(str, range(2012, 2014)) #set the x-axis labels
line.add('Page views', [None, 0, 12, 32, 72, 148]) #set values.
line.render_to_file('linechart.svg') #set filename.
```

The screenshot demonstrates a basic pygal line chart output:

![](bbox=[0.125, 0.363, 0.617, 0.658])

Inside your main project file where you executed your script, you should see the linechart.SVG file created. Open this file, and your char will look like the above screenshot. To identify the file, open the directory your project is in and search the linechart.svg file. Keep in mind that you can hover over the dots and acquire the values of every marker in the chart. These are some of the properties that come prebuilt inside the pygal library.
You will also notice that the timeline of the chars begins from 0.0 in 2013. If you look at the line.add() statement; the first parameter is None. This creates a spacer within the chart to push the chart data out rather than force the chart