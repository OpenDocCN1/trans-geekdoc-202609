
# Experiment No. 3

**AIM:** Write a program to demonstrate the working of the decision tree-based ID3 algorithm. Use an appropriate data set for building the decision tree and apply this knowledge to classify a new sample.

## ID3 Algorithm

```text
ID3 (Examples, Target attribute, Attributes)
```

- **Examples** are the training examples.
- **Target attribute** is the attribute whose value is to be predicted by the tree.
- **Attributes** is a list of other attributes that may be tested by the learned decision tree.
- Returns a decision tree that correctly classifies the given examples.

### Algorithm Steps

1. Create a Root node for the tree.
2. If all examples are positive, return the single-node tree root, with label = `+`.
3. If all examples are negative, return the single-node tree root, with label = `-`.
4. If attributes are empty, return the single-node tree root, with label = most common value of target attribute in examples.
5. Otherwise, begin:
   - `A` ← the attribute from attributes that best* classifies examples.
   - The decision attribute for root ← `A`.
   - For each possible value, `v`, of `A`:
     - Add a new tree branch below corresponding to the test `A = v`.
     - Let `Examples_v` be the subset of examples that have value `v` for `A`.
     - If `Examples_v` is empty:
       - Then below this new branch add a leaf node with label = most common value of target attribute in examples.
     - Else below this new branch add the subtree `ID3(Examples_v, Target attribute, Attributes – {A})`.
6. Return Root.

The best attribute is the one with the highest information gain.

## Training Dataset: `ML3.CSV`

![Dataset](image-bd7zu3of.jpg)

## Program

```python
import pandas as pd

df = pd.read_csv("ML3.CSV")  # Input Data Set
t = "Answer"  # Target Attribute is: t
attribute_names = list(df.keys())
attribute_names.remove(t)  # Predicting Attributes: attribute_names

import math

def entropy(probs):
    return sum([-prob * math.log(prob, 2) for prob in probs])

def entropy_of_list(a_list, classes):
    from collections import Counter
    cnt = Counter(x for x in a_list)  # Counter calculates the proportion of class
    total_instances = sum(cnt.values())  # no of instances/records associated with {0} is:
    probs = [x / total_instances for x in cnt.values()]  # x means no of YES/NO
    return entropy(probs)  # Call Entropy

def information_gain(df, split_attribute, target_attribute, default_attr):
    df_split = df.groupby(split_attribute)  # group the data based on attribute values
    glist = []
    for gname, group in df_split:
        glist.append(gname)  # Attribute Values
    glist.reverse()
    nobs = len(df.index) * 1.0
    df_agg = df_split.agg({target_attribute: [entropy_of_list, lambda x: len(x) / nobs]})
    df_agg.columns = ['Entropy', 'PropObservations']
    new_entropy = sum(df_agg['Entropy'] * df_agg['PropObservations'])
    old_entropy = entropy_of_list(df[target_attribute], default_attr)
    return old_entropy - new_entropy

def id3(df, target_attribute, attribute_names, default_class=None, parent_attr=None):
    from collections import Counter
    cnt = Counter(x for x in df[target_attribute])  # class of YES /NO

    ## First check: Is this split of the dataset homogeneous?
    if len(cnt) == 1:
        return next(iter(cnt))  # next input data set, or raises StopIteration when EOF is hit.

    ## Second check: Is this split of the dataset empty? if yes, return a default value
    elif df.empty or (not attribute_names):
        return default_class  # Return None for Empty Data Set

    ## Otherwise: This dataset is ready to be divided up!
    # Get Default Value for next recursive call of this function:
    default_class = max(cnt.keys())  # No of YES and NO Class

    # Compute the Information Gain of the attributes:
    gainz = []
    for attr in attribute_names:
        ig = information_gain(df, attr, target_attribute, default_class)
        gainz.append(ig)
        print(f"Gain of {attr} is : {ig}")

    index_of_max = gainz.index(max(gainz))  # Index of Best Attribute
    best_attr = attribute_names[index_of_max]  # Choose Best Attribute to split on
    print(f"Attribute with the maximum gain is: {best_attr}")

    # Create an empty tree, to be populated in a moment
    tree = {best_attr: {}}  # Initiate the tree with best attribute as a node
    remaining_attribute_names = [i for i in attribute_names if i != best_attr]

    # Split dataset-On each split, recursively call this algorithm.Populate the empty tree with subtrees, which
    # are the result of the recursive call
    for attr_val, data_subset in df.groupby(best_attr):
        subtree = id3(data_subset, target_attribute, remaining_attribute_names, default_class, best_attr)
        tree[best_attr][attr_val] = subtree
    return tree

from pprint import pprint
tree = id3(df, t, attribute_names)
print("Resultant Decision Tree")
pprint(tree)

def classify(instance, tree, default=None):
    attribute = next(iter(tree))  # Outlook/Humidity/Wind
    if instance[attribute] in tree[attribute].keys():  # Value of the attribute in set of Tree keys
        result = tree[attribute][instance[attribute]]
        if isinstance(result, dict):  # this is a tree, delve deeper
            return classify(instance, result)
        return result  # this is a label
    return default
```

