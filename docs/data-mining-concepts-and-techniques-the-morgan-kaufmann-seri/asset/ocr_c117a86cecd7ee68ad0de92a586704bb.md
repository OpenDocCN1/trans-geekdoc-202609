![](bbox=[0.16, 0.12, 0.82, 0.71])

**FIGURE 3.20**
A 3-D array for the dimensions A, B, and C, organized into 64 chunks. Each chunk is small enough to fit into the memory available for cube computation. The *'s indicate the chunks from 1 to 13 that have been aggregated so far in the process.

Let's look at how the multiway array aggregation technique is used in this computation. There are many possible orderings with which chunks can be read into memory for use in cube computation. Consider the ordering labeled from 1 to 64, shown in Fig. 3.20. Suppose we want to compute the $b_0c_0$ chunk of the $BC$ cuboid. We allocate space for this chunk in *chunk memory*. By scanning $ABC$ chunks