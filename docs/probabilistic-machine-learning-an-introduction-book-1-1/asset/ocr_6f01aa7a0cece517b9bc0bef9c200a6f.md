# Chapter 14. Neural networks for images

![](bbox=[0.02, 0.12, 0.98, 0.32])

![](bbox=[0.02, 0.35, 0.98, 0.55])



The DeepDream system in Fig. 14.32 shows one way that CNNs can be used to create “art”. However, it is rather creepy. In this section, we discuss a related approach that gives the user more control. In particular, the user has to specify a reference “style image” x_s and “content image” x_c. The system will then try to generate a new image x that “re-renders” x_c in the style of x_s. This is called neural style transfer, and is illustrated in Fig. 14.33. This was first proposed in [GEB16], and there are now many papers on this topic; see [Jin+17] for a recent review.



Style transfer works by optimizing the following energy function:

```
L(x|x_s, x_c) = λ_TV L_TV(x) + λ_c L_content(x, x_c) + λ_s L_style(x, x_s)
(14.26)
```

See Fig. 14.34 for a high level illustration.

The first term in Eq. (14.26) is the total variation prior discussed in Sec. 14.5.2.2. The second term measures how similar x is to x_c by comparing feature maps of a pre-trained CNN φ(x) in the ...