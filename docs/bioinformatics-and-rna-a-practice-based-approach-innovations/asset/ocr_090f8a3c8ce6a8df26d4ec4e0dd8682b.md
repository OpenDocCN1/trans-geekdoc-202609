```
{
for (int j = 1; j < b; j++)
{
int scroeDiag = 0;
if (txtSeq2.Text.Substring(j - 1, 1) == txtSeq1.Text.Substring(i - 1, 1))
scroeDiag = ScoreMatrix[i - 1, j - 1] + ma;
else
scroeDiag = ScoreMatrix[i - 1, j - 1] + mi;
int scroeLeft = ScoreMatrix[i, j - 1] + Ga;
int scroeUp = ScoreMatrix[i - 1, j] + Ga;
int maxScore = Math.Max(Math.Max(scroeDiag, scroeLeft), scroeUp);
ScoreMatrix[i, j] = maxScore;
if (ScoreMatrix[i, j] == scroeDiag)
{
tracebackMatrix[i, j] = 'D';
}
else if (ScoreMatrix[i, j] == scroeLeft)
{
tracebackMatrix[i, j] = 'L';
}
else if (ScoreMatrix[i, j] == scroeUp)
{
tracebackMatrix[i, j] = 'U';
}
}
}
}
```

```
GridView1.DataSource = ConvertArrayToDataTable(ScoreMatrix, a, b);
GridView1.DataBind();
GridView2.DataSource = ConvertArrayToDataTable(tracebackMatrix, a, b);
GridView2.DataBind();
TraceBack(tracebackMatrix, txtSeq1.Text, txtSeq2.Text);
}
```

```
public DataTable ConvertArrayToDataTable(int[,] ScoreMatrix,int a,int b)
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
```