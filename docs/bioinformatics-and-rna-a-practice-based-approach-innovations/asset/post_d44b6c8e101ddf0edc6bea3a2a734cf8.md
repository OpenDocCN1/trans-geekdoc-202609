
![](img/4cb83489753bba67a16c119dae990237_39_0.png)

### FIGURE 2.19 NCBI – Multiple Sequence Alignment (Step 4)

![](img/4cb83489753bba67a16c119dae990237_39_1.png)

### FIGURE 2.20 Multiple Sequence Alignment

![](img/4cb83489753bba67a16c119dae990237_40_0.png)

### FIGURE 2.21 Clustal Omega – Multiple Sequence Alignment Example

![](img/4cb83489753bba67a16c119dae990237_40_1.png)

### FIGURE 2.22 Clustal Omega – Multiple Sequence Alignment

![](img/4cb83489753bba67a16c119dae990237_41_0.png)

### FIGURE 2.23 Cladogram – Clustal Omega Phylogenetic Tree

Step 8. The cladogram or phylogenetic tree can now be constructed by clicking “Phylogenetic Tree” as shown in Figures 2.22 and 2.23.

## APPENDIX

## Implementing the Needleman-Wunsch global sequence alignment algorithm using ASP.net and C#

Sequence alignment is a way of arranging two or more sequences of characters to identify regions of similarity – similarities may be a consequence of functional or evolutionary relationships between these sequences.

It is a procedure for comparing two or more sequences by searching for a series of individual characters that are in the same order in those sequences.

Find optimal global alignment between sequences for a given set of rules.

There are three steps:

- 1. Initialization step
- 2. Matrix fill step
- 3. Trace-back step

### Design front end

- 1. Take five input boxes and one button, first two text boxes for sequences, three text boxes for match, mismatch and gap value and button to perform a click action.
- 2. Take two gridviews and labels to visualize the matrix operation and output both sequence alignments.

### C# code explained

- 1. Input five variables for the length of the first sequence, length of the second sequence, match, mismatch and gap.
- 2. Define two matrices of first and second sequence length + 1, one for scoring and the second for trace-back.
- 3. Fill both matrices according to the score value (max score value is opt).
- 4. In the traceback matrix, use D for diagonal, L for left, U for upper score value.
- 5. Convert both matrices into a data table to visualize the data into a grid view.
- 6. Call the trace-back function to display both aligned sequences in labels.
- 7. If the value is D, i.e. diagonal, then write both characters of both sequences; otherwise, in the case of L and U score values, we write only one character of the corresponding sequence.

```csharp
using System;
using System.Collections.Generic;
using System.Data;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;
public partial class GlobalSeq: System.Web.UI.Page
{
    protected void btnFillMatrix_Click(object sender, EventArgs e)
    {
        int a = txtSeq1.Text.Length+1;
        int b = txtSeq2.Text.Length+1;
        int ma=Convert.ToInt32(txtMatch.Text);
        int mi=Convert.ToInt32(txtMisMatch.Text);
        int Ga=Convert.ToInt32(txtGap.Text);
        int[,] ScoreMatrix=new int[a,b];
        char[,] tracebackMatrix = new char[a, b];
        ScoreMatrix[0,0]=0;
        for (int i = 1; i < a; i++)
        {
            ScoreMatrix[i, 0] = i * Ga;
            tracebackMatrix[i, 0] = 'U';
        }
        for (int j = 1; j < b; j++)
        {
            ScoreMatrix[0, j] = j * Ga;
            tracebackMatrix[0, j] = 'L';
        }
        for (int i = 1; i < a; i++)
        {
            for (int j = 1; j < b; j++)
            {
                int scoreDiag = 0;
                if (txtSeq2.Text.Substring(j - 1, 1) == txtSeq1.Text.Substring(i - 1, 1))
                    scoreDiag = ScoreMatrix[i - 1, j - 1] + ma;
                else
                    scoreDiag = ScoreMatrix[i - 1, j - 1] + mi;
                int scoreLeft = ScoreMatrix[i, j - 1] + Ga;
                int scoreUp = ScoreMatrix[i - 1, j] + Ga;
                int maxScore = Math.Max(Math.Max(scoreDiag, scoreLeft), scoreUp);
                ScoreMatrix[i, j] = maxScore;
                if (ScoreMatrix[i, j] == scoreDiag)
                {
                    tracebackMatrix[i, j] = 'D';
                }
                else if (ScoreMatrix[i, j] == scoreLeft)
                {
                    tracebackMatrix[i, j] = 'L';
                }
                else if (ScoreMatrix[i, j] == scoreUp)
                {
                    tracebackMatrix[i, j] = 'U';
                }
            }
        }
        GridView1.DataSource = ConvertArrayToDataTable(ScoreMatrix, a, b);
        GridView1.DataBind();
        GridView2.DataSource = ConvertArrayToDataTable(tracebackMatrix, a, b);
        GridView2.DataBind();
        TraceBack(tracebackMatrix, txtSeq1.Text, txtSeq2.Text);
    }

    public DataTable ConvertArrayToDataTable(int[,] ScoreMatrix, int a, int b)
    {
        DataTable dt = new DataTable();
        for (int j = 0; j < b; j++)
            dt.Columns.Add(j.ToString());
        for (int i = 0; i < a; i++)
        {
            dt.Rows.Add();
            for (int j = 0; j < b; j++)
                dt.Rows[i][j] = ScoreMatrix[i, j];
        }
        dt.AcceptChanges();
        return dt;
    }

    public DataTable ConvertArrayToDataTable(char[,] ScoreMatrix, int a, int b)
    {
        DataTable dt = new DataTable();
        for (int j = 0; j < b; j++)
            dt.Columns.Add(j.ToString());
        for (int i = 0; i < a; i++)
        {
            dt.Rows.Add();
            for (int j = 0; j < b; j++)
                dt.Rows[i][j] = ScoreMatrix[i, j];
        }
        dt.AcceptChanges();
        return dt;
    }

    public void TraceBack(char[,] tracebackMatrix, string sequenzA, string sequenzB)
    {
        int i = tracebackMatrix.GetLength(0) - 1;
        int j = tracebackMatrix.GetLength(1) - 1;
        string alignedSeqA = "";
        string alignedSeqB = "";
        while (i != 0 || j != 0)
        {
            switch (tracebackMatrix[i, j])
            {
                case 'D':
                    alignedSeqA += sequenzA[i - 1];
                    alignedSeqB += sequenzB[j - 1];
                    i--;
                    j--;
                    break;
                case 'U':
                    alignedSeqA += sequenzA[i - 1];
                    alignedSeqB += "-";
                    i--;
                    break;
                case 'L':
                    alignedSeqA += "-";
                    alignedSeqB += sequenzB[j - 1];
                    j--;
                    break;
            }
        }
        lblSequence1.Text = reverseString(alignedSeqA);
        lblSequence2.Text = reverseString(alignedSeqB);
    }

    public string reverseString(string strInp)
    {
        char[] arr = strInp.ToCharArray();
        Array.Reverse(arr);
        return new string(arr);
    }
}
```

