

![](img/4cb83489753bba67a16c119dae990237_62_0.png)

图 3.22 字符矩阵分支图

系统发生树，如图 3.22 所示。另一方面，海龟拥有所给五个特征中的四个，因此看起来最接近豹。

物种特征实际上是通过统计物种 DNA 的相似性百分比来比较的。图 3.23(a) 得到的系统发生树实际上称为分支图。系统发生树的实际表示如图 3.23(b) 所示。

创建分支图时需要牢记的另一个重要点是，可能需要在多个选项中进行选择来创建分支图。可能需要考虑多个特征。这里的目标是在分支图中从一个分支移动到另一个分支时，使进化步骤数最少。哺乳动物–鸟类分支类群和蜥蜴–鸟类分支类群的示例如图 3.24 所示。

### (a)

| 特征 | 氙鱼 | 七鳃鳗 | 金枪鱼 | 蝾螈 | 龟 | 豹 |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| 毛发 | 0 | 0 | 0 | 0 | 0 | 1 |
| 羊膜卵 | 0 | 0 | 0 | 0 | 1 | 1 |
| 四条步行腿 | 0 | 0 | 0 | 1 | 1 | 1 |
| 可动颚 | 0 | 0 | 1 | 1 | 1 | 1 |
| 脊柱 | 0 | 1 | 1 | 1 | 1 | 1 |

### (b)

![](img/4cb83489753bba67a16c119dae990237_63_0.png)

图 3.23 (a) 字符矩阵；(b) 系统发生树

![](img/4cb83489753bba67a16c119dae990237_64_0.png)

![](img/4cb83489753bba67a16c119dae990237_64_1.png)

图 3.24 (a) 哺乳动物–鸟类分支类群；(b) 蜥蜴–鸟类分支类群

## 附录

### 使用 ASP.NET 和 C# 实现 UPGMA 算法

### 基于距离的 (UPGMA)

新生物的进化由以下因素驱动

- 多样性：不同个体携带相同基本蓝图的不同变异
- 突变：由于单碱基变化、DNA 片段的插入/删除等，DNA 序列可能发生改变
- 选择偏差

现代生物学方法允许使用分子特征，即基因序列和蛋白质序列。目标是生成一棵树，使得相似序列（短距离）彼此更接近，且两个节点的支距之和等于它们的距离。

UPGMA：非加权对组算术平均法。

- 假设存在分子钟（恒定的进化速率）
- 生成有根树
- 超度量条件：对于任意三个分类单元 (a,b,c)，dac <= max(dab, dbc)。

换句话说：两个最大距离必须相等。

或者：所有分支的进化速率恒定。

### UPGMA 条件

dAB <= max(dAC,dBC)
dAC <= max(dAB,dBC)
dBC <= max(dAB, dAC)

![](img/4cb83489753bba67a16c119dae990237_65_0.png)

初始化：定义 T 为叶节点集合，每个序列对应一个叶节点。每个节点的高度均为零。令 L = T。重复

- 选择最接近的两个节点 (A, B) 并为它们创建父节点 K。分别连接 A、B 和 K。将节点 K 的高度设置为 dAB/2。将 K 与 A 之间的支长设置为 height K – height A，将 K 与 B 之间的支长设置为 height K – height B。
- 从 L 中移除 A、B 并将 K 加入 L。重新计算 K 与 L 中其他节点之间的距离。K 与其他节点之间的距离是 K 下方叶序列与该其他节点之间的平均距离。

直到只剩一个节点

### 前端设计

- 1. 添加文本框和按钮以获取矩阵大小的输入。
- 2. 添加 DataList 以获取输入矩阵坐标。
- 3. 添加 Div 以显示输出。

### C# 代码说明

- 1. 生成一个 DataTable 并将 DataList 的数据源绑定到它，以获取矩阵元素的输入。
- 2. 将 DataList 的值存储到数据表 (dtMain) 中。
- 3. 为步骤打开一个 for 循环。
- 4. 查找最小值及其坐标。
- 5. 在 Label 中显示它们，并将 Label 添加到 Div 中以显示步骤输出。
- 6. 现在用新元素重建矩阵。合并最小值对应元素的坐标。计算所有对应距离的平均值。
- 7. 现在将 DataTable 绑定到 GridView，并将 GridView 添加到 Div 中以显示步骤输出。
- 8. 循环按矩阵大小执行。
- 9. 每个步骤的输出将在 aspx 页面上可用。

### ASP.CS 页面代码

