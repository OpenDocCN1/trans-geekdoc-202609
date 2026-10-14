# The generated passage

![](bbox=[0.17, 0.15, 0.86, 0.6])

Figure 11-10. The color of each square in the matrix indicates the amount of attention given to each position on the vertical axis, at the point of predicting the note on the horizontal axis

There are also examples of where the network has chosen to ignore a certain note or rest nearby, as it doesn't add any additional information to its understanding of the phrase. For example, the penultimate note (A2) is not particularly attentive to the B-2 three notes back, but is slightly more attentive to the A2 four notes back. It is more interesting for the model to look at the A2 that falls on the beat, rather than the B-2 off the beat, which is just a passing note.

Remember we haven't told the model anything about which notes are related or which notes belong to which key signatures—it has worked this out for itself just by studying the music of J.S. Bach.