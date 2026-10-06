# Searching Gene and Protein Sequences for Domains and Motifs

| HBA HUMAN | VHLTPEEKSAVSAALAHGKHKVVEALVKAHYFRGSAHHGTVGLDSAHKGAEVAAALALFDLERAEH | 110 |
| HBA MOUSE | VHLTPEEKSAVSAALAHGKHKVVEALVKAHYFRGSAHHGTVGLDSAHKGAEVAAALALFDLERAEH | 110 |
| HZ CAPHI | VHLTPEEKSAVSAALAHGKHKVVEALVKAHYFRGSAHHGTVGLDSAHKGAEVAAALALFDLERAEH | 110 |
| consensus | | * : * * * * * * * * * * * * * * * |

| HBA HUMAN | TAHGMPPAHSAQVKTRHKGAEEGAHGAALGAEGAVHKDLVFTL | 142 |
| HBA MOUSE | TAHGMPPAHSAQVKTRHKGAEEGAHGAALGAEGAVHKDLVFTL | 142 |
| HZ CAPHI | TAHGMPPAHSAQVKTRHKGAEEGAHGAALGAEGAVHKDLVFTL | 142 |
| consensus | | * : * * * * * * * * * * * * * * * |

+   - non-conserved
- >50% conserved

Figure 8.4 – A full-length alignment

In *step 4*, we use the second positional argument of *aaPrettyPrint (* to restrict the view between positions 10 and 30, which results in the output shown in *Figure 8.5*.

![](bbox=[0.268, 0.345, 0.732, 0.463])

Figure 8.5 – A zoomed-in alignment

The alignment shown here is more than what can be rendered in this book, but these figures should have given you an idea. You should see more when you run the code on your computer.

# There’s more...

A tree visualization of sequence similarity is often useful at this stage. We can generate one of these with the ape and seqinr packages. We can convert our alignment object into a seqinr distance object that describes the sequence distances, and from that, use ape to create a simple neighborjoining tree that we can plot. This looks as follows:

# Phylogenetic Tree of HBA Sequences

![](bbox=[0.235, 0.743, 0.764, 0.863])

Figure 8.6 – A tree of the alignment