# How it works...

In step 1, the rbioinfcookbook and Rsamtools packages are loaded, both of which provide several functionalities, such as reading BAM/SAM/CRAM files and BED files, handling BAM indices, and retrieval data from BAM files. Then, the path_path function from the fs package is used to get the path of the windows .bam file, which is a BAM file containing sequencing reads. This is part of the data that comes with the rbioinfcookbook package, and it will be used in the following steps of the analysis.

In step 2, the clusterMaker function from the bumhunter package is used to find preliminary clusters in the data. The clusterMaker function expects a vector of chromosome names (pileup_dfpos) and a maxGap parameter that defines the maximum allowed distance between two positions in the same cluster. Here, the maximum distance allowed is 100 bp. The clusterMaker function returns a vector of cluster IDs, where positions that belong to the same cluster have the same ID. Refer to the following code:

```
## clusters
## 1 2 3
## 1486 1552 1520
```

This gives us the clusters that were obtained in step 2, represented as a table showing the number of positions that belong to each cluster.

In step 3, the regionFinder function is used to find the actual bumps of enrichment in the data, based on the preliminary clusters obtained in the previous step. The regionFinder function expects a vector of counts (pileup_dfcounts), a vector of positions (pileup_dfpos), the clusters obtained from the previous step 2, and a cutoff parameter that defines the minimum allowed count for a position to be considered part of a bump. The minimum count is set to 1.

The regionFinder returns a DataFrame with cluster positions and metrics on the bump sizes: Hopefully, this has outlined how to find peaks or bumps with expression data alone.

# There’s more...

If you have multiple experiments to analyze, try the bumhunter function. This will operate over multiple data columns in a matrix and perform linear modeling to assess uncertainty about the position and existence of the replicates. It is very similar to regionFinder () in operation.