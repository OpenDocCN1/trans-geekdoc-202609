
cabling are UTP, STP, and coaxial cable (coax). UTP has an outer jacket to protect the copper wires from physical damage, twisted pairs to protect the signal from interference, and color-coded plastic insulation that electrically isolates wires from each other and identifies each pair. STP cable uses four pairs of wires, each wrapped in a foil shield, and the four pairs are then wrapped in an overall metallic braid or foil. Coaxial cable, or coax for short, gets its name from the fact that it has two conductors that share the same axis. Coax is used to attach antennas to wireless devices. Cable internet providers use coax inside their customers’ premises.

## UTP Cabling
UTP cabling consists of four pairs of color-coded copper wires that have been twisted together and then encased in a flexible plastic sheath. UTP cable does not use shielding to counter the effects of EMI and RFI. Instead, cable designers have discovered other ways they can limit the negative effect of crosstalk: by using cancellation and by varying the number of twists per wire pair. UTP cabling conforms to the standards established jointly by the TIA/EIA. The electrical characteristics of copper cabling are defined by the Institute of Electrical and Electronics Engineers (IEEE). UTP cable is usually terminated with RJ-45 connectors. The main cable types created by using specific wiring conventions are Ethernet straight-through and Ethernet crossover. Cisco has a proprietary UTP cable called a rollover cable that connects a workstation to a router console port.

## Fiber-Optic Cabling
Optical fiber cable transmits data over longer distances and at higher bandwidths than any other networking media. Fiber-optic cable can transmit signals with less attenuation than copper wire and is completely immune to EMI and RFI. Optical fiber contains a flexible but extremely thin, transparent strand of very pure glass, not much bigger than a human hair. Bits are encoded on the fiber as light impulses. Fiber-optic cabling is now being used in enterprise networks, FTTH, long-haul networks, and submarine cable networks. There are four types of fiber-optic connectors: ST, SC, LC, and duplex multimode LC. Fiber-optic patch cords include SC-SC multimode, LC-LC single-mode, ST-LC multimode, and SC-ST single-mode. In most enterprise environments, optical fiber is primarily used as backbone cabling for high-traffic point-to-point connections between data distribution facilities and for interconnecting buildings in multi-building campuses.

## Wireless Media
Wireless media carry electromagnetic signals that represent the binary digits of data communications using radio wave or microwave frequencies. Wireless does have some limitations, including coverage area, interference, security, and the problems that occur with any shared medium. Wireless standards include Wi-Fi (IEEE 802.11), Bluetooth (IEEE 802.15), WiMAX (IEEE 802.16), and Zigbee (IEEE 802.15.4). A wireless LAN (WLAN) requires a wireless AP and wireless NIC adapters.

## Practice
The following activities provide practice with the topics introduced in this chapter. The lab is available in the companion Introduction to Networks Labs & Study Guide (CCNAv7) (ISBN 9780136634454). The Packet Tracer activity instructions are also provided in the Labs & Study Guide. The PKA files are available in the online course.

![](img/e71dc48d3ae3db3394e5857ab2acae75_206_0.png)

## Lab
### Lab 4.6.6: View Wired and Wireless NIC Information

![](img/e71dc48d3ae3db3394e5857ab2acae75_206_1.png)

## Packet Tracer Activities
Packet Tracer 4.6.5: Connect a Wired and Wireless LAN

Packet Tracer 4.7.1: Connect the Physical Layer

## Check Your Understanding Questions
Complete all the review questions listed here to test your understanding of the topics and concepts in this chapter. The appendix “Answers to ‘Check Your Understanding’ Questions” lists the answers.

- 1. What is the purpose of the OSI physical layer?
  a. controlling access to media
  b. transmitting bits across the local media
  c. performing error detection on received frames
  d. exchanging frames between nodes over physical network media

2. Why are two strands of fiber used for a single fiber-optic connection?
- a. The two strands allow the data to travel for longer distances without degrading.
- b. The two strands prevent crosstalk from causing interference on the connection.
- c. The two strands increase the speed at which the data can travel.
- d. The two strands allow for full-duplex connectivity.

3. Which of the following describes crosstalk?
- a. the distortion of a network signal due to fluorescent lighting
- b. the distortion of a transmitted message due to signals carried in adjacent wires
- c. the weakening of a network signal over long cable lengths
- d. the loss of wireless signal over excessive distance from an access point

4. Which procedure is used to reduce the effect of crosstalk in copper cables?
- a. requiring proper grounding connections
- b. twisting opposing-circuit wire pairs together
- c. wrapping a bundle of wires with metallic shielding
- d. designing a cable infrastructure to avoid crosstalk interference
- e. avoiding sharp bends during installation

5. Which type of UTP cable is used to connect a PC to a switch port?
- a. console
- b. rollover
- c. crossover
- d. straight-through

6. What is the definition of bandwidth?
- a. the speed of bits across media over a given period of time
- b. the speed at which bits travel on a network
- c. the amount of data that can flow in a given amount of time
- d. the measure of usable data transferred over a given period of time

7. Which statement correctly describes frame encoding?
- a. It uses the characteristic of one wave to modify another wave.
- b. It transmits data signals along with a clock signal that occurs at evenly spaced time durations.
- c. It generates the electrical, optical, or wireless signals that represent the binary numbers of the frame.
- d. It converts bits into a predefined code in order to provide a predictable pattern to help distinguish data bits from control bits.

8. Which of the following is a characteristic of UTP cabling?
- a. cancellation
- b. cladding
- c. immunity to electrical hazards
- d. woven copper braid or metallic foil

9. A wireless LAN is being deployed inside the new one-room office that is occupied by the park ranger. The office is located at the highest part of the national park. After network testing is complete, the technicians report that the wireless LAN signal is occasionally affected by some type of interference. What is a possible cause of the signal distortion?
- a. the microwave oven
- b. the large number of trees surrounding the office
- c. the elevated location where the wireless LAN was installed
- d. the number of wireless devices that are used in the wireless LAN

10. What is indicated by the term *throughput*?
- a. the guaranteed data transfer rate offered by an ISP
- b. the capacity of a particular medium to carry data
- c. the measure of the usable data transferred across media over a given period of time
- d. the measure of bits transferred across media over a given period of time

11. What is one advantage of using fiber-optic cabling rather than copper cabling?
- a. It is usually cheaper than copper cabling.
- b. It can be installed around sharp bends.
- c. It is easier to terminate and install than copper cabling.
- d. It is able to carry signals much farther than copper cabling.

12. Which standards organization oversees development of wireless LAN standards?
- a. IANA
- b. IEEE
- c. ISO
- d. TIA

13. A network administrator is designing a new network infrastructure that includes both wired and wireless connectivity. In which situation would a wireless connection be recommended?
- a. The end-user device has only an Ethernet NIC.
- b. The end-user device requires a dedicated connection due to performance requirements.
- c. The end-user device needs mobility when connecting to the network.
- d. The end-user device area has a high concentration of RFI.

14. A network administrator is troubleshooting connectivity issues on a server. Using a tester, the administrator notices that the signals generated by the server NIC are distorted and not usable. In which layer of the OSI model does the error occur?
- a. presentation layer
- b. network layer
- c. physical layer
- d. data link layer

15. What type of cable is used to connect a workstation serial port to a Cisco router console port?
- a. crossover
- b. rollover
- c. straight-through
- d. coaxial
