# Algorithm 2 The algorithm for optimizing the hyperparameters α, β, and γ.

Require: A list samples with 239 dual-entity queries, the pathfinding procedure FIND PATH, the minimize function of the Simple optimizer

```
procedure TESTCONF(α, β, γ)
  score ← 0 // lower is better
  entityLimit ← 100
  for ⟨e, e′⟩ ∈ samples do
    path, numberOfVisitedEntities ← FIND PATH(e, e′, α, β, γ, entityLimit)
    if path == ⊥ then
      score ← score + numberOfVisitedEntities × 2
    else
      score ← score + numberOfVisitedEntities
    end if
  end for
  objectiveValue ← score / |samples|
  return objectiveValue
end procedure
```

```
procedure PERFORMOPTIMIZATION
  interval ← [0.0;1.0]
  iterations ← 150
  minValue, α, β, γ ← minimize(TESTCONF, interval, iterations)
  return minValue, α, β, γ
end procedure
```

In the literature on Bayesian optimization, the recommendations for the number of iterations vary depending on factors like the number of hyperparameters and the employed acquisition function (cf. [23]). [20] reports that Simple approximates the global optimum of an objective function with two hyperparameters at about 25 iterations. Thus, generous 150 iterations are used for our problem with three hyperparameters. Since the hyperparameters α, β, and γ represent weights of the cost function components, specifying that each of them can assume a value in the interval [0.0;1.0] suffices. With respect to these settings, Algorithm 2 presents the PERFORMOPTIMIZATION procedure for optimizing the hyperparameters α, β, and γ. To this end, the procedure calls the Simple optimizer’s minimize function to minimize the objectiveValue returned by the TESTCONF procedure. Hence representing the objective function, TESTCONF accepts a candidate hyperparameter configuration and returns the average number of entities visited during pathfinding across all queries from samples using this configuration as the objectiveValue. If no path is found before the entity limit is reached, the number of visited entities is doubled as a penalty for the particular query.

Figure 2 shows the objectiveValue yielded in each iteration of the optimization process as well as the minValue, i.e., the so far smallest objectiveValue. As depicted, a good minValue is already found in the 17th iteration and no major improvements are observed until the 150th iteration. Significant improvements beyond 150 iterations are therefore not expected. The lowest minValue, i.e., 59.347, was encountered in the 101st iteration using the hyperparameter configuration

α = 0.699, β = 0.109, γ = 0.823