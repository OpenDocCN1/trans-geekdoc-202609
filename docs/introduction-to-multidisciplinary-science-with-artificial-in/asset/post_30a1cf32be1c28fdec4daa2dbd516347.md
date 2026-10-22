
We used the fact that the total time it takes sound to cross the elementary tube is $dt = dx/c_s$. Furthermore, by substituting mass conservation in (2.34) into (2.35), we arrive at

$$\rho c_s dc_s = -dP \implies c_s^2 d\rho = dP \iff c_s = \left(\frac{dP}{d\rho}\right)^{1/2}. \tag{2.36}$$

The sound enters and leaves the tube in the same state, without increasing the entropy; i.e., $PV^\gamma = \text{constant}$ (where $\gamma = c_P/c_V$), which implies that

$$\ln P + \gamma \ln V = \text{constant} \implies \ln P - \gamma \ln \rho = \text{constant}$$

or

$$\frac{dP}{d\rho} = \gamma \frac{P}{\rho} = \gamma \frac{RT}{M}, \tag{2.37}$$

where $M$ is the molecular mass of the gas, as defined earlier. Combining (2.36) and (2.37), we obtain the velocity of sound passing through air as

$$c_s = \left(\gamma \frac{RT}{M}\right)^{1/2}. \tag{2.38}$$

Note that the hotter the gas, the faster the sound is. Also, the heavier the gas, the slower the sound is. For air, $\gamma = 1.4$, $M = 0.029$ kg/mole, $R = 8.314$ Joule/(Kelvin $\times$ mole), and $T = 300$ K. We then obtain

$$c_s = \left(\frac{1.4 \times 8.314 \times 300}{0.029}\right)^{1/2} = 347\ \text{m/s}. \tag{2.39}$$

**Quiz:**

- (1) The amount of heat needed to change one gram of ice at 0 degree Celsius to one gram of liquid water at 0 degree Celsius is $3.35 \times 10^2$ Joules. What is the change in entropy when 100 grams of ice at 0 degree Celsius melt into 100 grams of liquid water at 0 degree Celsius?
- (2) Suppose that two reservoirs are brought into direct contact. An amount of heat, $Q$, is transferred from the high temperature reservoir (heat source) to the low temperature reservoir (heat sink). Determine the entropy change and show that heat transfer is irreversible.
- (3) No heat is supplied in adiabatic expansion, but work is done. Show that, for an ideal gas, this work is $W = c_V(T_B - T_A)$, where $T_A$ is the temperature at the beginning of the adiabatic process and $T_B$ is the temperature at the end of the adiabatic process.

## 2.1.3. Entropy: Public Policies

The use of entropy is not limited to thermodynamics. It extends to public policies and the field of economics. However, the key parameter in these cases is no longer the temperature. It is now the statistical distribution, including random variables.

![](img/f5b5b8709fc3a81631262f22d3552c5e_186_0.png)

Figure 2.5. Generalized Gaussian distribution for α = 0.5, 1 (Laplace), 2 (Gaussian), and 6. For the scale parameter β, we have used the following expression: β² = Γ(1/α) / Γ(3/α). Notice that we have scaled up the curves corresponding to α = 1, 2, and 6 to facilitate their display. The scaling factors are shown in the top right corner of this picture.

The fundamental question at this point is: How to interpret entropy? To answer this question, let us return to the example of coin tossing that we discussed earlier. Our discussion of this example was carried out under the assumption of equiprobability of the outcomes; i.e., the probability of observing the head is 0.5 as well as that of observing the tail. Suppose that the coin has been modified such that the coin-tossing experiment becomes biased. Such modifications can lead to the production of more heads than tails or to a deterministic experiment in which the outcomes are always heads, for instance. These possible modifications of the coin show the need for an additional statistical quantity which characterizes the degree of randomness of the experiment itself. The entropy provides this characterization. If the experiment is really as unpredictable as coin tossing, with two equiprobable outcomes, the entropy $H[X]$ has its maximal value. This maximal value is 1 in the case of the coin-tossing experiment. If the experiment is totally biased toward either heads or tails, the entropy is zero.

So the entropy is a function of the probability-density function, $p_X$, for the coin-tossing experiment:

