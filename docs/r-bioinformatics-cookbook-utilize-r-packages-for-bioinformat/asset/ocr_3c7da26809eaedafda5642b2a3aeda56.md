Giving us a full GWAS. Note that the example data is small and that a real dataset would take a long time to run.

# How it works...

Most of the code is setup code. After loading the libraries and fixing the random number generator for reproducibility (set_seed()) in step 1, we get the VCF file of useful variants loaded.
In step 2, we extract useful information: we get a matrix of genotypes with the geno (vcf) GT call in which the row is a variant, a column is a sample, and the genotype is recorded at the intersection.
Next, we use some accessor functions to pull sample and marker names and the reference sequence (chrom) and position (pos) for each variant. In step 3, we define a translation function called convert() to "0/0" VCF-type heterozygous and homozygous annotations to those used in GWAS.
Briefly, in VCF,"0/0" means AA (homozygous), which is encoded as 1 in GWAS (); "0/1" and "1/0" are heterozygous Aa or a, and "1/1" is homozygous aa or -1 in GWAS ().
In step 4, we convert to the gt matrix and convert it into a numeric matrix. In step 5, we build a DataFrame containing the variant from the sample, marker, and sequence information created and in step 6, we combine the variant information with the genotype encodings to get the following:

```
##              marker chrom      pos NA00001 NA00002 NA00003
## 1  rs60504257   20      14370        1        0       -1
## 2  20:17330_T/A   20      17330        1        0        1
## 3  20:1230237_T/G   20     1230237        1        1        0
```

Note that the order of the columns is important. The GWAS () function expects us to have this information in the order specified here.
In step 7, we build the phenotype information. The first column must be called line but containing the sample names in the same order as the columns of the genotype matrix. The rest of the columns can be phenotype scores and have fixed effects.
This results in the following command block (the actual numbers may vary if you omit the seed() call):

```
##              line        score
## 1  NA00001   -1.2070657
## 2  NA00002    0.2772492
## 3  NA00003   1.0844412
```