click STEP for the above sign program. When the new window comes up, click the right and left arrows there.

That is, a conditional expression consists of as many *conditional lines* as needed. Each line contains two expressions: the left one is often called *condition*, and the right one is called *result*; occasionally we also use *question* and *answer*. To evaluate a cond expression, DrRacket evaluates the first condition expression, *ConditionExpression1*. If this yields #true, DrRacket replaces the cond expression with *ResultExpression1*, evaluates it, and uses the value as the result of the entire cond expression. If the evaluation of *ConditionExpression1* yields #false, DrRacket drops the first line and starts over. In case all condition expressions evaluate to #false, DrRacket signals an error.

With this knowledge, you can now change the course of the simulation. The goal is to not let the rocket descend below the ground level of a 100-by-60 scene. Since the *picture-of-rocket* function consumes the height where it should place the rocket in the scene, a simple test comparing the given height to the maximum height appears to suffice.

See figure 5 for the revised function definition. The definition uses the name *picture-of-rocket.v2* to distinguish the two versions. Using distinct names also allows us to use both functions in the interactions area and to compare the results. Here is how the original version works:

```
> (picture-of-rocket 5555)
```

![](bbox=[0.138, 0.606, 0.305, 0.685])

```
(define (picture-of-rocket.v2 height)
  (cond
    [(<= height 60)
     (place-image
      [rocket icon]
      50 height
      (empty-scene 100 60))]
    [(> height 60)
     (place-image
      [rocket icon]
      50 60
      (empty-scene 100 60))]))
```