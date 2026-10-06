+   2. Set up a function to make a blast database:

```
make_blastdb <- function(fasta, blast_path) {
  system(paste0(blast_path, "makeblastdb -in ", fasta,
"input_type fasta -dbtype prot -hash_index")
))
}
```

}

+   3. Set up a function to run blastp:

```
run_blast <- function(query, db, outfile, blast_path,
evaluate="1E-5", max_target_seqs=1000) {

  system(paste0(
    blast_path,
    'blastp -db ',
    db,
    '-query ',
    query,
    '-evaluate ',
    evaluate,
    '-max_target_seqs ',
    max_target_seqs,
    '-out ',
    outfile,
    '-outfmt "6',
    ' gseqid ssdid pident nident length mismatch gapen gaps\npositive ppos qstart gend qlen qovs ccovhp sstart send len\nvalue bitscore score'
  ))
)
}
```

}

+   4. Run blastp in the first direction:

```
sceres <- fs::path_package(
"extdata",
"sceres_100.fa",
package = "rbioinfookbook"
)

spombe <- fs::path_package(
"extdata",
"spombe_100.fa",
package = "rbioinfookbook"
)
```