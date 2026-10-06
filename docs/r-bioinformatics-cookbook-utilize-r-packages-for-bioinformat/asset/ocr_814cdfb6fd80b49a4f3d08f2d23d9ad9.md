# Finding Genetic Variants with HTS Data

```
return(max(width (orfs)))
}
```

+   5. Run the function on 10 simulated genomes:

```
random_lengths <- unlist(lapply(1:10, get_longest_orf_in_random_ngenome, length = seq_length, probs = probs, bases = bases)
```

+   6. Get the length of the longest random ORF:

```
longest_random_orf <- max(random_lengths)
```

+   7. Keep only predicted ORFs longer than the random ORF:

```
keep <- width(predicted_orfs) > longest_random_orf
orfs_to_keep <- predicted_orfs[keep]
orfs_to_keep
```

And with that, we predict ORFs from long reference sequences.

# How it works...

The first part of this recipe is when we predict ORFs. Initially, we load the DNA sequence as a DNAString object using readDNAStringSet() from Biostrings. The predORF () function from systemPipe uses this object as input and predicts ORFs according to the options set. In the following code block, we are returning all ORFs on both strands.

This will result in the following output:

```
## GRanges object with 2501 ranges and 2 metadata columns:
## segments strand | subject_inframe2end
## <Rle> <GRanges> <Rle> <integer> <numeric>
## 1 chloroplast 86762-93558 + | 1 2
## 1162 chloroplast 2056-2532 + | 1 3
## 2 chloroplast 72371-73897 + | 2 2
## 1163 chloroplast 77901-78362 - | 2 1
## 3 chloroplast 54937-56397 + | 3 1
```

We have received a GRanges object in return, 2501 ORFs. This is far too many, so we need to filter them; in particular, we can work out which ORFs are caused by change in sequence. To do this, we need to do a little simulation: that's happens in the next section of code. To estimate the length that random ORFs can reach, we're going to generate a series of random genomes of a length equal to our input sequence and with the same base proportion and see what the longest ORF that can be predicted. We do a few iterations of it to get an idea of what the longest ORF occurring by chance could be. This length serves as a cut-off in us to reject the predicted ORFs in the real sequence.