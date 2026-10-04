# Extended Data Table 1 | Features of MUNIS and competing predictive models

| Model | Positives | Decoys | Deep Learning | Flanking residues | Protein language model |
| MixMHCpred 2.2 | Mass spectrometry | Human | No | No | No |
| NetMHCpan 4.1 | Mass spectrometry + Binding affinity | Uniprot | No | No | No |
| MHCflurry 2.0 | Mass spectrometry + Binding affinity | Parent protein | No | Optional | No |
| TransPHLA | Mass spectrometry + Binding affinity | Parent protein | Yes | No | No |
| BigMHC - EL | Mass spectrometry | Random | Yes | No | No |
| BigMHC - IM | Immunogenic epitopes | Human | Yes | No | No |
| Prime 2.0 | Immunogenic epitopes | Human | No | No | No |
| MUNIS | Mass spectrometry | SwissProt | Yes | Optional | Yes |

Table showing the the differences between MUNIS and other models. Models in the literature differ based on several factors, including the sampling of negatives, model architecture and the use of flanking residues.