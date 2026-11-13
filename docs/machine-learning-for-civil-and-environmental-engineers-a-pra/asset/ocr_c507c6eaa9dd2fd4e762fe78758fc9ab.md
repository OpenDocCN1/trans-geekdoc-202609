![](bbox=[0.1, 0.09, 0.56, 0.3])

# Figure 7.5 Comparison between models in terms of feature importance in regression.

zero ($f_c$, $f_y$, and $T$). The other two models also rely on $a$, and have noted the importance of all features with varying magnitudes.49

Let us now also compare the PDP50 for the features as calculated by the three models. Figure 7.6 illustrates three PDPs comprising moment arm, reinforcement, and FRP ratios.51 As you can see, the influence of the moment arm is significant52 in predicting the moment capacity when compared to the reinforcement and FRP ratios.

For example, larger moment arms beyond 800 mm, 1400 mm, and 1600 mm tend to generate higher moments, hence the possible reasoning for Keras, Decision Tree Regressor, and the Generalized Additive Model of tying this feature with larger values of moment capacity.53 Furthermore, smaller moment arms of less than 800 mm do not affect moment capacity

![](bbox=[0.1, 0.49, 0.5, 0.73])

49 What can we learn from such analysis? Well, we can clearly see that ML models may or may not agree on the importance of features (despite having very close performance and goodness)! In addition, I would say that it is worth investigating re-occurring features between models such as a, r, and f if you happen to be surprised the fy was not as important as you have thought, here is what to do. Go back to the dataset and see the ranges of this parameter. It is evident that most of the collected beams had ranges that resemble normal strength concrete (average 43.2 MPA) with a few beams of higher strength. In other words, there were not many beams with drastically different fc that could have warranted a higher importance.

50 Remember that a PDP depicts the marginal effect of an individual feature on the prediction of the model while maintaining all other features constant [15].

51 Calculated as the ratio of the cross sectional area of the FRP to the cross sectional area of concrete.

52 This can be seen by the range of the vertical axis in the PDP for a, as opposed for r or f. Key features tend to have a large span of influence.

53 This also agrees with domain knowledge! The reader is reminded that from a structural engineering perspective, a larger moment arm is expected to generate a higher bending moment (for identical beams and simply supported beams).