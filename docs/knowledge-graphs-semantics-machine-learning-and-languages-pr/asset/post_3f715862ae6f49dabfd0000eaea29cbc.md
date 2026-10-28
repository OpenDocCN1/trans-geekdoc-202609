
## Algorithm 2 The algorithm for optimizing the hyperparameters α, β, and γ.

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

![](img/5368dd329bd72fa0bf97ac91d6cef632_136_0.png)

**Figure 2.** The optimization results.

which represents the optimized hyperparameter configuration and thus the answer to RQ3. Interestingly, β is significantly lower than the other hyperparameters. This supports the assumption that leveraging semantic distances as part of the search heuristics can reduce the number of visited entities. In the course of answering RQ4, Section 5 elaborates on this point.

## 4. The Implementation: BiPaSS

Another point that needs to be addressed even though it is not directly related to the answering of the research questions is the implementation. Originally, the prototype implementing the pathfinding algorithm was written in Python²². For the present paper, a full re-implementation⁷ was produced. For future reference, we call the implementation Bidirectional Pathfinding System (BiPaSS). The new implementation uses Rust²³ for the pathfinding algorithm itself and leverages state-of-the-art data structures including a Fibonacci-heap-based priority queue. As shown in Figure 3, the implementation comprises four components. The first one is the *Query Factory* that implements the procedure from Section 3 for deriving the dual-entity query dataset from the TREC dataset. The resulting dual-entity queries are provided to the *Pathfinder* component, which contains the pathfinding algorithm as well as the code for running the hyperparameter optimization and the benchmark. For calculating the semantic distances using SBERT and all-mpnet-base-v2, it interacts with the *Wembed API* component via HTTP. For retrieving entity data from Wikidata, it interacts with the *Wikidata API* component, which is a wrapper for issuing SPARQL queries to the Wikidata Query Service, also via HTTP. The *Pathfinder*, the *Wikidata API*, and the *Wembed API* thus constitute the pathfinding system. For ease of use and reproducibility, all components are Docker-ized²⁴. Additionally, a significant number of the HTTP interactions are cached, allowing for rapid reproduction of the results despite the restrictive query limits of the Wikidata Query Service, which are responsible for the major portion of the pathfinding duration.

²² https://www.python.org (accessed 2023/05/26)
²³ https://www.rust-lang.org (accessed 2023/05/26)
²⁴ https://www.docker.com (accessed 2023/05/26)

![](img/5368dd329bd72fa0bf97ac91d6cef632_138_0.png)

**Figure 4.** The benchmark results in terms of the coverage of the test set (*n* = 957), the average number of visited entities, and the average path length. The characters on the x-axis denote the examined hyperparameter configurations: **Optimized**, **Semantics-Only**, **Balanced**, **Greedy**, and **Uninformed**.

On average. The second group, i.e., the Semantics-Only and the Greedy configuration, yield average path lengths about twice as high. Note that the members of the former group use a β value of higher than 0, whereas the members of the latter use a β value of exactly 0. This indicates that β plays a key role in controlling the path lengths.

In summary, the answer to RQ4 is as follows: The Uninformed configuration reaches a lower coverage than the configurations that consider semantic distances, thereby supporting their utility as part of the search heuristics. Given the web search engine context, the Optimized configuration represents the best option as it reaches the highest coverage of the test set with a low average of visited entities and a moderate average path length. Its high coverage also supports the assumption by [2] that limiting the algorithm to only consider outgoing edges is unproblematic. At first, the Semantics-Only configuration seems to be a competitive configuration, as well. However, the high average length of the paths found with this configuration raises doubts about their usefulness for users.

To investigate the usefulness of entity relationships, a representative user study has to be conducted in the future. The goal of this study is to deepen the understanding of the meaningfulness of entity relationships in the web search engine context and to assess to what extent the cost function and hyperparameter configurations comply with the users’ perceived meaningfulness of entity relationships. Nevertheless, to give an idea of the paths found by the different configurations, Table 4 presents a few examples. Generally, the examples conform with the quantitative results. One interesting observation is that the Semantics-Only path for Query A exhibits concept drift even though the employed configuration fully depends on semantic distances. Also, the Balanced and Uninformed configurations fail to find paths for Query B given the entity limit. The Optimized configuration produces adequately long paths that retain the semantic focus of the queries.

