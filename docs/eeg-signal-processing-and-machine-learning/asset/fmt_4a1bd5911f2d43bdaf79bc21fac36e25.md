
## 3.5 Electronic Models

These models describe the cell as an independent unit. The well established models such as the Hodgkin–Huxley model have been implemented using electronic circuits. Although, for accurate models large numbers of components are required, in practise it has been shown that a good approximation of such models can be achieved using simple circuits [[56]](#c03.xhtml#c3-bib-0056).

### 3.5.1 Models Describing the Function of the Membrane

Most of the models describing the excitation mechanism of the membrane are electronic realizations of the theoretical membrane model of Hodgkin and Huxley. In the following sections, two of these realizations are discussed.

![Figure 3.14 The Lewis membrane model [57].](images/c03f014.gif)

[**Figure 3.14**](#c03.xhtml#R_c3-fig-0014) The Lewis membrane model [[57]](#c03.xhtml#c3-bib-0057).

#### 3.5.1.1 Lewis Membrane Model

Lewis electronic membrane models are based on the Hodgkin–Huxley equations. All the components are parallel circuits connected between nodes representing the inside and outside of the membrane. He realized the sodium and potassium conductances using electronic hardware in the form of active filters. Since the model output is the transmembrane voltage `V_m`, the potassium current can be evaluated by multiplying the voltage corresponding to `G_K` by (`V_m` − `V_K`). [Figure 3.14](#c03.xhtml#c3-fig-0014) is consequently an accurate physical analogue to the Hodgkin–Huxley expressions, and the behaviour of the output voltage `V_m` corresponds to that predicted by the Hodgkin–Huxley equations. The electronic circuits in the Lewis neuromime had provision for inserting (and varying) not only such constants as `G_K_max`, `G_Na_max`, `V_K`, `V_Na`, `V_Cl`, which enter the Hodgkin–Huxley formulation, but also `τ[h]`, `τ[m]`, `τ[n]`, which allow modifications from the Hodgkin–Huxley equations. In this realization the voltages of the biological membrane are multiplied by 100 to fit the electronic circuit. In other quantities, the original values of the biological membrane have been used.

#### 3.5.1.2 Roy Membrane Model

As in [Figure 3.15](#c03.xhtml#c3-fig-0015), Roy also introduced a model based on the Hodgkin–Huxley model [[58]](#c03.xhtml#c3-bib-0058). He used field‐effect transistors (FETs) to simulate the sodium and potassium conductances in the membrane model [[58]](#c03.xhtml#c3-bib-0058).

In the Roy model the conductance is controlled by a circuit including an operational amplifier, capacitors, and resistors. This circuit is designed to make the conductance behave according to the Hodgkin–Huxley model. Roy's main goal was to achieve a very simple model rather than to simulate accurately the Hodgkin–Huxley model.

### 3.5.2 Models Describing the Function of a Neuron

#### 3.5.2.1 Lewis Neuron Model

The Lewis model is based on the Hodgkin–Huxley membrane model and the theories of Eccles on synaptic transmission [[59]](#c03.xhtml#c3-bib-0059). The model circuit is illustrated in [Figure 3.16](#c03.xhtml#c3-fig-0016). This neuron model is divided into two sections: the synaptic section and the section generating the action pulse. Both sections consist of parallel circuits connected to the nodes representing the intracellular and extracellular sites of the membrane.

![Figure 3.15 Circuits simulating (a) potassium and (b) sodium conductances in the Roy membrane model [58].](images/c03f015.gif)

[**Figure 3.15**](#c03.xhtml#R_c3-fig-0015) Circuits simulating (a) potassium and (b) sodium conductances in the Roy membrane model [[58]](#c03.xhtml#c3-bib-0058).

![Figure 3.16 The Lewis neuron model from 1968 [57].](images/c03f016.gif)

[**Figure 3.16**](#c03.xhtml#R_c3-fig-0016) The Lewis neuron model from 1968 [[57]](#c03.xhtml#c3-bib-0057).
