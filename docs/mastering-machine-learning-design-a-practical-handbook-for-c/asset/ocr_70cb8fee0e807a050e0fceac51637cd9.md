```
```python
import pandas as pd
# Create synthetic loan data with potential bias
data = pd.DataFrame({
    "loan_amount":[10000, 5000, 15000, 8000],
    "income":[50000, 30000, 70000, 40000],
    "approved":[True, False, True, False],
    "group":["A", "B", "A", "B"] # Introduce group bias
})

# Calculate statistical parity metric
approval_rate_group_A = data[data["group"] == "A"]["approved"].mean()
approval_rate_group_B = data[data["group"] == "B"]["approved"].mean()
parity_difference = abs(approval_rate_group_A - approval_rate_group_B)
print(f"Statistical parity difference: {parity_difference}")
# Investigate potential reasons for the observed difference and explore mitigation strategies.
```
```

# 2. Fairness-aware Algorithm Design (simplified example):

```
```python
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import equalized_odds_score
# Simplified model predicting loan approval based on income and group (not for real-world use)
def predict_loan_approval(income, group):
    model = LogisticRegression()
    model.fit([[income], [group]], [True, False]) # Sample training data
```
```