## Output

**Input Data Set is:**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| sunny | hot | high | weak | no |
| overcast | hot | high | weak | yes |
| rain | mild | high | weak | yes |
| rain | cool | normal | weak | yes |
| rain | cool | normal | strong | no |

**Target Attribute is:** `Answer`
**Predicting Attributes:** `['Outlook', 'Temperature', 'Humidity', 'Wind']`

### Information Gain Calculation of `Outlook`

**Grouped Attribute Values (overcast):**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| overcast | hot | high | weak | yes |

**Grouped Attribute Values (rain):**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | mild | high | weak | yes |
| rain | cool | normal | weak | yes |
| rain | cool | normal | strong | no |

**Grouped Attribute Values (sunny):**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| sunny | hot | high | weak | no |

- Target attribute class count(Yes/No)= `{'yes': 1}`
- Total no of instances/records associated with `overcast` is: `1`
- Probability of Class `yes` is: `1.0000`
- Target attribute class count(Yes/No)= `{'yes': 2, 'no': 1}`
- Total no of instances/records associated with `rain` is: `3`
- Probability of Class `no` is: `0.3333`
- Probability of Class `yes` is: `0.6667`
- Target attribute class count(Yes/No)= `{'no': 1}`
- Total no of instances/records associated with `sunny` is: `1`
- Probability of Class `no` is: `1.0000`
- Target attribute class count(Yes/No)= `{'no': 2, 'yes': 3}`
- Total no of instances/records associated with `S` is: `5`
- Probability of Class `no` is: `0.4000`
- Probability of Class `yes` is: `0.6000`
- **Information gain of `Outlook` is : `0.4199730940219749`**

### Information Gain Calculation of `Temperature`

**Grouped Attribute Values (cool):**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | cool | normal | weak | yes |
| rain | cool | normal | strong | no |

**Grouped Attribute Values (hot):**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| sunny | hot | high | weak | no |
| overcast | hot | high | weak | yes |

**Grouped Attribute Values (mild):**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | mild | high | weak | yes |

- Target attribute class count(Yes/No)= `{'yes': 1, 'no': 1}`
- Total no of instances/records associated with `cool` is: `2`
- Probability of Class `no` is: `0.5000`
- Probability of Class `yes` is: `0.5000`
- Target attribute class count(Yes/No)= `{'no': 1, 'yes': 1}`
- Total no of instances/records associated with `hot` is: `2`
- Probability of Class `no` is: `0.5000`
- Probability of Class `yes` is: `0.5000`
- Target attribute class count(Yes/No)= `{'yes': 1}`
- Total no of instances/records associated with `mild` is: `1`
- Probability of Class `yes` is: `1.0000`
- Target attribute class count(Yes/No)= `{'no': 2, 'yes': 3}`
- Total no of instances/records associated with `S` is: `5`
- Probability of Class `no` is: `0.4000`
- Probability of Class `yes` is: `0.6000`
- **Information gain of `Temperature` is : `0.17095059445466854`**

### Information Gain Calculation of `Humidity`

**Grouped Attribute Values (high):**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| sunny | hot | high | weak | no |
| overcast | hot | high | weak | yes |
| rain | mild | high | weak | yes |

**Grouped Attribute Values (normal):**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | cool | normal | weak | yes |
| rain | cool | normal | strong | no |

- Target attribute class count(Yes/No)= `{'no': 1, 'yes': 2}`
- Total no of instances/records associated with `high` is: `3`
- Probability of Class `no` is: `0.3333`
- Probability of Class `yes` is: `0.6667`
- Target attribute class count(Yes/No)= `{'yes': 1, 'no': 1}`
- Total no of instances/records associated with `normal` is: `2`
- Probability of Class `no` is: `0.5000`
- Probability of Class `yes` is: `0.5000`
- Target attribute class count(Yes/No)= `{'no': 2, 'yes': 3}`
- Total no of instances/records associated with `S` is: `5`
- Probability of Class `no` is: `0.4000`
- Probability of Class `yes` is: `0.6000`
- **Information gain of `Humidity` is : `0.01997309402197489`**

