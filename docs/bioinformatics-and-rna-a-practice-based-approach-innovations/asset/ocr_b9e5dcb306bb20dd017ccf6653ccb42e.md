```
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
lbl.Text += "<br/> Merge the elements of rows and columns corresponding of
(" + dtTemp.Rows[0][c] + ") and (" + dtTemp.Rows[r][0] + ")";
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
        if ((i == r || j == r) && (i! = j))
        {
            if ((i == 0 || j == 0))
            {

```