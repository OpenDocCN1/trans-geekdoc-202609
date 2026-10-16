```
In [9]:

def best_model_hyper_params(make_a_model,
                            some_hyper_params,
                            data):
    results = {}
    for hyper_params in it.combinations(some_hyper_params):
        for train,test in make_cv_split(data):
            model = make_a_model(*hyper_params).fit(train)
            key = tuple(hyper_params)
            if key not in results:
                results[key] = []
            results[key].append(score(test, model.predict(test)))
            # or, rock stars can use this instead of the prior 4 lines:
            # (results.setdefault(tuple(hyper_params), [])
            #     .append(score(test, model.predict(test)))

    best_hp = max(results, key=results.get)
    best_model = make_a_model(*best_hp).fit(data)
    return best_model

def do_it():
    model = pick_a_model  # e.g., k-NN

    some_hyper_params = [values_for_hyper_param_1, # e.g., n_neighbors=[]
                         values_for_hyper_param_2,
                         values_for_hyper_param_3]

    best_model_hyper_params(model_type,
                            some_hyper_params,
                            data)
```

Fortunately, evaluating over hyperparameters is a common task in designing and building a learning system. As such, we don’t have to code it up ourselves. Let’s say we want to try all combinations of these hyperparameters:

| Hyperparameter | Values |
|---|---|
| n_neighbors | 1, ..., 10 |
| weights | uniform, distance |
| p | 1, 2, 4, 8, 16 |

Two notes:

+   1. *distance* means that my neighbor’s contribution is weighted by its distance from *me*. *uniform* means all my neighbors are considered the same with no weighting.