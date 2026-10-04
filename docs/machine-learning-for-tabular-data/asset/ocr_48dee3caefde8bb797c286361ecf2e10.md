# CHAPTER 6 Advanced feature processing methods

```
model_pipeline['processing']
.get_feature_names_out())
,
OutputXlsFile='fir.xlsx'
fir = pd.read_excel('fir.xlsx', sheet_name='Interaction Depth 1'
result = fir[['Interaction', 'Gain']].sort_values(by='Gain',
```

Generates a report with xgbformat and saves it to an Excel file

Reads the Excel file created in the previous steps

```
ascending=False).head(10)
for index, row in result.iterrows():
    print(f"{row['Interaction']}")
```

Extracts and sorts by split gain
'Interaction' and 'Gain' columns from
the feature report

```
PartialDependenceDisplay.from_estimator(
model_pipeline,
x=data,
kind='average',
features={
    'minimum_nights',
    'calculated_host_listings_count'
})
```

Generates a partial dependence plot for the features='minimum-nights' and 'calculated_host_listings_count'

The code will print a of interactions. If you work with a linear model, each interaction returned by XGBFIR should be tested because it could enhance your model's performance. If you work with decision trees, you can ignore the ones that involve a binary feature and concentrate on only numeric ones. An example is the interaction between minimum_nights and calculated_host_listings_count. Figure 6.5 shows how combining with specific values is strongly associated with a positive target response.

![](bbox=[0.18, 0.545, 0.715, 0.865])

Figure 6.5 Conjoint PDP for two numeric features