
## Article

## Mechanical simulation

The commercial software ABAQUS was used to predict deformation and evaluate the streptability of interface connections between each layer (Extended Fig. 2). Two Cu/PL laminates were modeled using four-dimensional shell elements².

An explicit solver was used to ensure convergence in involving intricate contact areas with the serpentine interconnections.

Cu was used to evaluate the mechanical properties using an elastic modulus of 110 GPa, Poisson's ratio of 0.34 and a strength of 350 MPa (-0.3 yield). The mechanical behavior of the elastomer (Ecoflex), and the substrate, was modeled using a hyperelastic viscoelastic model.

This relationship was evaluated with an elastic modulus of 10 GPa and a Poisson's ratio of 0.49. For Ep, an elastic modulus of 2.5 GPa and a Poisson's ratio of 0.27 were used. A rigid and frictionless contact model described interactions between the serpentine interconnections and elastomer.

Boundary conditions were implemented on the two vertical edges of the model. Specifically the displacement constraints were prescribed as follows: (uₓ, 0) for the left side and (uₓ, ε*L) for the right side, where ε* is the strain applied along the length of the model and L is the length of the model.

## Bluetooth characterization

The Bluetooth signal was characterized using the received signal strength meter. Measurements were conducted through the Bluetooth scanner. To ensure data accuracy and reliability, the received signal strength value was recorded 15 times under each specified condition (Fig. 1, Extended Fig. 3 and Supplementary Fig. 37).

## Thermal characterization

Thermal images were captured by a thermal camera (FLIR C Series) after activating the sensors. Images were recorded every 10 minutes during different conditions (Fig. 4 and Supplementary Fig. 4).

To assess actual conditions, a thermocouple (a sensor) was placed between the active and the skin to monitor temperature during continuous operation (Supplementary Fig. 4).

## Signal processing of EMG signals for differentiating grasping and relaxing

Raw EMG signals are susceptible to low frequency artifacts and noise. To mitigate these interferences, we used a digital 30–200 Hz bandpass filter and a 6 Hz notch filter.

The root mean square (RMS) of the EMG signals was calculated by:

$$EMG_{RMS} = \sqrt{\frac{1}{N}\sum_{i=1}^{N} EMG^{2}(i)}$$

where N represents the length of the signal and EMG denotes the magnitude of the RMS data points. The value represents the power of the EMG signal during a short duration: duration for grasping and relaxing.

When the window length increases, we capture more of the signal but reduce resolution. We used a window of 200 ms to achieve a balance. The RMS value exceeded 0.2 μV when the robotic finger performed grasping, and conversely, relaxed when the value was below the threshold (Fig. 4b and Extended Data Figs. 7–10).

To account for individual variations in muscle tone, which can influence EMG amplitudes, we implemented an individual-specific calibration strategy to reliably distinguish grasping from relaxing – specifically for each individual, EMG signals were recorded during baseline and grasping actions (each lasting: -2 s to 10 cycles). The RMS of the baseline during grasping and relaxing (V_{baseline} and V_{grasping}) were measured.

$$V_{threshold} = 0.5 \times (V_{baseline} + V_{grasping})$$

This calibration consistent recognition performance across individuals with varying signal quality.

## Characterization of electrode conductivity, impedance and signal quality

The impedance of the test electrode was measured using a digital multimeter (Keysight). Impedance was measured using a bioimpedance analyzer (AD-594B02) in a three-electrode configuration (that, is, reference and counter electrodes).

Measurements were conducted under specific conditions, ringing and vibration conditions (Supplementary Fig. 1).

The impedance of the EMG was evaluated by quantifying the signal-to-noise ratio during grasping, ringing and vibration (Supplementary Fig. 11). In each test, the individual performed hand relaxing and grasping force of –n N.

## Characterization of electrode-skin interface

The impedance at the electrode-skin interface was measured using a Palenostat with a three-electrode configuration (Supplementary Fig. 2). The device maintains a stable pressure.

This setup enabled characterizing the impedance of the working electrode-skin interface, while the counter electrode circuited the circuits. The three electrodes were laminated onto the flexible polymer substrate with a 2 cm spacing.

We utilized the galvanic impedance spectroscopy over a frequency range of 0.1 Hz to 10 Hz, to ensure stability for the body. The units were tested under various conditions, the electrode-skin interface was submerged in seawater collected from the San Diego Mission.

## Stability of the sensor performance

To evaluate the sensors' long-term term performance during interactive activities, we conducted experiments over five days. The experiments were performed on the individuals, where the EMG module recorded signals induced by grasping and hand. The recorded signal was analysed using power spectral density analysis (Supplementary Fig. 12).

Performance under varying temperature and humidity conditions was assessed by baseline noise levels. The sensors were placed on a hotplate at different temperatures while kept stationary. Additionally, the sensors were tested under varying humidity levels during measurement (Supplementary Fig. 13).

