```
#effect_modifiers=['W','r', 'L','fc','C','P', 'K']
)
model.view_model()
from IPython.display import Image, display
display(Image(filename="causal_model.png"))
#Identify
identified_estimand = model.identify_effect(proceed_when_unidentifiable=True)
print(identified_estimand)

#Estimate using Linear Regression
#Estimate the causal effect and compare it with Average Treatment Effect
estimate = model.estimate_effect(identified_estimand,
method_name="backdoor.linear_regression", test_significance=True
)
print(estimate)

#Refute
#Random Common Cause – add an independent random variable as a common cause to the
dataset; If the assumption was correct, the estimation should not change.
refute_results=model.refute_estimate(identified_estimand, estimate,
method_name="random_common_cause")
print(refute_results)

#Data Subset Refuter – replace the given dataset with a randomly selected subset;
If the assumption was correct, the estimation should not change that much.**
res_subset=model.refute_estimate(identified_estimand, estimate,
method_name="data_subset_refuter", subset_fraction=0.9)
print(res_subset)

#Placebo Treatment – replace the true treatment variable with an independent random
variable; If the assumption was correct, the estimate should go close to zero.
res_placebo=model.refute_estimate(identified_estimand, estimate,
method_name="placebo_treatment_refuter", placebo_type="permute")
print(res_placebo)

#Model:Isolated Model
causal_graph = """digraph {
W->T;
T->Y;
}"""

from dowhy import CausalModel
model=CausalModel(
data = df,
treatment='T',
outcome='Y',
#common_causes=['K'],
graph=causal_graph.replace("\n", " "),
#instruments=['C'],
#effect_modifiers=['W','r', 'L','fc','C','P', 'K']
)
model.view_model()
from IPython.display import Image, display
display(Image(filename="causal_model.png"))
```