## 6. Conclusion

With the goal of investigating the open points of [2], the key contributions of the present paper include the improvement of the semantic distances leveraged in the pathfinding

algorithm’s cost function, the introduction of a dual-entity query dataset for pathfinding in Wikidata, the optimization of the algorithm’s three hyperparameters, and an evaluation of the algorithm on the said dataset with respect to the examined hyperparameter configurations. The provided re-implementation completes the picture.

Apart from the leads on future work mentioned above, one important point is the integration of the pathfinding algorithm in an end-to-end application where dual-entity queries can be entered, upon which the pathfinder is issued, such that a knowledge panel explaining the relationship between the query entities can be generated and finally be displayed. In this regard, it has to be investigated which kind of presentation yields the best user experience. For instance, an actual text describing the relationship could be generated using natural language generation techniques based on the found paths. At the same time, graph-based visualizations are conceivable, as well.

Instead of adopting the cost function introduced in [2], one could investigate alternative cost functions that also take the meaning of the predicates into account. Intuitively, predicates that express taxonomic relations might be more accessible for non-expert users than more specialized predicates.

Finally, a point raised in [2] should also be repeated here, namely how multi-entity queries that mention more than two entities could be served. While the obvious option is to simply issue a pathfinder between all pairs of entities and concatenate the resulting paths, an approach that tries to identify an entity that connects the query entities with minimal global concept drift is also conceivable, for example.

## Table 4. Examples of paths found using the five hyperparameter configurations. For conciseness, the predicates have been left out.

| Configuration | Path found for Query A (Q7958 (explanation), Q46857 (scientific method)) |
|---|---|
| Optimized | Q7958 (explanation) → Q352842 (teaching) → Q11862829 (academic discipline) ← Q336 (science) ← Q46857 (scientific method) |
| Semantics-Only | Q7958 (explanation) → Q352842 (teaching) → Q133500 (learning) → Q14819853 (learning or memory) → Q2996394 (biological process) → Q64732777 (biological phenomenon) → Q420 (biology) → Q7205 (paleontology) → Q1069 (geology) → Q7991 (natural science) → Q2522419 (hard science) → Q336 (science) ← Q46857 (scientific method) |
| Balanced | Q7958 (explanation) → Q352842 (teaching) → Q11862829 (academic discipline) ← Q336 (science) ← Q46857 (scientific method) |
| Greedy | Q7958 (explanation) → Q352842 (teaching) → Q11862829 (academic discipline) → Q336 (science) → Q46857 (scientific method) |
| Uninformed | Q7958 (explanation) → Q151885 (concept) → Q5891 (philosophy) ← Q1799072 (method) ← Q46857 (scientific method) |
| Configuration | Path found for Query B (Q81938 (pain), Q482853 (vertebral column)) |
|---|---|
| Optimized | Q81938 (pain) → Q408801 (celecoxib) → Q52849 (ankylosing spondylitis) → Q7577457 (spinal disease) → Q1979420 (human vertebral column) → Q482853 (vertebral column) |
| Semantics-Only | Q81938 (pain) → Q169872 (symptom) ← Q12136 (disease) ← Q1595418 (remedy) ← Q179661 (treatment) ← Q701216 (pharmacotherapy) ← Q12140 (medication) ← Q11190 (medicine) ← Q514 (anatomy) ← Q515083 (extremities) ← Q62513663 (lower limb) ← Q6027402 (human leg) ← Q23852 (human body) ← Q5170145 (core) ← Q160695 (torso) ← Q133279 (back) ← Q482853 (vertebral column) |
| Balanced | No path could be found within the entity limit. |
| Greedy | Q81938 (pain) → Q898407 (venlafaxine) → Q410142 (solute carrier family 6 member 4) → Q14330969 (brain development) → Q1073 (brain) → Q28947902 (cranium) → Q13147 (skull) → Q1377526 (axial skeleton) → Q482853 (vertebral column) |
| Uninformed | No path could be found within the entity limit. |
