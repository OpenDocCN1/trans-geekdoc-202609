further alignment needs to make a decision, i.e., which is the best to select among these three incremental alignments.

The first incremental alignment type is to pick the first remaining residues of both sequences. This is to align $x_{m+1}$ with $y_{n+1}$. If they are included in a new alignment, the current total alignment distance is calculated based on the following formula,

```
$d(\\dots x_m|x_{m+1}, \dots y_n|y_{n+1}) = d_{mn} + \delta(x_{m+1}, y_{n+1})$   (7.7)
```

where the bar is used to separate the residues from the unaligned residues of two sequences. The residue just on the right side of the bars for a newly aligned residue. They are $x_{m+1}$ and $y_{n+1}$ in the above equation. $\delta(x_{m+1}, y_{n+1})$ is the alignment distance between $x_{m+1}$ and $y_{n+1}$. It is calculated on Table 7.1. $d_{mn}$ is the alignment score for all residues from two sequences, which have been aligned in the previous steps, i.e., $x_1x_2\dots x_m$ and $y_1y_2\dots y_n$. In dynamic programming table, this incremental alignment is called the diagonal move.

The second incremental alignment type is to align the first remaining residue $y_{n+1}$ of sequence $y$ with a gap. This implies that a gap is inserted into sequence $x$. The formula of calculating the alignment cost is shown below,

```
$d(\\dots x_m|-, \dots y_n|y_{n+1}) = d_{mn} + \delta(-, y_{n+1})$   (7.8)
```

where the hyphen stands for an insertion in sequence $x$ and $\delta(-, y_{n+1})$ is a gap penalty applied in this new alignment. This incremental alignment is called the horizontal move in the dynamic programming table.

The third incremental alignment aligns the first remaining residue $x_{m+1}$ of sequence $x$ with a gap. A gap is inserted into sequence $y$ for this alignment. The formula of calculating the alignment cost is shown below

```
$d(\\dots x_m|x_{m+1}, \dots y_n|-) = d_{mn} + \delta(x_{m+1}, -)$   (7.9)
```

Similarly, $\delta(x_{m+1}, -)$ is the gap penalty applied in this new alignment. This is called the vertical move in the dynamic programming table.