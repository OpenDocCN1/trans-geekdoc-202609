
Augmented reality navigation systems have the following three characteristics: (1) virtual-real fusion; (2) precise “alignment”; (3) real-time interaction. Although the surgical navigation system has been used for more than 20 years, the current interactive technology still has shortcomings in terms of stability, perception and feedback, limited by hardware technology (Lu et al. 2010). Therefore, augmented reality navigation systems, especially those based on an optical perspective, are very different from traditional human-machine interfaces. Its information channels are more diverse, so the interaction mode is very different from the traditional human-machine interface (Zhao et al. 2013). In addition, during surgery, doctors are under high stress. Therefore, smooth and comfortable human-computer interaction is essential. On the other hand, the redundant information in the human-machine interface may distract the doctor’s energy and make the doctor feel “out of control” (Lee et al. 2011).

## 2 OPTICAL FLUOROSCOPY-BASED SURGICAL NAVIGATION SYSTEMS FOR ACL RECONSTRUCTION

### 2.1 Surgical navigation system

### 2.1.1 System structure

As shown in Figure 1, this paper proposes an augmented reality navigation system based on HoloLens. The system includes a CT machine, C-arm, PC, Micron Tracker, and HoloLens. The relationship between the nine modules of the ACL navigation system based on augmented reality technology is as follows:

- The position tracking module provides the entire system with the position information of each tracking target (calibrator, surgical target, calibration block and HoloLens). The position information is collected by Micron Tracker and transmitted to other modules through the UDP protocol;
- The C-arm space registration module can realize the registration of X-ray images and the surgical space, and the registration results can provide parameter support for the 2D-3D registration module; 2D-3D registration module can realize the registration of the pre-operative CT image and the intraoperative X-ray image;
- The virtual-real registration module can recognize the spatial registration between the virtual space and the actual scene; as a result, information such as virtual models, path planning, etc. accurate scene fusion display;
- 3D reconstruction module can realize 3D reconstruction of preoperative CT images and provide a 3D data model for 2D-3D registration, path planning and visual presentation.

![](img/9eefc6d2972274efeb1680c6a31895e5_83_0.png)

Figure 1. Augmented reality system structure of ACL reconstruction system.

### 2.1.2 Navigation process

The usage flow of the ACL navigation system based on augmented reality technology is as follows:

### 1) Preoperative treatment

- Offline calibration of the HoloLens workspace.
- CT scan of the target area.
- Segmentation and reconstruction of preoperative CT data were performed to obtain femur and tibia, STL models.
- On the segmented STL model, perform surgical path planning.

### 2) Intraoperative Navigation

- Take X-rays, perform spatial calibration on the C-arm, and transmit the calibration results and X-ray images to the 2D-3D registration module.
- In the 2D-3D registration module, import the preoperative CT data and the segmented STL model, adjust the initial position of the STL model and X-ray, perform 2D-3D image registration, and transmit the registration results to the visualization Reality Module.
- Online calibration of HoloLens.
- Enhanced display, navigation tracking.

### 2.2 Spatial registration technology

### 2.2.1 C-arm calibrator based on tapered helix

As shown in Figure 2, to improve the spatial registration accuracy of point pair registration, a C-arm calibrator based on a conical helix is used to calibrate the C-arm. In the vicinity of the surgical target, this calibrator has a higher calibration accuracy than the traditional dual-plane calibrator (Yu et al. 2012).

### 2.2.2 Splat-based 2D-3D image registration

To achieve the spatial unification of preoperative CT images and digital X images a DRR projection-based 2D/3D automatic registration method strategy is adopted. DRR reconstruction, similarity criterion, and parameter optimization algorithms are essential components of the 2D/3D registration process (Collazos and Merchan 2015).

### 2.2.3 Virtual and real calibration based on space compensation

To achieve fast online calibration, the calibration process is decomposed into offline calibration and online calibration by analyzing the workspace of the HoloLens.

![](img/9eefc6d2972274efeb1680c6a31895e5_84_0.png)

Figure 2. Workspace of HoloLens.

### 2.3 Human-computer Interaction Technology

### 2.3.1 Human-computer interface

For scene development in Unity3D, the human-computer interaction interface of the system is shown in Figure 3. The setting of the navigation tracking method can be confirmed by voice or gesture, which does not involve channel integration.

![](img/9eefc6d2972274efeb1680c6a31895e5_85_0.png)

Figure 3. Human-computer interaction interface.

### 2.3.2 Human-computer interaction model

