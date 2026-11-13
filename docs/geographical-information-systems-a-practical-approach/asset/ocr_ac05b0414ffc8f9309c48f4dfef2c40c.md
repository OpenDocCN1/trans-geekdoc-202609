```
(continued)
PARAMETER["Central_Meridian", 24.0],
PARAMETER["Standard_Parallel_1", -18.0],
PARAMETER["Standard_Parallel_2", -32.0],
PARAMETER["Latitude_Of_Origin", 0.0],
UNIT["Meter", 1.0]
```

+   - The .sbn and .sbx files. These are two spatial index files, containing the spatial index of the geographical features. The .sbn (spatial bin) file divides the area the data covers into rectangular regions (bins). Each bin contains the record numbers of the features in the .shp file that fall in its area. The .sbx (spatial bin index) file contains rows, each row storing the record number and the length in bytes of the corresponding bin record in the .sbn file.
+   - The .shp.xml file. This is the metadata file, containing information about the basic characteristics of the data layer in XML format, which may include the identification, the extent, the quality, the georeference and the custodian of the dataset.

![](bbox=[0.225, 0.485, 0.835, 0.695])

| Arc | From-node | To-node |
|---|---|---|
| 1 | 1 | 2 |
| 2 | 3 | 2 |
| 3 | 2 | 4 |
| 4 | 4 | 6 |
| 5 | 4 | 5 |

| Arc | (x, y) coordinate pairs |
|---|---|
| 1 | (20, 50) (175, 110) (120, 226) (205, 330) |
| 2 | (21, 725) (170, 590) (105, 475) (205, 330) |
| 3 | (205, 330) (302, 290) (350, 200) |
| 4 | (350, 200) (480, 220) (675, 89) |
| 5 | (350, 200) (400, 430) (370, 560) (523, 651) (624, 550) (700, 630) |