```csharp
using System;
using System.Collections.Generic;
using System.Data;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;
public partial class upgma: System.Web.UI.Page
{
static int step = 0;
DataTable dtMain = new DataTable();
protected void btnStart_Click(object sender, EventArgs e)
{
int size = Convert.ToInt32(txtSize.Text);
dtMain = new DataTable();
for (int i = 0; i <= size; i++)
dtMain.Columns.Add();
dtMain.AcceptChanges();
for (int i = 0; i <= size; i++)
{
dtMain.Rows.Add();
for (int j = 0; j <= size; j++)
{
TextBox txt = (TextBox)dlInput.Items[(size * j) + i + j].FindControl("txtInput");
dtMain.Rows[i][j] = txt.Text;
}
}
dtMain.AcceptChanges();
GridView gvInput = new GridView();
gvInput.ID = "gvMatrix";
gvInput.ShowHeader = false;
gvInput.DataSource = dtMain;
gvInput.DataBind();
divResults.Controls.Add(gvInput);
step = size;
DataTable dtTemp = new DataTable();
dtTemp = dtMain;
int r=0, c = 0;
for (int l = 0; l < size-1; l++)
{
    decimal min = Convert.ToDecimal(dtTemp.Rows[1][2]);
    r = 1;
    c = 2;
    for (int i = 1; i <= step; i++)
    for (int j = i + 1; j <= step; j++)
    {
        if (min > Convert.ToDecimal(dtTemp.Rows[i][j]))
        {
            min = Convert.ToDecimal(dtTemp.Rows[i][j]);
            r = i;
            c = j;
        }
    }
}
Label lbl = new Label();
lbl.ID = "lblSteps" + l;
lbl.Text = "Step " + (l + 1);
lbl.Text += "<br/> Min Value is " + min.ToString() + " at coordinates["+ r +","+ c + "]";
lbl.Text += "<br/> Merge the elements of rows and columns corresponding of (" + dtTemp.Rows[0][c] + ") and (" + dtTemp.Rows[r][0] + ")";
divResults.Controls.Add(lbl);
DataTable dtT = new DataTable();
step--;
for (int i = 0; i <= step; i++)
dtT.Columns.Add();
int pc = 0;
int pr = 0;
for (int i = 0; i <= step; i++)
{
    dtT.Rows.Add();
    for (int j = 0; j <= step; j++)
    {
        if ((i == r || j == r) && (i != j))
        {
            if ((i == 0 || j == 0))
            {
            dtT.Rows[i][j] = dtTemp.Rows[0][r].ToString() + "," + dtTemp.Rows[0][c].ToString();
            if (i == 0)
            pc++; // increase column index because of column merge from beginning or middle
            else
            pr++; // increase row index because of row merge from beginning or middle
            }
            else if (j > i)
            {
            dtT.Rows[i][j] = getMeanDistance(dtT.Rows[i][0].ToString(), dtT.Rows[0][j].ToString()).ToString();
            //dtT.Rows[i][j] = "rc";
            }
        }
        else
        {
        if (i != j)
        {
        if (c != step + 1)
        {
        if (j > r && i > r)
        dtT.Rows[i][j] = dtTemp.Rows[i + pr][j + pc];
        else if (j > r)
        dtT.Rows[i][j] = dtTemp.Rows[i][j + pc];
        else if (i > r)
        dtT.Rows[i][j] = dtTemp.Rows[i + pr][j];
        else
        dtT.Rows[i][j] = dtTemp.Rows[i][j];
        }
        else
        dtT.Rows[i][j] = dtTemp.Rows[i][j];
        }
        }
    }
}
dtT.AcceptChanges();
dtTemp = dtT;
GridView gv = new GridView();
gv.ID = "gvMatrix" + 1.ToString();
gv.ShowHeader = false;
gv.DataSource = dtT;
gv.DataBind();
divResults.Controls.Add(gv);
}
}
protected decimal getMeanDistance(string a, string b)
{
    decimal rslt = 0;
    string[] stra = a.Split(';');
    string[] strb = b.Split(';');
    for (int i = 0; i < stra.Length; i++)
    for (int j = 0; j < strb.Length; j++)
    {
        int posx = GetCharPosition(stra[i], "From");
        int posy = GetCharPosition(strb[j], "To");
        if (posx < posy)
        rslt += Convert.ToDecimal(dtMain.Rows[posx][posy]);
        else
        rslt += Convert.ToDecimal(dtMain.Rows[posy][posx]);
    }
    rslt = rslt / (stra.Length * strb.Length);
    return Math.Round(rslt, 2);
}

protected int GetCharPosition(string strChar, string strType)
{
    int pos = 0;
    if (strType == "From")
    {
    for (int i = 1; i < dtMain.Rows.Count; i++)
    if (dtMain.Rows[i][0].ToString() == strChar)
    {
    pos = i;
    break;
    }
    }
    else
    {
    for (int j = 1; j < dtMain.Columns.Count; j++)
    if (dtMain.Rows[0][j].ToString() == strChar)
    {
    pos = j;
    break;
    }
    }
    return pos;
}

protected void btnGenerateMatrix_Click(object sender, EventArgs e)
{
    DataTable dt = new DataTable();
    int size = Convert.ToInt32(txtSize.Text) + 1;
    dt.Columns.Add();
    for (int i = 0; i < size * size; i++)
```

