Step 1: Let us consider that the three seeds or cluster heads are the first three students, Tarun, Medha, and Bhavik, as shown in the following table:

| Cluster Head | Student Name | English | Hindi | Maths |
|---|---|---|---|---|
| C₁ | Tarun | 65 | 81 | 85 |
| C₂ | Medha | 70 | 90 | 78 |
| C₃ | Bhavik | 55 | 65 | 65 |

Table 1.12: Three cluster heads

Step 2: Calculate the Euclidean distance between the cluster head and these four attributes.

Euclidean distance:

D(p, q) = (∑(pᵢ - qᵢ)²)^1/2   (1.23)

Where p and q are the points for which the Euclidean distance is to be calculated.

Let us calculate the distance for the student’s name Tarun from cluster head C₂.

D(A, C₂) = ((65 - 70)² + (81 - 90)² + (85 - 78)²)^1/2
D(A, C₂) = 12.45

Similarly, calculate Euclidean distance for all the points. We get the first iteration result as shown in table 1.13:

| Student name | English | Hindi | Maths | Distance from C₁ | Distance from C₂ | Distance from C₃ | Nearest cluster allocation |
|---|---|---|---|---|---|---|---|
| Tarun | 65 | 81 | 85 | 0 | 12.45 | 27.49 | C₁ |
| Medha | 70 | 90 | 78 | 12.44 | 0 | 29.68 | C₂ |
| Bhavik | 55 | 65 | 65 | 27.49 | 29.98 | 0 | C₃ |
| Anushka | 62 | 76 | 70 | 16.09 | 18 | 13.96 | C₃ |
| Devam | 83 | 86 | 55 | 35.34 | 26.72 | 36.40 | C₂ |
| Farhan | 74 | 58 | 80 | 25.196 | 32.31 | 25.199 | C₃ |
| Gouri | 60 | 70 | 50 | 37.027 | 35.83 | 16.58 | C₃ |
| Himanshu | 91 | 75 | 85 | 26.683 | 26.739 | 42.37 | C₁ |

Table 1.13: Nearest cluster allocation