### Output screenshot

www.medixny.com/globalseq.aspx

Input Sequence 1
Input Sequence 2
Fill Matrix

Score Matrix
Output

Match 1
Mismatch 0
Gap -1

### Output for two given sequences, ACGC and GACTAC

Input Sequence 1: ACGC
Input Sequence 2: GACTAC

| 0 | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|
| 0 | -1 | -2 | -3 | -4 | -5 | -6 |
| -1 | 0 | 0 | -1 | -2 | -3 | -4 |
| -2 | -1 | 0 | 1 | 0 | -1 | -2 |
| -3 | -1 | -1 | 0 | 1 | 0 | -1 |
| -4 | -2 | -1 | 0 | 0 | 1 | 1 |

| 0 | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|
| | L | L | L | L | L | L |
| U | D | D | L | L | D | L |
| U | D | D | D | L | L | D |
| U | D | D | D | D | D | D |
| U | U | D | D | D | D | D |

-AC-GC
GACTAC

## APPENDIX

### Exercise

### Multiple-Choice Questions

Q1. Which programming technique is used in the Needleman-Wunsch algorithm to allow it to efficiently carry out global alignment?

- a. heuristic approach
- b. list comprehension
- c. dynamic programming
- d. matrix algebra

Q2. If two sequences show significant similarity, it means

- a. they are paralogs.
- b. they are orthologs.
- c. they evolved from a common ancestor.
- d. HGT has occurred.

Q3. Which of the following is a sequence alignment tool?

- a. BLAST
- b. PRINT
- c. PROSITE
- d. PIR

Q4. A multiple sequence alignment of related genes can identify amino acids required for protein function.

- a. True
- b. False

Q5. The BLAST program is used in

- a. DNA sequencing.
- b. amino acid sequencing.
- c. DNA barcoding.
- d. bioinformatics.

Q6. Clustal W is a

- a. multiple sequence alignment tool.
- b. protein secondary structure predicting tool.
- c. data retrieving tool.
- d. nucleic acid sequence analysis tool.

Q7. The procedure of aligning two sequences by searching for patterns in the same order in the sequences is

- a. sequence alignment.
- b. pairwise alignment.
- c. multiple sequence alignment.
- d. all of these.

Q8. Sequence alignment helps scientists

- a. trace out evolutionary relationships.
- b. infer the functions of newly synthesized genes.
- c. predict new members of gene families.
- d. with all of these.

Q9. Well-conserved regions in multiple sequence alignments

- a. reflect areas of structural importance.
- b. reflect areas of functional importance.
- c. reflect areas of both functional and structural importance.
- d. reflect areas likely to be of functional and/or structural importance.

Q10. Why are colour schemes important in creating and analyzing sequence alignments?

- a. They look pretty.
- b. They make clearer printouts and presentations.
- c. They allow you to distinguish conserved residues and residue groups more easily.
- d. They allow you to detect active sites of proteins.

### Essay-Type Questions

Q1. What do you mean by sequence alignment? What are its applications in computational biology?

Q2. Explain global sequence alignment in detail. Also, perform global sequence alignment on the below-mentioned DNA sequences:

T G A
T T A
