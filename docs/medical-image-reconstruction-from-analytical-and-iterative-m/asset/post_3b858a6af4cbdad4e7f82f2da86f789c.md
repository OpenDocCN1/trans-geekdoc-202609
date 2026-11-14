
![](img/dd555effd38151c67af30d84800c554a_201_0.png)

Fig. 7.5: Protons precess at the Larmor frequency $\omega_0$.

find a way to create precession while the vector $\vec{M}$ is on that rotating platform. The vector $\vec{M}$ now is currently standing on the rotating platform upright and is spinning on its own axis; there is no motion relative to the platform. Even if the vector $\vec{M}$ is not standing upright and it has a nonzero angle with the vertical line, vector $\vec{M}$ will stay with that angle and will not have any motion relative to the platform.

Next, we step on the rotating platform and apply a new magnetic field $\vec{B}_1$, orthogonal to the main magnetic field $\vec{B}_0$. On the rotating platform, the vector $\vec{M}$ does not feel the existence of the main field $\vec{B}_0$; it only feels the push from the new field $\vec{B}_1$. Since $\vec{M}$ is not aligned with $\vec{B}_1$, it will precess about the direction of $\vec{B}_1$ (see Figure 7.7) at a precession frequency $\omega_1 = \gamma B_1$. Once $\vec{M}$ reaches the platform floor, we turn the new field $\vec{B}_1$ off. Thus, the mission of knocking off $\vec{M}$ is accomplished. The $\vec{B}_1$ field is only turned on very briefly; it is called a 90° RF pulse if it is turned off as soon as $\vec{M}$ touches the platform floor.

What is this $\vec{B}_1$ field anyway? The magnetic field $\vec{B}_1$ is applied on a virtual rotating platform, which rotates at the Larmor frequency, say 64 MHz for a proton in a 1.5 T MRI machine. Therefore, $\vec{B}_1$ is an alternating electromagnetic RF field with the same frequency as the Larmor frequency. Another term for the same frequency is the resonance frequency. The $\vec{B}_1$ RF signal is sent to the patient through an RF coil, which is basically an antenna. The procedure of turning the $\vec{B}_1$ RF field on and knocking $\vec{M}$ off balance is called RF excitation.

After RF excitation, we turn off $\vec{B}_1$. Now the net magnetic moment $\vec{M}$ is not in the equilibrium state, but in the excited state. The vector $\vec{M}$ is precessing about the main field direction $\vec{B}_0$, and RF signals that contain the patient’s proton density information are emitted. The excited state is unstable. After excitation, the vector $\vec{M}$ then goes through the relaxation period and eventually returns to the original equilibrium state, where the vector $\vec{M}$ points to the $\vec{B}_0$ direction (see Figure 7.8). In a Cartesian system, the $\vec{B}_0$ direction is the z-direction, and the “platform floor” is the x–y plane.

The x- and y-components of the vector $\vec{M}$ make up the MRI signal. After $\vec{M}$ relaxes back to its equilibrium position, both its x- and y-components are zero; hence, no more signals can be detected. Another RF pulse excitation is needed for further data acquisition. This procedure is repeated over and over again until enough data are acquired for imaging.

![](img/dd555effd38151c67af30d84800c554a_202_0.png)

Fig. 7.6: The magnetization vector does not precess relative to the rotating platform.

![](img/dd555effd38151c67af30d84800c554a_202_1.png)

Fig. 7.7: On the rotating platform, the effect of the main field can be ignored. Only the new B1 field is effective.

![](img/dd555effd38151c67af30d84800c554a_203_0.png)

Fig. 7.8: Relaxation of the magnetization vector.

## 7.3 Spatial Encoding

The RF signal emitted by the patient as described in Section 7.2 cannot be used to form an image because it is a combined signal from everywhere. We need a way to code the location information. This is achieved by the gradient coils.

