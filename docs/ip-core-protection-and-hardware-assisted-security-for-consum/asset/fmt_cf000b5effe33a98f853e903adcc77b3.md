
The understanding of this chapter so far is that a PUF provides better security and robustness to the entire application. But there are many issues and challenges that have to be addressed while designing and implementing the PUF in an application ([Chang *et al*., 2017](#Chapter12.html#c12_bib5); [Wan *et al*., 2015](#Chapter12.html#c12_bib72); [Wen and Lao, 2018](#Chapter12.html#c12_bib74); Ye *et al*., [2017](#Chapter12.html#c12_bib79), [2018](#Chapter12.html#c12_bib80)). There are various attempts for providing better security and robustness by implementation of PUF, but some of the common attacks are:

*   There is a chance that the attacker can create a large number of chips with the similar design to the PUF module used in a respective application for obtaining the response. In cases where the design of PUF is simple, this can be very successful.

*   It is also possible to predict the response of the PUF or calculate it using mathematical modeling techniques ([Ma *et al*., 2018](#Chapter12.html#c12_bib40); [Mispan *et al*., 2018](#Chapter12.html#c12_bib52); [Tanaka *et al*., 2018](#Chapter12.html#c12_bib71)). Adding a nonlinearity to the PUF design can avoid these kinds of attacks.

*   There are different types of attacks, invasive or semi-invasive, which can determine the time delay and power of the devices. Tamper-resisting packaging can avoid these attacks.

*   Introducing errors into the module can also be performed by the attacker to tamper with it and render it useless.

These attacks are common and there are many different kinds of solutions that are suggested. Improvements can also be made to the PUF designs to make them difficult to attack by the attacker.

*   A hash function can also be implemented before or after the PUF module which can prevent the attacker from gaining knowledge of the CRPs. This can prevent the modeling attacks on the modules.

*   Error correction mechanisms can be implemented in the PUF modules which can make them more reliable and avoid bit-flips due to environmental variations and operational disturbances.

*   Control of PUF response is often desired by the client who is using the module. Additional secret keys for the input of the modules can be implemented, which is totally in hands of the user or client.

*   Tamper-resistant packaging should be used for the ICs and PUF modules. This will increase the cost of the entire application and will increase the robustness also.

Attacking the PUF modules is a kind of attack that has to be performed by an adversary with an ill intent. But there are also other challenges faced during the design of PUF modules ([Ganta and Nazhandali, 2014](#Chapter12.html#c12_bib13); [Sahoo *et al*., 2018](#Chapter12.html#c12_bib64); [Wang and Tehranipoor, 2010](#Chapter12.html#c12_bib73); [Yanambaka *et al*., 2017, 2018](#Chapter12.html#c12_bib78)). Some of the challenges include crosstalk, noise in the signals, noise in power supply, and so on. Noise sources can also originate from an unusual input pattern which varies with a different input. Such a noise can be taken as an advantage by the user in designing different input challenges which will increase the robustness of the module against the attackers.

When a large switching activity is triggered due to the input pattern, a power supply noise can occur. The dynamic power is increased due to this and will be responsible for a voltage drop in the power line and an increase in voltage at the ground. Such changes in the supply voltages can cause the change in gate voltages and induce unusual delays in the circuitry. Then the entire circuit operation changes which affect the output response inducing more errors into it. Parasitics should also be taken into consideration during the design of a PUF module.

Aging is another issue that is present in the PUF designs. With the aging effects, the integrity of the circuit degrades over time and renders it useless. Over a period of time, the circuit health degrades and the output responses of a set of challenges can also be affected due to these changes ([Chowdhury *et al*., 2017](#Chapter12.html#c12_bib10); [Ganta and Nazhandali, 2014](#Chapter12.html#c12_bib13); [Meguerdichian and Potkonja, 2011](#Chapter12.html#c12_bib51); [Rahman *et al*., 2015, 2016](#Chapter12.html#c12_bib58)). The aging effects on the PUF module depending on the frequency of turning the device on have been presented by [Ganta and Nazhandali (2014)](#Chapter12.html#c12_bib13). An RO PUF was subjected to the study and some of the observations presented by [Ganta and Nazhandali (2014)](#Chapter12.html#c12_bib13) are:

*   The bit error rate (BER) in the case of PUF, which is always on is the highest. But when the device is turned on during the day only once, the BER is 2%. A 35% reduction in BER can be achieved by turning on the device once a day.

*   The manufacturing variations of the devices are modeled during the simulation as threshold voltage variations. A mismatch was observed by [Ganta and Nazhandali (2014)](#Chapter12.html#c12_bib13) in identical circuit elements, and when the process variation is high, the PUF is stable.

*   For the effects of temperature and the aging of the modules, and their effects on the stability of design, the PUFs were operated at various temperatures and ages. The effect of aging on the PUF design was not observed to be significant on the stability of the device due to the differential nature. The correlation on stability is shown as 70% of the aging effect and the temperature.

*   Supply voltage and the noise in the supply voltage are also the challenges in the designs. The PUFs’ performance is measured in the presence of these issues and aging by [Ganta and Nazhandali (2014)](#Chapter12.html#c12_bib13). The effect of supply noise is less than 0.2% in the presence of aging. But the BER of the PUF that is operating at a subthreshold voltage with aging is high.

*   The stability of the PUF depends on the ring oscillation configuration highly where with an increase in the stages, there is also an increase in the susceptibility to the environmental changes.

### 12.16 Conclusion

This concept of a PUF was initially proposed in 2001 as physical one-way function. Since then, there are various concepts of PUF that were designed using different architectures, devices, and materials. Many of the PUFs are highly robust and others are not secure which can be easily broken with the implementation of a simple machine learning algorithm.

Research is being conducted for designing more robust and secure designs of PUFs for better security. But with the high implementations of IoT architectures, there is more necessity and scope for the development of low-power designs of PUF. There are low-power-consuming designs being implemented and proposed by many researchers around the world but the main focus of research has been the increase in the robustness and resistance to attacks. As a future research, low-power design of PUF can also be implemented for better wide range of implementation and integration.

There are also the threats and attacks on the PUF that are yet to be addressed. With the introduction of new applications every day, it is necessary to secure them against attacks that come with it. Side-channel resilient PUF designs are yet to be more saturated and better designs are yet to come into the consumer-level market. PUFs are being implemented in many enterprise domain applications like servers, but commercial market is still open to the implementations of PUF. This can also be considered as a future research of the PUFs.

### 12.17 Exercises

1.  What is encryption and decryption?

2.  How is implementing a PUF be better than using a traditional cryptographic primitive?

3.  What is PUF?

4.  Explain the principle of PUF.

5.  Describe the working of an arbiter PUF.

6.  Explain uniqueness of the PUF with an example. How hamming distance is calculated for uniqueness?
