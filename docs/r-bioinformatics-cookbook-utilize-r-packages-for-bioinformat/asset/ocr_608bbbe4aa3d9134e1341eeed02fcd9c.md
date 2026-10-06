# Estimating differential expression with DESeq2

| FBgn0261575 599.6725 0.292291 0.0399686 7.31301 |
| 2.61228e-13 | | | | |
| padj | | | | |
| <numeric> | | | | |
| FBgn0000003 NA | | | | |
| FBgn0000008 4.16746e-02 | | | | |
| FBgn0000014 2.21580e-111 | | | |\ |
| FBgn0000015 5.99754e-32 | | | | |
| FBgn0000017 4.79873e-09 | | | | |
| ... | | | | |
| FBgn02615671 1.00000e+00 | | | | |
| FBgn02615672 1.29821e-47 | | | | |
| FBgn02615673 2.53877e-05 | | | | |
| FBgn02615674 5.04156e-13 | | | | |
| FBgn02615675 7.62380e-13 | | | | |

With that, we've learned how to work through DESeq2 using multiple initial inputs.

# How it works…

Similar to what we covered edgeR earlier, we will go through to do this from a count matrix, not an ExpressionSet object.

# Using DESeq2 from a count matrix

In step 1, the count_dataframe DataFrame is loaded and a matrix called count_matrix is created by creating count_dataframe and setting the row names to the gene column from count_dataframe. The gene column is removed from count_dataframe.

In step 2, a character vector experiments_of_interest is created that contains the L1Larvae and L2Larvae elements. Then, a numeric vector columns_of_interest is created by finding the indices in the stage column of pheno_data that are elements of experiments_of_interest.

In step 3, a character vector stages is created by subsetting the stage column of pheno_data using columns_of_interest and converted into a factor using the as_factor() function from the forcats package. A DataFrame grouped is created with a single column stage containing the stages vector.

In step 4, a matrix counts_of_interest is created by subsetting count_matrix using columns_of_interest.