### Information Gain Calculation of `Wind`

**Grouped Attribute Values (strong):**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | cool | normal | strong | no |

**Grouped Attribute Values (weak):**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| sunny | hot | high | weak | no |
| overcast | hot | high | weak | yes |
| rain | mild | high | weak | yes |
| rain | cool | normal | weak | yes |

- Target attribute class count(Yes/No)= `{'no': 1}`
- Total no of instances/records associated with `strong` is: `1`
- Probability of Class `no` is: `1.0000`
- Target attribute class count(Yes/No)= `{'no': 1, 'yes': 3}`
- Total no of instances/records associated with `weak` is: `4`
- Probability of Class `no` is: `0.2500`
- Probability of Class `yes` is: `0.7500`
- Target attribute class count(Yes/No)= `{'no': 2, 'yes': 3}`
- Total no of instances/records associated with `S` is: `5`
- Probability of Class `no` is: `0.4000`
- Probability of Class `yes` is: `0.6000`
- **Information gain of `Wind` is : `0.3219280948873623`**

**Attribute with the maximum gain is:** `Outlook`

### Information Gain Calculation of `Temperature` (Subtree for `rain`)

**Grouped Attribute Values (cool):**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | cool | normal | weak | yes |
| rain | cool | normal | strong | no |

**Grouped Attribute Values (mild):**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | mild | high | weak | yes |

- Target attribute class count(Yes/No)= `{'yes': 1, 'no': 1}`
- Total no of instances/records associated with `cool` is: `2`
- Probability of Class `no` is: `0.5000`
- Probability of Class `yes` is: `0.5000`
- Target attribute class count(Yes/No)= `{'yes': 1}`
- Total no of instances/records associated with `mild` is: `1`
- Probability of Class `yes` is: `1.0000`
- Target attribute class count(Yes/No)= `{'yes': 2, 'no': 1}`
- Total no of instances/records associated with `S-rain` is: `3`
- Probability of Class `no` is: `0.3333`
- Probability of Class `yes` is: `0.6667`
- **Information gain of `Temperature` is : `0.2516291673878229`**

### Information Gain Calculation of `Humidity` (Subtree for `rain`)

**Grouped Attribute Values (high):**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | mild | high | weak | yes |

**Grouped Attribute Values (normal):**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | cool | normal | weak | yes |
| rain | cool | normal | strong | no |

- Target attribute class count(Yes/No)= `{'yes': 1}`
- Total no of instances/records associated with `high` is: `1`
- Probability of Class `yes` is: `1.0000`
- Target attribute class count(Yes/No)= `{'yes': 1, 'no': 1}`
- Total no of instances/records associated with `normal` is: `2`
- Probability of Class `no` is: `0.5000`
- Probability of Class `yes` is: `0.5000`
- Target attribute class count(Yes/No)= `{'yes': 2, 'no': 1}`
- Total no of instances/records associated with `S-rain` is: `3`
- Probability of Class `no` is: `0.3333`
- Probability of Class `yes` is: `0.6667`
- **Information gain of `Humidity` is : `0.2516291673878229`**

### Information Gain Calculation of `Wind` (Subtree for `rain`)

**Grouped Attribute Values (strong):**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | cool | normal | strong | no |

**Grouped Attribute Values (weak):**

| Outlook | Temperature | Humidity | Wind | Answer |
| :--- | :--- | :--- | :--- | :--- |
| rain | mild | high | weak | yes |
| rain | cool | normal | weak | yes |

- Target attribute class count(Yes/No)= `{'no': 1}`
- Total no of instances/records associated with `strong` is: `1`
- Probability of Class `no` is: `1.0000`
- Target attribute class count(Yes/No)= `{'yes': 2}`
- Total no of instances/records associated with `weak` is: `2`
- Probability of Class `yes` is: `1.0000`
- Target attribute class count(Yes/No)= `{'yes': 2, 'no': 1}`
- Total no of instances/records associated with `S-rain` is: `3`
- Probability of Class `no` is: `0.3333`
- Probability of Class `yes` is: `0.6667`
- **Information gain of `Wind` is : `0.9182958340544896`**

**Attribute with the maximum gain is:** `Wind`

## Resultant Decision Tree

```python
{'Outlook': {'overcast': 'yes',
  'rain': {'Wind': {'strong': 'no', 'weak': 'yes'}},
  'sunny': 'no'}}
```
