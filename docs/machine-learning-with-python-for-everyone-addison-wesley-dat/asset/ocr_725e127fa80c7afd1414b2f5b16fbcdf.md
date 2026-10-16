```
svm_ftrs = logreg_ftrs_p1
svm_tgt = binary_to_pm1(logreg_tgt)  # svm "demands" +/- 1

# svm model is "just" rdot, so we don't define it separately now
svc_cost = make_cost(svm_ftrs, svm_tgt, rdot,
                    hinge_loss, 0.0, no_penalty)
learned_weights = magical_minimum_finder(svc_cost, [5,5], disp=False)

preds = predict_with_svm_weights(learned_weights, svm_ftrs)
print('no penalty accuracy:',
      metrics.accuracy_score(preds, svm_tgt))
```

no penalty accuracy: 0.91

As we did with linear and logistic regression, we can add a penalty term to control the weights.

```
# svc with penalty
svc_pen_cost = make_cost(svm_ftrs, svm_tgt, rdot,
                    hinge_loss, 1.0, L1_penalty)
learned_weights = magical_minimum_finder(svc_pen_cost, [5,5], disp=False)

preds = predict_with_svm_weights(learned_weights, svm_ftrs)
print('accuracy with penalty:',
      metrics.accuracy_score(preds, svm_tgt))
```

accuracy with penalty: 0.91

Now would be a great time to give you a warning. We are using trivial true relationships with tiny amounts of easy-to-separate data. You shouldn't expect to use scipy.optimize.fmin for real-world problems. With that warning set aside, here's a cool way to think about the optimization that is performed by the techniques you would use. From this perspective, when you use SVM, you are simply using a nice custom optimizer that works well for SVM problems. The same thing is true for linear and logistic regression: some ways of optimizing—finding the minimum cost parameters—work well for particular learning methods, so under the hood we use that method! In reality, customized techniques can solve specific optimization problems—such as those we need to solve when we fit a model—better than generic techniques like fmin. You usually don't have to worry about it until you start (1) using the absolute latest learning methods that are coming out of research journals or (2) implementing customized learning methods yourself.

One quick note. In reality, we didn't actually get to the kernelized version that takes us from SVCs to SVMs. Everything is basically the same, except we replace our dot products with kernels.