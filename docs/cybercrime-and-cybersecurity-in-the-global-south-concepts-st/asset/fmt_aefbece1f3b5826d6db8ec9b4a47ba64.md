
We will now explore the conditions in which the identified DMS factors (i.e. `RATD`, `SPND`, `AVOD`) and the other predictors have positive or negative statistical impacts on `SINT`. To do so we use the parts of our regression equation that includes the given DMS factor (i.e. ‘Regression Eq. Extract’ column of [Table 7.6](#ch7.xhtml#table7_6)) then obtain its derivative (i.e. ‘Derivative’ column of [Figure 7.2](#ch7.xhtml#fig7_2)) since a positive value for the derivative indicates the conditions under which the factor has a positive impact, while the negative value for the derivative indicates the conditions under which the factor has a negative impact.

[Table 7.6 Model 1 – Conditions for Which DMS Factors Positively or Negatively Impact SINT](#ch7.xhtml#R_table7_6)

| **Factor** | **Regression Eq. Extract** | **Derivative** | **Direction of Impact** |
| --- | --- | --- | --- |
| RATD | `0.809399*RATD – 0.18951*RATD*SELF` | `0.809399 – 0.18951*SELF` | * Positive if `SELF < 4.27`; * Negative otherwise |
| SPND | `– 0.16798*SPND*SPND + 0.15137*SPND*GSOR` | `– 2*0.16798*SPND + 0.15137*GSOR` | * Negative if `SPND > 0.451*GSOR` |
| AVOD | `+ 0.120845*AVOD*GSAW – 0.10737*AVOD*SELF` | `0.120845*GSAW – 0.10737*SELF` | * Negative if `GSAW < 0.89*SELF` |

These results suggest that the relationship between the DMS and intended cybersecurity compliance is very complex, and is impacted by the values of the other predictor variables:

*   Being more rational (`RATD`) will result in a higher level of cybersecurity compliance depending on whether the level of perceived cybersecurity self-efficacy (`SELF`) is below a threshold (i.e. `SELF < 4.27`);
*   Whether a high `SPND` score will result in a lower level of cybersecurity compliance depends on the corresponding relationship between `SPND` & `GSOR` is impactful (i.e. `SPND > 0.451*GSOR`).
*   Whether a high `AVOD` score will result in a lower level of cybersecurity compliance depends on the corresponding relationship between `GSAW` & `SELF` is impactful (i.e. `GSAW < 0.89*SELF`).

#### 7.7.4.2 Model 2 – Results and Interpretation

[Scott and Bruce (1995)](#ch7.xhtml#ref7_63) empirical evaluations of the five DMS variables noted the following correlations in their samples:

*   Negative correlations: (`RATD` & `AVOD`); (`RATD` & `SPND`); (`RATD` & `INTD`);
*   Positive correlations: (`SPND` & `INTD`); (`DPND` & `AVOD`)

For our Model 2, we will use the following candidate predictor variables: `GSAW`, `GSOR`, `SELF`, `RATD` and `DNPD`. Here rather than including all five DMS variables, we only include the two that are not correlated.

[Figure 7.3](#ch7.xhtml#fig7_3) provides results from this regression analysis in the form of the main effects and interaction effects that are statistically significant at the 0.05 level, along with the corresponding coefficients. The associated R-squared value is 0.475

![Figure 7.3 Model 1 – Results of Regression Analysis](images/fig7_3_B.jpg)

[Figure 7.3 Model 1 – Results of Regression Analysis](#ch7.xhtml#R_fig7_3)

The results displayed in [Table 7.6](#ch7.xhtml#table7_6) suggest the following:

```
SINT = 0.753586
     + 1.393483 * GSOR - 0.27937 * GSAW * GSOR + 0.183525 * GSAW * SELF
     - 0.19197 * RATD * SELF + 0.178461 * GSAW * RATD
```

We will now explore the conditions in which the identified DMS variable (i.e. `RATD`) and the other predictors have positive or negative statistical impacts on `SINT`. [Table 7.7](#ch7.xhtml#table7_7) presents these results.

[Table 7.7 Model 2 – Conditions for Which DMS Factors Positively or Negatively Impact SINT](#ch7.xhtml#R_table7_7)

| **Factor** | **Regression Eq. Extract** | **Derivative** | **Direction of Impact** |
| --- | --- | --- | --- |
| RATD | `– 0.19197*RATD*SELF + 0.178461*GSAW*RATD` | `– 0.19197*SELF + 0.178461*GSAW` | * Positive only if `GSAW > 1.08*SELF` |
| GSOR | `1.393483*GSOR – 0.27937*GSAW*GSOR` | `1.393483 – 0.27937*GSAW` | * Positive only if `GSAW < 4.8` |
| GSAW | `– 0.27937*GSAW*GSOR + 0.183525*GSAW*SELF + 0.178461*GSAW*RATD` | `– 0.27937*GSOR + 0.183525*SELF + 0.178461*RATD` | * Positive only if `GSOR < 0.66*SELF + 0.64*RATD` |
| SELF | `0.183525*GSAW*SELF – 0.19197*RATD*SELF` | `0.183525*GSAW – 0.19197*RATD` | * Positive only if `GSAW > 1.05*RATD` |

These results suggest that the relationship between the DMS and intended cybersecurity compliance is very complex, and is impacted by the values of the other predictor variables:

*   Whether being more rational will result in a higher level of cybersecurity compliance depends on the relationship between *General Security Awareness* and perceived *Self-Efficacy* (i.e. `GSAW > 1.08*SELF`);
*   Whether a higher level of *General Security Orientation* will result in a higher level of cybersecurity compliance depends on the corresponding level of *General Security Awareness* (i.e. `GSAW < 4.8`);
*   Whether a higher level of *General Security Awareness* will result in a higher level of cybersecurity compliance depends on the relationship between *General Security Orientation*, perceived *Self-Efficacy*, and the level of rationality (i.e. `GSOR < 0.66*SELF + 0.64*RATD`);
*   Whether a higher level of perceived *Self-Efficacy* will result in a higher level of cybersecurity compliance depends on the relationship between *General Security Awareness* and the level of rationality (i.e. `GSAW > 1.05*RATD`).

## 7.8 Conclusion

In this chapter, we conducted an exploration of the relationships between individual DMS and cybersecurity compliance using different DMS variables than were used in previous research. The results of this research have implications for both theory and practice.

With regard to practice, we expect that organizations would be interested in knowing the impacts of both discretionary (e.g. `GSAW`) variables and non-discretionary variables (e.g. `GSOR`, `RATD`) on the level of *Security Compliance* since this could help them in several ways. For example, with respect to discretionary variables it could identify the employees in which they can invest less while achieving the same or higher level of security compliance. This would be of particular importance to organizations with budget and other type’s resource constraints including small and medium enterprises (SMEs) and other types of enterprises in developing countries. For example, for projects which require a high level of security compliance, at the point of assignment of employees to such projects, the non-discretionary variables (e.g. `GSOR`, `RATD`) could be used to identify employees who would be a good fit.

With regard to theory, our approach offers the opportunity to abduct new hypotheses that relate to antecedents of cybersecurity compliance behaviour. At a minimum, this is another study along with those of Donalds and Osei-Bryson ([2017](#ch7.xhtml#ref7_21), [2020](#ch7.xhtml#ref7_22)) whose results suggest that individual DMS has statistically significant impacts on cybersecurity compliance behaviour. Our results suggest that some of such hypotheses could involve DMS variables as moderators.

We consider these results to be preliminary because it is not certain that our sample is sufficiently representative of the various organizational and cultural contexts that exist, and so these results should be subjected to future empirical analysis. However, there seems to be a good reason to expect that inclusion of DMS variables in causal models that explain and/or predict security compliance will be shown to be warranted.

## References

*   Ali, A. (1989). Decision styles and work satisfaction of Arab executives: A cross- national study. International Studies of Management and Organization, *19*(2), 22–37.