In this paper, the eGOMS model is used to analyze human-computer interaction tasks and realize the integration of multi-channel information. According to the eGOMS model, the interaction model of the virtual-real alignment of the calibration block and the visibility setting of the virtual-real fusion target (Looi and See 2010).

## 3 GUIDELINES FOR HUMAN-COMPUTER INTERACTION BASED ON COGNITIVE MODELS

### 3.1 Human-computer interaction guidelines for surgical navigation systems

This article uses Microsoft HoloLens as the AR display device. Microsoft HoloLens can not only complete the superposition of virtual and real scenes based on optical perspective but also perform voice and gesture interaction (Lokhande et al. 2021). Therefore, the human-computer interaction rules of the AR surgical navigation system mainly include:

- 1) Consistency of virtual and real registration: virtual objects and natural scenes should be effectively integrated to minimize the distortion of virtual objects, tracking errors and parameter errors of user perspective.
- 2) User's sense of security: The biggest problem of the surgical navigation system based on VST-HMD is that the doctor cannot look directly at the actual scene with glasses, so there is a certain sense of fear.
- 3) Effectiveness of information: Information should be classified and managed to avoid redundant information distracting users' energy.

## 4 USABILITY EVALUATION OF HUMAN-COMPUTER INTERACTION

### 4.1 Usability evaluation index based on AHP

According to the ISO9241-11 standard proposed by the International Organization for Standardization, usability refers to the effectiveness, efficiency and satisfaction of a specific user using a product to achieve a particular goal under a specific context of use. Some researchers have conducted usability evaluations for virtual reality systems. However, there are no usability studies on AR navigation system interaction. Therefore, combined with the human-computer interaction criteria proposed in Section 3.2, refer to the virtual reality interface usability evaluation method (Li et al. 2021; Silva and Medeiros 2021; Tao et al. 2018). The consistency test indicators CR and CRi are: 0.0371, 0, 0, 0.0061, 0, 0.0028, respectively. All levels of consistency test indicators are less than 0.1, so all passed the test, where i = 1, 2, 3, 4, 5. If λ and λi are the largest eigenroots corresponding to matrices A and Bi, respectively, and x and xi are the eigenvectors corresponding to matrices A and Bi, respectively. Normalize ε and εi respectively to get vectors θ and θi. If xi represents the element of the vector θ, and yij represents the element of the vector θi, the weight of each layer is combined and calculated, and the total weight of each secondary index can be obtained as xij = yij × θi. The weight of each indicator is shown in Table 1 and Figure 4.

| Index | Weight xi | Index | Weight yij | Comprehensive weight xij |
|---|---|---|---|---|
| Task performance | 0.2345 | Error rate | 1.00002 | 0.2339 |
| Appropriateness | 0.3608 | Key information rate | 0.6298 | 0.2265 |
| | | suggestive | 0.3708 | 0.1336 |
| Ease of use | 0.1598 | Symbolic Manipulation | 0.5109 | 0.0818 |
| | | Complexity | 0.3359 | 0.0533 |
| | | Operation depth | 0.1548 | 0.0243 |
| | | total operation | | |
| Learnability | 0.1029 | New knowledge rate | 0.5837 | 0.0597 |
| | | Study-time | 0.4165 | 0.0428 |
| Interactivity | 0.1452 | Naturalness | 0.2637 | 0.0384 |
| | | Immediacy | 0.2149 | 0.0313 |
| | | predictability of results | 0.5223 | 0.0759 |

![](img/9eefc6d2972274efeb1680c6a31895e5_86_0.png)

Figure 4. Operational depth ratio.

### 4.2 Comprehensive evaluation based on fuzzy theory

The fuzzy evaluation method is based on fuzzy mathematics, applying the synthesis principle of undefined relationships, quantifying some factors with unclear boundaries and challenging to quantify, and comprehensively evaluating the affiliation status of the considered object from multiple aspects (Wang et al. 2011; Yao et al. 2021; Zhou et al. 2021).

- 1) Determine the set of evaluation factors and the set of evaluation grades.
- The performance of human-computer interaction is divided into five grades, V = {excellent, good, fair, poor, and inferior}.

- 2) Single-factor evaluation
- When using fuzzy theory for a comprehensive evaluation, it is necessary to quantify fuzzy sets through membership function. According to the evaluation index of usability evaluation characteristics, this paper adopts the trapezoidal/semi-trapezoidal membership function. Given by experts based on experience, the boundaries of each indicator are shown in Table 2.
