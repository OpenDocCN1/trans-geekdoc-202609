The merge mask should look like the illustration in [figure 16.8](#).

![](bbox=[0.279, 0.132, 0.714, 0.426])

**FIGURE 16.8**  
The resulting *Merged* layer.

# 16.2.1.3  Grid generation

In this section, we will generate the grid that will be used to extract the patches in the images. As in section 12.1.3.1, we use QGIS to generate a vector layer of polygons that represent the patch layout, aligned on the pixel positions of the images. Since our model needs 64 × 64 patches at inputs and the pixels have 10-m spacing, we will generate a grid tiled with 640-meter-sized squares. From the menu, click on **Vector > Research tools > Create grid** as shown in [figure 16.9](#).

![](bbox=[0.239, 0.68, 0.748, 0.827])

**FIGURE 16.9**  
Create a vector grid.