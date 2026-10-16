```
In [33]:

# parameters:
# degree: degree of terms
# interaction_only: no x**2, only x*y (and x,y)
# include_bias: constant term
quad_inters = skpre.PolynomialFeatures(degree=2,      # degree of terms
                                    interaction_only=True, # no x**2, only x*y
                                    include_bias=False)   # constant term
subset = iris_df.loc[[0, 50, 100], ['sepal length', 'sepal width']]
new_terms = pd.DataFrame(quad_inters.fit_transform(subset),
                         index=[0, 50, 100])
new_terms.set_axis(['sep length', 'sep width', 'sep area'],
                   axis=1, inplace=True)

# note: creating the interaction *also*
# includes the base terms in the interaction
display(new_terms)
```

|  | sep length | sep width | sep area |
|---|---|---|---|
| 0 | 5.1000 | 3.5000 | 17.8500 |
| 50 | 7.0000 | 3.2000 | 22.4000 |
| 100 | 6.3000 | 3.3000 | 20.7900 |

This representation may be good enough, particularly if we want to make these steps part of an sklearn pipeline. However, we can get much finer grained control using patsy.

# 10.6.2.1 Interactions via Patsy Formulas

Now we can get a big win from using patsy formulas. Patsy lets us specify interactions with either : or *. The difference is that : only includes the interaction— sepal_width * sepal_length—between the two, like interaction_only=True in skpre.PolynomialFeatures.

```
In [34]:

design_df = patsy.dmatrix("Q('sepal length'):Q('sepal width') - 1",
                        data=iris_df.iloc[[0, 50, 100]],
                        return_type='dataframe')
design_df
```