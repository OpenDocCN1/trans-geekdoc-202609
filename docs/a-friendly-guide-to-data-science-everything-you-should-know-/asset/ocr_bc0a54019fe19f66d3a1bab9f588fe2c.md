![](bbox=[0.258, 0.118, 0.772, 0.439])

Figure 15-19. Data with an overfitted model

It’s not hard to see that this model is weird and likely wrong. Let’s say new points come in to be classified, as shown in Figure 15-20. This shows two new data points with the correct class marked in the center of a green ring. But because these are just in the wrong spots within the circuitous decision boundary, they will be misclassified. The new red point that’s near many other red points will be marked blue, and the new blue point that’s right next to a correctly classified blue point will be marked red. It’s pretty clear that this isn’t what we want out of a model.