| Prefix | Projected Database | Sequential Patterns |
| :--- | :--- | :--- |
| `<a>` | `((abc)(ac)d(cf)), ((_d)(bc)(ae)), ((_b)(df)cb), ((_f)cbc)` | `<a>`, `<aa>`, `<ab>`, `<a(bc)>`, `<a(bc)a>`, `<aba>`, `<abc>`, `<(ab)>`, `<(ab)c>`, `<(ab)d>`, `<(ab)f>`, `<(ab)dc>`, `<ac>`, `<aca>`, `<acb>`, `<acc>`, `<ad>`, `<adc>`, `<af>` |
| `<b>` | `<(_c)(ac)d(cf)>, <(_c)(ae)>, <(df)cb>, <c>` | `<b>`, `<ba>`, `<bc>`, `<(bc)>`, `<(bc)a>`, `<bd>`, `<bdc>`, `<bf>` |
| `<c>` | `<(ac)d(cf)>, <(bc)(ae)>, <b>, <bc>` | `<c>`, `<ca>`, `<cb>`, `<cc>` |
| `<d>` | `<(cf)>, <(c)(bc)(ae)>, <(_f)cb>` | `<d>`, `<db>`, `<dc>`, `<dcb>` |
| `<e>` | `<(_f)(ab)(df)cb>, <(af)cbc>` | `<e>`, `<ea>`, `<eab>`, `<eac>`, `<eacb>`, `<eb>`, `<ebc>`, `<ec>`, `<ecb>`, `<ef>`, `<efb>`, `<efc>`, `<efcb>` |
| `<f>` | `<(ab)(df)cb>, <cbc>` | `<f>`, `<fb>`, `<fbc>`, `<fc>`, `<fcb>` |

Recursively, all sequential patterns with prefix `<a>` can be partitioned into six subsets: (1) those prefixed with `<aa>`, (2) those with `<ab>`, ..., and finally, (6) those with `<af>`. These subsets can be mined by constructing respective projected databases and mining each recursively as follows.

+   i. The `<aa>`-projected database consists of two nonempty (suffix) subsequences prefixed with `<aa>`: `{(_bc)(ac)d(cf)>, {(_e)}`. Since there is no hope of generating any frequent subsequence from this projected database, the processing of the `<aa>`-projected database terminates.

+   ii. The `<ab>`-projected database consists of three suffix sequences: `<(_c)(ac)d(cf)>`, `<(_c)a>`, and `<c>`. Recursively mining the `<ab>`-projected database returns four sequential patterns: `<(_c)>`, `<(_c)a>`, `<a>`, and `<c>` (i.e., `<a(bc)>`, `<a(bc)a>`, `<aba>`, and `<abc>`.) They form the complete set of sequential patterns prefixed with `<ab>`.

+   iii. The `<ab>`)-projected database contains only two sequences: `<(_c)(ac) d(cf)>` and `<(df)cb>`, which leads to the finding of the following sequential patterns prefixed with `<(ab)>`: `<c>`, `<d>`, `<f>`, and `<dc>`.

+   iv. The `<ac>`-, `<ad>`- and `<af>`- projected databases can be constructed and recursively mined in a similar manner. The sequential patterns found are shown in Table 5.5.

+   b. Find sequential patterns with prefix `<b>`, `<c>`, `<d>`, `<e>` and `<f>`, respectively. This can be done by constructing the `<(b)>-`, `<(c)>-`, `<(e)>-`, and `<(f)>-`projected databases and mining them. The projected databases and the sequential patterns found are also shown in Table 5.5.

+   4. The set of sequential patterns is the collection of patterns found in the above recursive mining process.

The method described above generates no candidate sequences in the mining process. However, it may generate many projected databases, one for each frequent prefix-subsequence. Forming a large number of projected databases recursively may become the major cost of the method if such databases have to be generated physically. An important optimization technique is **pseudo-projection**, as shown in Fig. 5.9. For example, for a sequence `<a(abc)(ac)d(cf)>`, `<a>`’s projection will generate a projected subsequence `<(abc)(ac)d(cf)>` (i.e., `<a>`’s suffix), and a subsequent projection on `<b>` generates an `<ab>`’s projected sequence `<(_c)(ac)d(cf)>`. Such physical projection may take a lot of time and space to copy and store the projected subsequences, which contains a lot of redundancy. The pseudo-projection method registers the index (or identifier) of the corresponding sequence and the starting position of the