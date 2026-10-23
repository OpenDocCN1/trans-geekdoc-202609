```
```text
2 0.482379 0.359907 0.898292 01:31
3 0.444970 0.332607 0.904825 01:31
4 0.341876 0.304116 0.915506 01:31
```
```

We see that we aren’t overfitting because the validation errors continue to go down. With Unet models the first epochs lasts a bit longer than the following ones.

As always we save our model to be able to come back later.

```
```python
learner.save('stage-1')
Path('models/stage-1.pth')
learner.load('stage-1')
```
```

Now have a look at how well our learner did on the segmentation task. On the left there are the target (y) values and on the right is the image our learner created

```
```python
learner.show_results(max_n=4, figsize=(12,6))
```
```

![](bbox=[0.125, 0.481, 0.876, 0.86])

Next we can unfreeze our model and continue training. Typically you have to