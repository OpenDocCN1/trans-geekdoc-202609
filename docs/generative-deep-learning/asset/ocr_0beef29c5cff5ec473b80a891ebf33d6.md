# Architecture

The overall architecture of Flamingo is shown in Figure 13-22. For conciseness, we shall explore the core components of this model—the Vision Encoder, the Perceiver Resampler, and the Language Mode—in just enough detail to highlight the key ideas that make Flamingo unique. I highly recommend reading the original research paper for a thorough review of each part of the model.

![](bbox=[0.19, 0.22, 0.85, 0.65])

Figure 13-22. The Flamingo architecture (source: Alayrac et al., 2022)

# The Vision Encoder

The first difference between a Flamingo model and pure text-to-image models such as DALL.E 2 and Imagen is that Flamingo can accept a combination of text and visual data interleaved. Here, visual data includes videos as well as images.