$$H[X] = -\left[p_X \log p_X + (1 - p_X) \log(1 - p_X)\right]. \tag{2.45}$$

In this case, the PDF can be represented by a single value. Figure 2.6 shows this entropy as a function of $p_X$. Maximum entropy is achieved for equiprobable outcomes; minimum entropy is achieved for deterministic outcomes $p_X = 0$ and $p_X = 1$.

![](img/f5b5b8709fc3a81631262f22d3552c5e_188_0.png)

Figure 2.7. (a) Entropy of the generalized Gaussian PDFs as a function of α, which is a positive real number and describes the sharpness of the distribution. (b) We zoomed the plot of entropy versus α around α = 2 to point out that the maximum entropy is achieved for α = 2.

Figure 2.7 captures this description of entropy as a function of α. Notice that the Gaussian PDF (i.e., α = 2) has the largest entropy. This result shows that the Gaussian distribution is the “most random” or the least structured of all symmetric distributions. We can also notice that the entropy is also small for “spiky” PDFs.

## 2.1.4. Heat-Transfer Mechanisms

Heat can move in four ways: conduction, convection, latent heat, and radiation (Figure 2.8). Heat energy is most intense in substances whose molecules are moving rapidly in a very disorderly way. Such substances will give up some of their heat to another substance whose molecules are less agitated. When this happens, heat is said to “flow” from one substance to another (or from one body to another). The energy transfer is indicated by a change in temperature. This transfer of heat is known as conduction, which requires the presence of matter and therefore can occur only in solids, liquids, and gases (see Figures 2.1 and 2.8). So conduction is a good way of moving heat around when dealing with objects (solids, liquids, and gases) in contact with each other. But it is not useful in a vacuum (regions where there is no matter), such as space. In other words, conduction is not important for heat exchange between the sun and the Earth (or for climate sciences) because there is nothing to conduct heat between Earth and space.

Heat can be transferred from hot places to cold places by convection. Convection occurs when warmer areas of a liquid or gas rise to cooler areas in a liquid or gaseous form. The cooler liquid or gas then takes the place of the warmer areas, which have risen. This exchange results in a continuous circulation pattern known as convection. Water boiling in a pan is a good example of a convection current (see Figure 3.33 of Ikelle, 2023a and Figure 2.8). Convection is important for describing the motion of the atmosphere and the ocean on both local and global scales.

![](img/f5b5b8709fc3a81631262f22d3552c5e_189_0.png)

Figure 2.8. Illustrations of the four heat transfer mechanisms. The pan is held above the burner and is not in direct contact with it. Yet energy travels from the burner to the pan via the process of radiation. The pan absorbs much of this radiation and becomes hot. In turn, the water nearest the bottom of the pan takes on more heat energy than the water above. The hotter water at the bottom rises and water not as hot at the top descends, setting up vertical circulation currents known as convection. The convection currents bring new but cooler water to the bottom of the pan to absorb heat energy from the pan's bottom. Once the water reaches the boiling point, some of the liquid water will change to gas bubbles (latent heat). Heat in the lower part of the pan migrates, molecule to molecule, up the side of the pan to its handle, and then out along the handle, all of this by the process of conduction.

As a substance changes phase, such as from a solid to a liquid or a liquid to a gas, it requires latent heat energy. For example, heat is needed to transform water into vapor. This way of moving heat is used in the climate sciences in relationship with the water cycle between the oceans and the atmosphere. In more general terms, the internal energy associated with the phase of a system is latent energy or latent heat (see Figures 2.8 and 2.9). It is associated with the intermolecular forces (forces that bind molecules to each other) between the molecules of a system. As described in Ikelle (2023a), these forces are strongest in solids and weakest in gases.

Radiation, which is important and even central to climate-science studies, is a method of heat transfer that does not rely on any contact between the heat source and the heated object, as is the case with conduction and convection (see Figures 2.4 and 2.8). Heat can be transmitted through empty space by thermal radiation, often called infrared radiation. Radiation absorption is accomplished directly through electromagnetic interactions. The process involves the motion of atoms and molecules at the beginning (radiation) and the end (absorption) of the
