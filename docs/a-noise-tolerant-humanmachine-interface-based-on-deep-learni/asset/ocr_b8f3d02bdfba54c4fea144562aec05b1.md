# Article

https://doi.org/10.1038/s41468-025-00001-3

All superimposed signals used in the dataset were unique and non-repetitive (which accommodates variability in both signals and motion), preventing the model from overestimating recurring patterns.

In addition, to reduce the orientation differences between superimposed motions and the gesture signals collected during different motion aspects (gestures used for training), we adopted two measures: first, during the training, we maintained a palm-down posture, matching the orientation used during real-world gesture execution. Second, we filtered the baseline component from the acceleration in motion before preprocessing (note that accelerometers have gravity bias), which reduces the orientation disparity; thereby aligning the superimposed signals with real world gesture signals collected under motions.

MATLAB was used for TCP/IP communication (Supplementary Fig. 27). In demonstrations, the beaker was at a fixed location to ensure comparison of gesture used under different motion aspects, and the robotic arm could operate anywhere within the workspace.

# Collection of superimposed sea waves

We generated superimposed waves in an enclosed atmosphere and monitored the wave characteristics using the Scripps-Ocean Research Simulator (Fig. 5b and Supplementary Fig. 30). Throughout the data acquisition, the sensors remained afloat on the water surface, which emitted a dliver wave with a paddle, with the frequency adjusted to vary wavelength (Supplementary

# Reporting

Further information on this research is available in the Nature Research Report Linking to this article.

# Process for training learning

For training, we collected data from 6 subjects (5 males and 1 female, aged 21 to 34) with different motion speeds and forearm lengths (40-50 cm). The data from five individuals were used to train the CNN, while the sixth was used for fine-tuning. During the testing phase, we used the CNN to determine the output. Notably, 100 sequences were randomly selected to evaluate the performance of the CNN (Fig. 3c and Extended Data Fig. 5). This cross-validation approach separates training and testing, preventing any data leakage during the process.

# Data availability

The material and resources supporting this findings are available upon request. The raw data can be found in the Source Data files. Source data are provided with this paper.

# Code availability

The codes used in gesture recognition and transfer learning are found in a publicly accessible repository (https://github.com/zIou/mm/main).

# Generation of the generated signals

# References

Each superimposed signal was generated for 19 superimposed gestures (including both identical and different gestures), which produced 342 concatenated signals (19 superimposed signals with 8 cm of motion for setting or lowering gestures). For each gesture, a randomly weighted segment was concatenated into segments, yielding a total of 2,280 segmented motions with signals (Fig. 3F, Extended Data Fig. 6 and Supplementary Fig. 4).

In total, 2,470 signals were generated per gesture, comprising 95 superimposed signals and 95 from lying down without motion, 2,280 segmented motions with signals. Across all 19 gestures, a total of 46,930 signals were generated per iteration. The dataset was split into training, validation and testing sets at a ratio of 70%:15%:15%. Performance was evaluated across 15 independent runs.

+   1. Simponatto, J. R., et al. An epidermal pathway for the monitoring of hemodynamics and metabolic biomarkers. Nat. Bio, 55, 738-745 (2023)

+   2. Wang, X., et al. Continuous monitoring of deep-tissue hemodynamics with ultrasonic phased arrays. Nat. Eng, 5, 749-758 (2018)

+   3. Zhang, J., et al. Smart soft contact lenses for monitoring of intracranial pressure in glaucoma case. Conn. Ophthalmol., 12, e02110 (2022).

+   4. Manassak, L., Lin, N., Lennon, A., Wang, J., & Dahlin, R. Energy harvesting autonomous sweat-based wearable sensors. Nat. Mater., 33, 1009-9 (2020).

# Control of the robot

To ensure sensor orientation, the individual maintained a palm-down orientation during the robotic control. This was necessary because six gestures involved the palm (that, is, wrist rotation). Maintaining a constant orientation minimized motion artifacts caused by gravity.

IMU and EMG data from the wearables were sent to a USB receiver and processed by MATLAB on a computer. The segmented CNN signals were generated using a sliding window (25 ms step) and then sent to an online CNN in Python. The model was chosen after three consecutive independent predictions, and the predicted results were sent back to MATLAB to control the robotic arm, which executed commands within the desired state. In addition, the EMGs were acquired and filtered in MATLAB to control the grasping of the robotic gripper based on the RMS values. The communication between Python and

+   5. Gao, W., et al. Fully integrated wearable sensors for sensing and harvest. Nat. Nature, 529, 509-514 (2019)

+   6. Li, C., et al. Wearable-smart electronics for wrist sensing and harvesting. Nat. Human Interact, 7, 13319 (2021)

+   7. Liu, R., Wang, Z., Fukuda, K., & Seymour, M. Flexible soft-power sensors for wearable. Nat. Mater., 7, 870-886 (2022)

+   8. Li, H., Zhang, J., Chen, Q., & Wang, Y. Stretchable stability and flexibility of wearable electronics devices. Journal Materials 3, 613-619 (2019)

+   9. Sun, Z., Zhou, M., Xian, X., & Lee, C. Augmented tactile-perception and haptic-feedback rings as interfaces for immersive interactions. Nat. Communication, 13, 5224 (2022)

+   10. Kwon, Y.-J., et al. All-printed nanomowires with biocompatible electronic skin for multimodal human interface. Nat. Communication, 11, 3450 (2020)

+   11. Liu, Y. et al. Electronic skin as human-machine interface for robotic VR. Sci. Adv., 8, e6700 (2022)

# Natural Sensors