# 3.4 Data cube computation

Data warehouses contain huge volumes of data. OLAP servers demand that decision support queries be answered in the order of seconds. Data cubes are the core of data warehouses. Therefore, it is crucial for data warehouse systems to support highly efficient dat cube computation, access, and query processing. In this section, we present an overview of the ideas behind data cube computation. Section 3.4.1 introduces the basic terminology. Section 3.4.2 discusses various ideas in fully or partially materializing a data cube. Section 3.4.3 explains how data cubes may be stored using various architectures. Section 3.4.4 overviews the general strategies frequently used in data cube computation. The detailed algorithms for data cube computation will be introduced in Section 3.5.

# 3.4.1 Terminology of data cube computation

One approach to cube computation is to compute aggregates over all subsets of the dimensions specified by a user. This can require excessive storage space, especially for large numbers of dimensions. To discuss the details about data cube computation and analysis, we need some terminology.

Fig. 3.18 shows a 3-D data cube for three dimensions, A, B, and C, and an aggregate measure, M. Hereafter in this chapter, we always use the term *data cube* to refer to a lattice of cuboids rather than an individual cuboid. A tuple in a cube is also called a **cell**, which represents a point in the data cube space. A cell in the base cuboid is a **base cell**. A cell from a nonbase cuboid is an **aggregate cell**. An aggregate cell aggregates over one or more dimensions, where each aggregated dimension is indicated by a * in the cell notation. Suppose we have an *n*-dimensional data cube. Let $a = (a_1, a_2, ..., a_n, measures)$

![](bbox=[0.38, 0.68, 0.62, 0.85])

**FIGURE 3.18**
Lattice of cuboids making up a 3-D data cube with the dimensions A, B, and C for some aggregate measure, M.