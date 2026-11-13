# Box 2.2 ESRI Grid

The grid is the native raster data format of ArcGIS. It uses the cell-by-cell or run-length encoding method to store raster data, depending on which is more efficient. A grid whose cell values are integer numbers (without a fractional or decimal component, for example, 24 and 80) is called an integer grid. Integer grids are mainly used to represent categorical or discrete data. A grid is called a floating-point grid if its cell values are floating-point numbers (with a fractional or decimal component, for example, 24.4 and 80.588). Floating-point grids are primarily used to represent continuous data. Integer grids usually have associated with them a value attribute table (VAT), while floating-point grids do not.

A VAT typically contains cell values that define a class, group or category. It contains a minimum of three fields: OID, VALUE and COUNT. Figure 2.25 illustrates a soil grid with VAT. OID is a unique, system-defined object ID for each row in the table. VALUE stores each unique cell value in the raster. COUNT represents the number of cells in the raster with the cell value in the VALUE field. For example, the first row in the VAT shows VALUE = 1 and COUNT = 7294, indicating that 7,294 cells have a value of 1, representing bedrock in the grid. Cells without measurements or actual values are assigned NoData. NoData is a special, system-defined value

![](bbox=[0.182, 0.571, 0.873, 0.843])

Figure 2.25 Grid with VAT.