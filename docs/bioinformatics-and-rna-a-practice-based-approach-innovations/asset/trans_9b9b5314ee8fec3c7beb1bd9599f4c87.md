

![](img/4cb83489753bba67a16c119dae990237_39_0.png)

### 图 2.19 NCBI – 多序列比对（步骤 4）

![](img/4cb83489753bba67a16c119dae990237_39_1.png)

### 图 2.20 多序列比对

![](img/4cb83489753bba67a16c119dae990237_40_0.png)

### 图 2.21 Clustal Omega – 多序列比对示例

![](img/4cb83489753bba67a16c119dae990237_40_1.png)

### 图 2.22 Clustal Omega – 多序列比对

![](img/4cb83489753bba67a16c119dae990237_41_0.png)

### 图 2.23 分支图 – Clustal Omega 系统发育树

步骤 8。现在可以单击“系统发育树”构建分支图或系统发育树，如图 2.22 和 2.23 所示。

## 附录

## 使用 ASP.net 和 C# 实现 Needleman-Wunsch 全局序列比对算法

序列比对是排列两个或多个字符序列的一种方法，以识别相似区域——相似性可能是这些序列之间功能或进化关系的结果。

它是一种通过查找一系列在这些序列中具有相同顺序的单个字符来比较两个或多个序列的过程。

为给定规则集查找序列之间的最优全局比对。

共有三个步骤：

- 1. 初始化步骤
- 2. 矩阵填充步骤
- 3. 回溯步骤

### 设计前端

- 1. 放置五个输入框和一个按钮，前两个文本框用于序列，三个文本框用于匹配、错配和间隙值，按钮用于执行单击操作。
- 2. 放置两个 GridView 和标签以可视化矩阵操作并输出两个序列比对结果。

### C# 代码说明

- 1. 输入五个变量，分别为第一个序列的长度、第二个序列的长度、匹配、错配和间隙。
- 2. 定义两个矩阵，大小均为第一个和第二个序列长度加 1，一个用于得分，另一个用于回溯。
- 3. 根据得分值填充两个矩阵（最大得分值为 opt）。
- 4. 在回溯矩阵中，D 表示对角线，L 表示左侧，U 表示上方得分值。
- 5. 将两个矩阵转换为数据表，以便在网格视图中可视化数据。
- 6. 调用回溯函数在标签中显示两个比对后的序列。
- 7. 如果值为 D，即对角线，则写出两个序列的两个字符；否则，对于 L 和 U 得分值，仅写出相应序列的一个字符。

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

### 输出截图

www.medixny.com/globalseq.aspx

输入序列 1
输入序列 2
填充矩阵

得分矩阵
输出

匹配 1
错配 0
间隙 -1

### 两个给定序列 ACGC 和 GACTAC 的输出

输入序列 1: ACGC
输入序列 2: GACTAC

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

## 附录

### 练习

### 选择题

Q1. Needleman-Wunsch 算法使用哪种编程技术来高效执行全局比对？

- a. 启发式方法
- b. 列表推导式
- c. 动态规划
- d. 矩阵代数

Q2. 如果两个序列显示出显著相似性，这意味着

- a. 它们是旁系同源基因。
- b. 它们是直系同源基因。
- c. 它们从共同祖先进化而来。
- d. 已发生水平基因转移。

Q3. 以下哪项是序列比对工具？

- a. BLAST
- b. PRINT
- c. PROSITE
- d. PIR

Q4. 对相关基因进行多序列比对可以识别蛋白质功能所需的氨基酸。

- a. 正确
- b. 错误

Q5. BLAST 程序用于

- a. DNA 测序。
- b. 氨基酸测序。
- c. DNA 条形码。
- d. 生物信息学。

Q6. Clustal W 是一种

- a. 多序列比对工具。
- b. 蛋白质二级结构预测工具。
- c. 数据检索工具。
- d. 核酸序列分析工具。

Q7. 通过在序列中查找相同顺序的模式来比对两个序列的过程是

- a. 序列比对。
- b. 两两比对。
- c. 多序列比对。
- d. 以上都是。

Q8. 序列比对帮助科学家

- a. 追踪进化关系。
- b. 推断新合成基因的功能。
- c. 预测基因家族的新成员。
- d. 以上都是。

Q9. 多序列比对中保守良好的区域

- a. 反映结构重要区域。
- b. 反映功能重要区域。
- c. 反映功能和结构重要区域。
- d. 反映可能具有功能和/或结构重要性的区域。

Q10. 为什么配色方案在创建和分析序列比对中很重要？

- a. 它们看起来漂亮。
- b. 它们使打印件和演示文稿更清晰。
- c. 它们让你更容易区分保守残基和残基组。
- d. 它们让你检测蛋白质的活性位点。

### 论述题

Q1. 你对序列比对是什么意思？它在计算生物学中的应用有哪些？

Q2. 详细解释全局序列比对。另外，对以下提到的 DNA 序列执行全局序列比对：

T G A
T T A