In the MRI machine, there are many coils. The main large superconducting coil immersed in liquid helium is used to generate the strong static $B_0$ field. There are RF coils, which are used to emit RF pulses for excitation and to receive RF imaging signals. The other coils in the machine to create gradients are x-gradient coils, y-gradient coils, and z-gradient coils.

### 7.3.1 To obtain z-information: slice selection

The z-gradient coils are shown in Figure 7.9. The currents in the two coils are running in the opposite directions and generate the local magnetic fields to enhance and reduce the main field $B_0$, respectively. The resultant magnetic field is still pointing in the z-direction; however, the field strength is stronger at locations with larger z-values and is weaker at locations with smaller z-values. These coils create a gradient of the magnetic field strength in the z-direction.

This z-gradient makes a nonuniform magnetic field, which results in different Larmor frequencies $\omega$ for a different z-position. The Larmor frequency is $\omega_0$ only at one z-slice. We turn on and off the z-gradient and the $B_1$ RF pulse at the same time. The $B_1$ RF pulse is at the frequency of $\omega_0$. According to the resonance frequency principle, only

![](img/dd555effd38151c67af30d84800c554a_204_0.png)

![](img/dd555effd38151c67af30d84800c554a_204_1.png)

one z-slice of the patient body is affected by the RF pulse. That is, only the protons in this particular z-slice get excited and send out the RF signal (see Figure 7.10).

### 7.3.2 To obtain x-information: frequency encoding

We use the x-gradient to provide the x-position information. When we are ready to receive the RF signal from the patient, we turn on the x-gradient. The x-gradient is generated by the x-gradient coils, and it makes the strength of the main magnetic field to vary in the x-direction. The principle of using x-gradient to code x-position is illustrated in Figure 7.11. Using the relation $\omega = \gamma B$, the stronger magnetic field $B$ gives the higher frequency. Thus, the x-location can be determined by the received frequency.

The x-gradient coils are depicted in Figure 7.12. We assume that the x-direction is the direction from the patient's right ear to left ear. The x-gradient is turned on only when the RF signal is received, and this gradient is also called the readout gradient. Do not turn it on during slice selection. When you turn two gradients on at the same time, they will combine and form a gradient in the third direction.

### 7.3.3 To obtain y-information: phase encoding

After slice selection and before RF signal readout, we turn on the y-gradient for a short time. Before a gradient is turned on, $\vec{M}$ at all locations precess at the same frequency (i.e., same speed). However, when the y-gradient is turned on, the field strength at a different y-position is different. As a result, $\vec{M}$ at a different y-position precesses at a different Larmor frequency (e.g., precession at a faster rate for a position with a larger y value, Figure 7.13). After the y-gradient is on for a short while, it is turned off. At this moment, $\vec{M}$ at a different y-position will arrive at a different phase (i.e., angle). This phase carries the information of the y-position.

The y-gradient coils look exactly like the x-gradient coils, except for a 90° rotation. The effective gradient is confined to the gap between two pairs of the coils (see Figure 7.14).

![](img/dd555effd38151c67af30d84800c554a_205_0.png)

![](img/dd555effd38151c67af30d84800c554a_206_0.png)

Fig. 7.12: The x-gradient coils generate a nonuniform magnetic field in the readout direction.

![](img/dd555effd38151c67af30d84800c554a_206_1.png)

Fig. 7.13: The y-gradient causes the phase displacement as a function of y-location.

The time diagram shown in Figure 7.15 summarizes this basic MRI data acquisition procedure. This procedure is repeated many times. At each time, a different value of the y-gradient is used. The next section will show that the acquired data is nothing but the 2D Fourier transform of the image f(x, y), which is closely related to the proton density distribution inside the patient body. A 2D inverse Fourier transform is used to reconstruct the image. A typical MRI image is shown in Figure 7.16. There is a small negative pulse in front of the x-gradient readout pulse. The purpose of it is to create an “echo” to make the strongest signal at the center.
