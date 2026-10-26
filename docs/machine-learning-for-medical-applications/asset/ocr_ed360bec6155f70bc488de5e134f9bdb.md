![](bbox=[0.106, 0.099, 0.349, 0.427])

**Figure 10:** Image registration.

Demons algorithm: Based on the mathematical equations, it adapts the alignment in a continual process by reducing the distance between the images.

Here we provide the basic knowledge about image registration and then describe its several applications.

Image registration is widely used across various medical imaging applications:

+   - **Multimodal imaging:** Fuses MRI, CT, and PET imaging to see the more detail and functional and anatomical data of the body.
+   - **Longitudinal studies:** Stretches acquired images to analyze the development of diseases, reaction to treatment, or changes following surgery.
+   - **Surgical planning and navigation:** Improves preoperative imaging by positioning it in parallel to intraoperative images to provide accurate direction in the surgery.
+   - **Image fusion:** Overlays anatomic images into one frame enhancing diagnostic accuracy since both modalities provide information that the other cannot provide.

Image registration remains a problem even in situations where images are taken from approximately the same viewpoint with minor changes done to the camera position.

Despite its importance, image registration poses several challenges:

+   - **Variability in image quality:** Getting variation on the image resolution, noise level, as well as contrast differences of the image will determine the registration accuracy.
+   - **Presence of artifacts:** Distortions and motions are some of the artifacts that hinder the alignment process and that can only be corrected through some methods.
+   - **Computational complexity:** Nonrigid registration algorithms are in general computationally expensive, thus consuming high computing power and time.