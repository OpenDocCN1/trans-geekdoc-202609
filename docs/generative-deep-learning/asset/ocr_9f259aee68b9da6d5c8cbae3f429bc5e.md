![](bbox=[0.15, 0.08, 0.85, 0.65])

Figure 14-7. The ControlNet architecture, with the trainable copies of the Stable Diffusion encoder blocks highlighted in blue (source: Lvmin Zhang, ControlNet)

Another advantage of Stable Diffusion is that it is able to run on a single modestly sized GPU with only 8 GB of VRAM, making it possible to run on edge devices, rather than through calls to a cloud service. As text-to-image services are included in downstream products, the speed of generation is becoming increasingly more important. This is one reason why the size of multimodal models is generally trending downward (see Figure 14-3).