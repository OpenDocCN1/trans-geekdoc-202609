# Example: Simulation of Infections in Central African Rep.

```
library(DescTools)
set.seed(240724) # seed for reproducibility
bbox_grid <- expand_grid(x = seq(from = bbox$xmin,
                                 to = bbox$xmax,
                                 length.out = 100),
                               y = seq(from = bbox$ymin,
                                 to = bbox$ymax,
                                 length.out = 100))
```

```
ctr_africa_grid_full <- data.frame(PtInPoly(bbox_grid,
                                               ctr_africa_coords))
```

```
ctr_africa_grid_full %>% head(
#    x         pip
# 1 14.45941 2.267640 0
# 2 14.45941 2.357284 0
# 3 14.45941 2.446928 0
# 4 14.45941 2.536572 0
# 5 14.45941 2.626216 0
# 6 14.45941 2.715860 0
```

Mapping the grid of points on the map of the Central African Republic, we can visualise the spatial distribution of infected locations.

```
# Window Grid
gggplot() + 
geom_sf(data = ctr_africa)+
geom_sf(data = grid, shape = ".") + 
geom_sf(data = df_sf %>% filter(presence == 1),
       aes(fill = presence),
       shape = 21, stroke = 0.3) + 
coord_sf() + 
labs(title = "Window Grid") + 
theme(legend.position = "right")
```

```
# Central Africa Grid
ggplot(data = ctr_africa_grid_full) + 
geom_point(aes(x, y, color = factor(pip)), shape = ".") + 
geom_sf(data = df_sf %>% filter(presence == 1),
       aes(fill = presence),
       shape = 21, stroke = 0.3, 
       show.legend = F) + 
coord_sf() + 
scale_color_manual(values = c("1" = "grey20", "0" = "grey")) + 
labs(title = "Grid Map",
     color = "PIP") +
theme(legend.position = "top")
```