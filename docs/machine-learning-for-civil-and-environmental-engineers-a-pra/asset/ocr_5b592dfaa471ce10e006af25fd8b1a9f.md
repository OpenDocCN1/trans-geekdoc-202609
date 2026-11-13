Since the first functional form matches the ground truth, we could further explore answers to causal principles outlined by the Pearian approach (e.g., association → intervention → counterfactuals). Table 9.5 lists such questions and answers.

You could argue that the above example and derived function could be a reflection of the simplicity of the sectional capacity phenomenon. As in, there were only two features Z and fy, wherein fy is reduced to two re-occurring values (36 ksi and 50 ksi). I would agree with you. In fact, having this example serves two purposes: 1) a good introductory problem, and 2) brings the practical aspect where W-shaped structural steel sections are primarily fabricated using two grades of steel – for the most part (which influences how feature importance looks down on fy137). I will be offering a problem at the end of this chapter to extend this example into multi-steel grades to inflate the number of data points. I feel that this would be a good homework problem to showcase the influence of data size and domain accepted practices on ML models/mapping function predictions.

To complement this case study, an effort is introduced to add a new layer of complexity by breaking down the plastic modulus Z into its basic components, i.e., depth, d, flange width, bf, flange thickness, tf, and web thickness, tw. Our goal is to repeat the above analysis to see if we can arrive at the ground truth relationship between Z and its components (shown in Equation 9.7). Thus, the same dataset is extended by substituting Z with its basic components. We finally arrive at Equation 9.8.138

```
M = f_y \times (b_f t_f (d - t_f) + 0.25 t_w (d - 2t_f)^2) \quad (9.14)
```

```
M = 6.24 d t_f f_y + 0.494 d b_f t_w f_y + 0.0194 b_f t_f f_y d^2 - 0.063 t_w t_f f_y d^2 \quad (9.15)
```

![](bbox=[0.13, 0.41, 0.46, 0.615])

![](bbox=[0.525, 0.41, 0.885, 0.625])

![](bbox=[0.13, 0.645, 0.46, 0.835])

# Figure 9.17 Feature importance (top), and PD plots for Z (middle) and fy (bottom) from ensemble vs. Mapping function (Equation 9.11).139

137 Remember this is an explainability tool that is based on data! Not domain knowledge!

138 We are a few generations away from getting a close match to the ground truth! Another good homework problem.

139 The axes were normalized since each feature has a different scale.