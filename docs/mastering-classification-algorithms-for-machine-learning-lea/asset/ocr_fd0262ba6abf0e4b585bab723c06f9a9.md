Encoders 335

]

)
df

| EmployeeID | Name Designation MaritalStatus NumberOfChildren |
|---|---|---|---|---||
| 0 | E001 | Partha | Director | Married | 2 |
| 1 | E002 | Deepshree | Manager | Married | 2 |
| 2 | E003 | Riya | Programmer | Single | 0 |
| 3 | E004 | Ranoe | Programmer | Single | 0 |
| 4 | E005 | Ujwala | Programmer | Widow | 1 |
| 5 | E006 | Anita | Manager | Married | 1 |
| 6 | E007 | Nomita | Programmer | Divorce | 2 |
| 7 | E008 | Anil | Programmer | Widower | 0 |
| 8 | E009 | Amarendra | Programmer | Married | 1 |
| 9 | E010 | Anuj | Manager | Married | 2 |

We will apply One-Hot Encoding in the column "Designation":
from sklearn.preprocessing import OneHotEncoder

```
oheDesignation = OneHotEncoder()
transformed = oheDesignation.fit_transform(df['Designation']).todense()
dfTemp = pd.DataFrame(transformed, columns = oheDesignation.get_feature_names_out())
print(dfTemp)
```

Designation_Director Designation_Manager Designation_Programmer

| | 1.0 | 0.0 | 0.0 |
|---|---|---|--|
| 0 | | 0.0 | 0.0 |
| 1 | | 0.0 | 1.0 | 0.0 |
| 2 | | 0.0 | 0.0 | 1.0 |
| 3 | | 0.0 | 0.0 | 1.0 |