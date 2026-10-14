given image/video frame causes desynchronization, which may lead to erroneous detection results. Second, PRNU calculations are often unreliable when the content in question has undergone compression.

The first limitation can be overcome by computing *normalized correlation coefficient* instead of *correlation* between test and reference PRNU (Equation 23.5). This helps neutralize the effects of mild geometric transformations.

$$\mathrm{NCC}\left(N_{\mathrm{ref}}, N_{\mathrm{test}}\right)=\frac{\left(N_{\mathrm{test}}-\overline{N_{\mathrm{test}}}\right)\cdot\left(N_{\mathrm{ref}}-\overline{N_{\mathrm{ref}}}\right)}{\sqrt{\left(N_{\mathrm{test}}-\overline{N_{\mathrm{test}}}\right)^{2}\cdot\left(N_{\mathrm{ref}}-\overline{N_{\mathrm{ref}}}\right)^{2}}$$ (23.5)

The second limitation can be overcome by modifying the noise pattern estimation process to make it more robust and effective, as explained in the following sub-section.

# 23.6.3.2 Modified Noise Pattern Estimation: SPN Based Analysis

By modifying the noise pattern estimation process, the accuracy and dependability of source camera identification techniques can be improved significantly. More specifically, instead of PRNU, we suggest working with Sensor Pattern Noise (SPN). Reference and test SPN are estimated using the same method as outlined in Equations 23.1 and 23.2; the only modifications are made to Equation 23.3, which now becomes:

$$\mathrm{SPN}_{\mathrm{ref}}=\frac{\sum_{k=1}^{N}W_{k}\bar{I}_{k}}{\sum_{k=1}^{N}\left(\bar{I}_{k}\right)^{2}}$$ (23.6)

Here, $I_k$ denotes the $k^{th}$ image or video frame and $\bar{I}_k$ is the denoised version of this image/frame; $W_k$ denotes the noise residue for the $k^{th}$ image/frame. Test SPN ($\mathrm{SPN}_{\mathrm{test}}$) is then estimated in a similar manner. (Correlation and NCC between reference and test SPN can be calculated using Equations 23.4 and 23.5, but with reference and test SPN instead of PRNU.)

As a forensic feature, SPN is quite efficacious and robust. Not only is it a unique characteristic of every digital camera, it also remains highly consistent within every image or video frame recorded by that camera. It is distributed evenly across all pixel of the image/frame, which is why it survives even the harshest of compressions. Furthermore, it remains completely unaffected by environmental conditions such as humidity and temperature variations.

*Note that in the digital visual media forensics literature, PRNU and FPN are sometimes collectively referred to as SPN. The terms PRNU and SPN are sometimes used synonymously as well.*