# Practical 3.9 See the Support Material

![](bbox=[0.76, 0.1, 0.85, 0.15])

In this practical, you are going to learn topological editing with shared geometry in ArcGIS Pro or QGIS.

# 3.4.3 Editing with Topology Rules

Beyond editing shared geometry, some GIS systems support the use of **topology rules** to discover and remove topologically errors in spatial data. Topology rules can be defined by the GIS system or the user. They control the acceptable topological relationships among features in a data layer (or feature class) or several data layers (or different feature classes): for example, land cover boundaries must not overlap, roads must not intersect with building footprints or address points must be properly inside property boundaries. The features are checked against the rules to identify those in violation – that is, topologically errors.

For example, the geodatabase in ArcGIS supports spatial data editing with 31 topology rules, 10 rules for polygons, 15 rules for lines and 6 rules for points. Key topology rules in geodatabase can be found in Perencsik (2004). Table 3.2 gives some examples of topology rules for polygons, lines and points. The topology rules in ArcGIS can only be built and applied to feature classes in a feature dataset based on the geodatabase data model.

Like editing features with shared geometry, editing with topology rules in a geodatabase first requires the construction of a

topology for all participating feature classes in a feature dataset. It involves specifying a cluster tolerance, topology rules and ranks. Ranks are assigned to the participating feature classes in the topology. They determine which feature classes are more likely to be moved when fixing topological errors. Edges or vertices of lower-ranking features within the cluster tolerance will be snapped to nearby edges or vertices of higher-ranking features. Edges or vertices of features of equal rank that lie within the cluster tolerance will be geometrically averaged together. Generally, lower-ranking features are known to have less-reliable or less-accurate positions. Figure 3.17 shows a set of feature classes and the associated ranks and rules that apply to those participating in a topology. Geodatabase topology is created and stored as a separate data layer, not with features, in a geodatabase.

Once a topology is built, it is validated: (1) to evaluate the features against the topology rules and identify topological errors where the rules are violated, and (2) to identify coincident features that fall within the cluster tolerance and snap them together automatically. The automatic editing of adjacent features with shared geometry in the validation process involves cracking and snapping features (Figure 3.18). In the cracking stage, new vertices are created at