To characterize the effect of pressure on signal quality, we measured EMG for 15 min and 30 min during short-term runs. In each session, the individual performed hand relaxing and grasping force of –n N (Supplementary Fig. 14).

## Generation of the corpus training dataset

The individual performed each gesture 20 times while sitting. Each session was recorded independently with 18 different motor motions, including grasping, ringing, vibration and their combinations at different stages, with a duration of 1 s (Fig. 3a and Extended Data Fig. 4). To address the influence of orientation and the morphology of the gesture signals, each gesture was also performed motion artifacts related to vibration (without those from grasping) (Supplementary Fig. 15).

## Article

https://doi.org/10.1038/s41468-025-00001-3

All superimposed signals used in the dataset were unique and non-repetitive (which accommodates variability in both signals and motion), preventing the model from overestimating recurring patterns.

In addition, to reduce the orientation differences between superimposed motions and the gesture signals collected during different motion aspects (gestures used for training), we adopted two measures: first, during the training, we maintained a palm-down posture, matching the orientation used during real-world gesture execution. Second, we filtered the baseline component from the acceleration in motion before preprocessing (note that accelerometers have gravity bias), which reduces the orientation disparity; thereby aligning the superimposed signals with real world gesture signals collected under motions.

MATLAB was used for TCP/IP communication (Supplementary Fig. 27). In demonstrations, the beaker was at a fixed location to ensure comparison of gesture used under different motion aspects, and the robotic arm could operate anywhere within the workspace.

## Collection of superimposed sea waves

We generated superimposed waves in an enclosed atmosphere and monitored the wave characteristics using the Scripps-Ocean Research Simulator (Fig. 5b and Supplementary Fig. 30). Throughout the data acquisition, the sensors remained afloat on the water surface, which emitted a dliver wave with a paddle, with the frequency adjusted to vary wavelength (Supplementary.

## Reporting

Further information on this research is available in the Nature Research Report Linking to this article.

## Process for training learning

For training, we collected data from 6 subjects (5 males and 1 female, aged 21 to 34) with different motion speeds and forearm lengths (40-50 cm). The data from five individuals were used to train the CNN, while the sixth was used for fine-tuning. During the testing phase, we used the CNN to determine the output. Notably, 100 sequences were randomly selected to evaluate the performance of the CNN (Fig. 3c and Extended Data Fig. 5). This cross-validation approach separates training and testing.

## Data availability

The material and resources supporting this findings are available upon request.

## Code availability

The codes used in- are found in a publicly accessible repository (https://github.com/z).

## Generation of the signals

Each signal was generated using a sliding window (25 ms step) and then sent to an online CNN in Python.

## References

1. Gao, W., et al. Fully integrated wearable sensors for sensing and harvest. Nat. Nature, 529, 509-514 (2019).
2. Li, C., et al. Wearable-smart electronics for wrist sensing and harvesting. Nat. Human Interact, 7, 13319 (2021).
3. Liu, R., Wang, Z., Fukuda, K., & Seymour, M. Flexible soft-power sensors for wearable. Nat. Mater., 7, 870-886 (2022).
4. Li, H., Zhang, J., Chen, Q., & Wang, Y. Stretchable stability and flexibility of wearable electronics devices. Journal Materials 3, 613-619 (2019).
5. Sun, Z., Zhou, M., Xian, X., & Lee, C. Augmented tactile-perception and haptic-feedback rings as interfaces for immersive interactions. Nat. Communication, 13, 5224 (2022).
6. Wang, X., et al. Continuous monitoring of deep-tissue hemodynamics. Nat. Eng, 5, 749-758 (2018).
7. Zhang, J., et al. Smart contact lenses for monitoring intracranial pressure. Conn. Ophthalmol., 12, e02110 (2022).
8. Manassak, L., Lin, N., Lennon, A., Wang, J., & Dahlin, R. Energy harvesting autonomous sweat-based. (20).
9. Kwon, Y.-J., et al. All-printed nanomowires with biocompatible electronic skin for multimodal human interface. Nat. Communication, 11, 3450 (2020).
10. Liu, Y. et al. Electronic skin as human-machine interface for robotic VR. Sci. Adv., 8, e6700 (2022).

## Control of the robot

To ensure sensor orientation, the individual maintained a palm-down orientation. This was necessary because six gestures involved the palm (that, is, rotation).

IMU and EMG data from the wearables were sent to a USB receiver and processed by MATLAB on a computer. The segmented CNN signals were generated using a sliding window (25 ms step) and then sent to an online CNN in Python. The model was chosen after three consecutive predictions, and the predicted results were sent back to MATLAB to control the robotic arm, which executed commands within the desired state. In addition, the EMGs were acquired and filtered in MATLAB to control the grasping of the robotic gripper based on the RMS values.
