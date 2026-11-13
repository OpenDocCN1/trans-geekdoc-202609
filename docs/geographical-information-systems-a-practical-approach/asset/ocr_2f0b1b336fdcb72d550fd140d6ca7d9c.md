# Box 9.1 A Cellular Automata Forest Fire Model in ArcGIS

![](bbox=[0.755, 0.102, 0.825, 0.158])

This example illustrates a CA model simulating how forest fires spread after trees ignite randomly by lightning in ArcGIS. The CA model is from Drossel and Schwabl (1992), which is defined by four transition rules that are applied simultaneously:

+   1. A burning tree becomes an empty cell.
+   2. A tree ignites if at least one neighbour is burning.
+   3. A tree becomes a burning tree with probability f of lightning strike even if no neighbour is burning.
+   4. A tree grows at an empty cell with probability p.

It should be noted that these rules are not a realistic representation of how real forests behave. The example seeks to demonstrate how a CA model is executed in ArcGIS, not how a forest fire model is created.

Spatial modelling in ArcGIS can be conducted with ModelBuilder or through scripting. ModelBuilder is a diagramming tool in ArcGIS for creating and executing spatial models using sequences of spatial analysis tools, feeding the output of one tool into another as input. It is also a useful tool for constructing and executing workflows represented using spatial influence diagrams discussed in Section 1.4. In principle, ModelBuilder can be used for dynamic modelling via an iterative process. However, it is far more efficient to use a scripting language for dynamic modelling. The major scripting language for model building and implementation in the current version of ArcGIS is Python, which is a free, cross-platform and open-source programming language. In this example, the CA model was written in Python, as shown in Table 9.4. Comments (starting with the hash character #) are provided to help understand the Python script. To learn Python programming in ArcGIS, consult Zandbergen (2020).

# Table 9.4 Python script for the CA forest fire model in Box 9.1

|   |   |
|---|---|
| 1 | import arcpy |
| 2 | from arcpy import env |
| 3 | from arcpy.sa import * |