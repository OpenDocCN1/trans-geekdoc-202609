0  3  0  1  0
1  1  1  3  1  0  1  1  1  0  2  0  1  0  0  2  1  0  3  3  3  0  3  3  3  0  1  0

The pairings given by this alignment are consistent. This is, in fact, the only consistent alignment for when MATHEMATICS is broken up as MA TH EM AT IC Sx and enciphered. However, as explained earlier, MATHEMATICS could be broken up as xM AT HE MA TI CS and then enciphered. In this case, the form pattern is (1, 2, 0, 2, 0). Because this pattern has two zeros separated by a single value we check alignments in positions where the ciphertext also has this form:

1  2  0  2  0
1  1  1  3  1  0  1  1  1  0  2  0  1  0  0  2  1  0  3  3  3  0  3  3  3  0  1  0

This alignment cannot be correct, because it sends the first 2 to 1 and the second 2 to 2, which is inconsistent.

1  2  0  2  0
1  1  1  3  1  0  1  1  1  0  2  0  1  0  0  2  1  0  3  3  3  0  3  3  3  0  1  0

This alignment is rejected, because it sends the 1 to 0.

1  2  0  2  0
1  1  1  3  1  0  1  1  1  0  2  0  1  0  0  2  1  0  3  3  3  0  3  3  3  0  1  0

This alignment is also impossible, as 1 cannot be paired with 3, if 2 is also paired with 3. Sometimes there will be several consistent alignments. The fact that the ciphertext was short made this less likely for the example above. Usually having more ciphertext makes the cipher easier to break, but for this attack it creates more work! Our only consistent alignment

0  3  0  1  0
1  1  1  3  1  0  1  1  1  0  2  0  1  0  0  2  1  0  3  3  3  0  3  3  3  0  1  0

tells us that MA TH EM AT IC Sx was enciphered as CI PM QE MF OU.

Representing our unknown enciphering matrix as (a  b; c  d), we get the following equations:

MA → CI  ⇒  (a  b; c  d)(12; 0) = (2; 8)  ⇒  12a = 2  and  12c = 8

TH → PM  ⇒  (a  b; c  d)(19; 7) = (15; 12)  ⇒  19a + 7b = 15  and  19c + 7d = 12

EM → QE  ⇒  (a  b; c  d)(4; 12) = (16; 4)  ⇒  4a + 12b = 16  and  4c + 12d = 4

AT → MF  ⇒  (a  b; c  d)(0; 19) = (12; 5)  ⇒  19b = 12  and  19d = 5

IC → OU  ⇒  (a  b; c  d)(8; 2) = (14; 20)  ⇒  8a + 2b = 14  and  8c + 2d = 20