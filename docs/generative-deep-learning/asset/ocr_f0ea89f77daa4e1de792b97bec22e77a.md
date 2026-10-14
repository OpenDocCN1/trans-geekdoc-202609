of the text prompt, missing key information such as the calculator. Using the text embedding as if it were an image embedding performs slightly better, though it is not able to capture the relationship between the hedgehog and the calculator. Only the full model with the prior produces an image that accurately reflects all of the information contained within the prompt.

![](bbox=[0.16, 0.19, 0.82, 0.66])

Figure 13-15. The prior provides the model with additional context and helps the decoder to produce more accurate generations (source: Ramesh et al., 2022)

# Limitations

In the DALL.E 2 paper, the authors also highlight several known limitations of the model. Two of these (attribute binding and text generation) are shown in Figure 13-16.