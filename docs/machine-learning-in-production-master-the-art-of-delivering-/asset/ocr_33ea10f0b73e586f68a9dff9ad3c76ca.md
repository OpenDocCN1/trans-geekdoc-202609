```
3. MetricsSelector,
4. MetricConstraint)
5.
6. # Function with Constraints for Data Quality Validation
7. def validate_feat(profile_view, verbose=False, viz=False):
8. builder = ConstraintsBuilder(profile_view)
9. # Define a constraint for data validation
10. builder.add_constraint(MetricConstraint(
11. name="Credit_History == 0 or == 1",
12. condition=lambda x: x.min == 0 or x.max == 1,
13. metric_selector=MetricsSelector(metric_name='distribution',
14. column_name='Credit_History')
15. ))
16.
17. # Build the constraints and return the report
18. constraints: Constraints = builder.build()
19.
20. if verbose:
21. print(constraints.report())
22.
23. # return constraints.report()
24. return constraints
25.
26. const = validate_feat(profile_view1, True)
```

In the current scenario, constraints are set to ensure that the **Credit_History** feature should contain either **0** or **1**. If it receives any value other than **0** or **1**, it will fail. You can add multiple constraints to validate multiple conditions at once. The following is the output of the preceding code:

```
[('Credit_History == 0 or == 1', 1, 0)]
```

This can be read as [('Constraint Name', Pass, Fail)]. It can be visualized with the whyllogs visualization functionality in the notebook.