
(DPD). The DPD is obtained from the three paths: all registers to all registers, all inputs to all registers and all registers to all outputs.

If the time period which has been set meets the setup slack and hold slack requirements, then that time period/constraint is saved for the further implementation of the design for layout post timing analysis. Figure 5.9 shows DIT-FFT design layout routed over the chosen FPGA for N=4. From this we can say that timing fixture plays a greater role for the routing when we compare DIT-FFT for N=4 post timing layout with N = 8. Here cells or nets are placed according to delay constraints. Timing fixture also provides information about exact path connections, buffer/inverters connection, etc. This way we can also say that DIT-FFT for N=8 routing does differ from N = 2 and N = 4, as seen in Figure 5.10. Once the design has been routed, we can have the utilization of different cell, slices, BRAMs, FFs, etc., from the fabric, as displayed in Table 5.4. This helps the user to visualize if the RTL design written is favorable with the availability of BRAMs, FFs, etc., from the chosen fabric/FPGA.

## 5.5 Result and Discussion

The values related to timing are the parameters obtained by the design for several input sampling sizes (N = 2, 4, & 8). After synthesis of the design, the utilization parameters for FPGA are shown in Table 4.3. From the available 134600 LUTs, 365 BRAM tiles, and 740 DSP blocks, 0.7% of LUT, 75% of BRAM tiles and 2.97% of DSP has been utilized for N = 8 sample inputs. Similarly, for N = 4, 0.18% of LUTs, 25% of BRAM tiles, and 1.49% of DSP blocks have been utilized; for N = 2, 0.05% of LUTs, 10% of BRAM tiles, and 0.41% of DSP blocks have been utilized. Post timing fixation values in Table 4.4 confirm that the proposed DIT-FFT architecture designed with offset binary representation for complex twiddle factors justifies the synthesis and the time period required for four different paths subsequently divided to meet the overall design. With this, we can ensure that the design is error free with respect to pin to pin time stipulation.

## 5.6 Conclusion

Timing analysis is an important pathway towards signing off any chip because engineers must be aware how fast the chip/task is going to run, how fast the data is reaching the output from input ports of design. This work shows a practice towards the synthesis and timing analysis of DIT-FFT architecture for VLSI Signal Processing modules. With strict adherence to the Simulation-Synthesis guidelines and by following the Static timing analysis procedure rules, the designed modules met timing at 24ns, 20ns and 15ns for different values of N such as 8, 4 and 2, respectively. It is also found that the proposed design after timing works efficiently with consumable resources of 780 LUTs as logic and 257 BRAM as tile. The Power report confirms that the design consuming 0.163W of on chip power after implementation and timing closure is a notable efficient power value. The high-speed and low-power performances of the proposed architecture make it suitable for wide-ranging on-chip signal processing applications.

## References

- 1. Siba Kumar Panda; Konasagar Achyut and Swati K. Kulkarni. “Industry 4.0: A Road Map to Custom Register Transfer Level Design”. In *Advances in Industry 4.0: Concepts and Applications*, edited by M. Niranjanamurthy, Sheng-Lung Peng, E. Naresh, S. R. Jayasimha and Valentina Emilia Balas, Berlin, Boston: De Gruyter, 2022, pp. 21-50.
- 2. Changeia Ankur; Zaveri Mazad and Verma Deepak, FPGA implementation of high-performance, resource efficient Radix-16 CORDIC rotator based FFT algorithm, *Integration, the VLSI Journal*; 2020; 1-12.
- 3. Ganjikunta Ganesh Kumar and Sahoo Subhendu Kumar, An area-efficient and low-power 64-point pipeline Fast Fourier Transform for OFDM applications, *Integration, the VLSI Journal*, 57, 2017; 125-131.
- 4. Rauf Adnan; Pasha Mohammed Adeel and Masud Shahid, Towards Design and automation of scalable split-radix FFT Processor for High Throughput Applications. *Microprocessors and Microsystems*, Elsevier. 65, 2017; 148-157.
- 5. Kar Subhajit; Ganguly Madhabi and Das Saptarshi, Using DIT FFT Algorithm for Identification of Protein Coding Region in Eukaryotic Gene. *Biomedical Engineering: Applications, Basis and Communications*, 31(1), 2018; 1-10.
- 6. Panda S.K. and Panda D.C, Developing High-Performance AVM Based VLSI Computing Systems: A Study. In: Pattnaik P., Rautary S., Das H., Nayak J. (eds.) *Progress in Computing, Analytics and Networking. Advances in Intelligent Systems and Computing*, 2017;710.
- 7. Prabhu E.; Mangalam H. and Karthick S., Design of area and power efficient Radix-4 DIT FFT butterfly unit using floating point fused arithmetic. *Journal of Central South University*, Springer, 23, 2016;1669-1681.
- 8. Neuenfeld Renato; Fonseca Mateus and Costa Eduardo, Design of Optimized Radix – 2 and Radix – 4 Butterflies from FFT with Decimation in Time. In: *VII Latin American Symposium on Circuits and Systems (LASCAS)*, 2016; 171-174.
- 9. Blake Anthony and Hunter Matt, Dynamically Generating FFT Code. Journal of Signal Processing Systems, Springer. 76, 2014; 275–281.
- 10. Qadeer Shaikh; Khan Mohammed Zafar Ali; Sattar Syed Abdul and Ahmed, A, Radix – 2 DIT FFT with Reduced Arithmetic Complexity. In: International Conference on Advances in Computing, Communications and Informatics (ICACCI), 2014; 1892–1896.
- 11. Paul Augusta Sophy Beullet; Raju Srinivasan and Janaki Raman Raja, Low power reconfigurable FP-FFT core with an array of folded DA butterflies. EURASIP Journal on Advances in Signal Processing, 2014; 144: 1–17.
- 12. Ma Zhen-guo, Yu Feng; Ge Rui-feng and Wang Ze-ke, An efficient radix-2 fast Fourier transform processor with ganged butterfly engines on field programmable gate arrays. Journal of Zhejiang University SCIENCE C, 12(4); 2011; 323–329.
- 13. Fonseca Mateus Beck; A Eduardo; Costa Da Cesar and Martins Joao B. S, Design of power efficient butterflies from Radix-2 DIT FFT using adder compressors with a new XOR gate topology. Analog Integr Circ Sig Process, Springer Science Business Media, LLC. 73(3);2012;945–954.
- 14. Saponara Sergio; Rovini Massimo; Fanucci Luca; Karachalios Athanasios; Lentaris George and Reisis Dionysios, Design and Comparison of FFT VLSI Architectures for SoC Telecom Applications with Different Flexibility, Speed and Complexity Trade-Offs. Circuits, Systems and Signal Processing, Springer, 31;2011;627–649.
- 15. Huang Walter; V David and Anderson, Modified Sliding-Block Distributed Arithmetic with Offset Binary Coding for Adaptive Filters. Journal of Signal Processing System, Springer Science Business Media, LLC. 63;2010; 153–163.
- 16. Parhami B., Computer Arithmetic: Algorithms and Hardware Designs. 2nd Edition, Oxford University Press, New York, 2010. ISBN No. 978-0-19-532848-6.
- 17. Chadha Rakesh and Bhasker J., Static Timing Analysis for Nanometer Designs: A Practical Approach. Springer-Verlag US, 2009; ISBN No. 978-0-387-93819-6.
- 18. Mano M. Morris and Ciletti Michael D., Digital Design. Fourth Edition. Pearson Education, Inc. 2008; ISBN No. 978-8131714508.
- 19. Parhi Keshab K., VLSI Digital Signal Processing Systems Design and Implementation. A Wiley-Interscience Publication, 1999; ISBN No. 978-0471241867.
- 20. Deepika Ghai, Suman Lata Tripathi, Sobhit Saxena, Manash Chanda, Mamoun Alazab, Machine Learning Algorithms for Signal and Image Processing, Wiley IEEE Press, 2022, ISBN: 978-1-119-86182-9
- 21. Dasari L. Prasanna; Suman Lata Tripathi, “Machine and Deep-Learning Techniques for Text and Speech Processing,” in Machine Learning Algorithms for Signal and Image Processing, IEEE, 2023, pp. 115-128, doi: 10.1002/9781119861850.ch7

## Artificial Intelligence-Based Active Virtual Voice Assistant

Swathi Gowroju*, G. Mounika, D. Bhavana, Shaik Abdul Latheef and A. Abhilash

1CCSE, Sreyas Institute of Engineering and Technology, Hyderabad, Telangana, India

### Abstract

As we all know, there are many voice assistants which determine the user’s intent which can be identified by the user input in spoken or textual form. Unlike the other voice assistants, here we can open multiple tabs or apps concurrently. Though the input is taken, the voice assistant will be activated till the user says to exit the app. It is a very useful tool for reminders, searching, opening, and saving applications as the user needs. The proposed virtual-based voice assistant helps people to communicate with the computer, which indeed saves time. The processes which are to be implemented will work under AI modules like speech recognition, pyttsx3, and operating system. This new version has added three features. They are movie recommender, book recommender, and some Covid protection features. The movie recommender and the book recommender work on the users’ interests. For example, the movie recommender helps users to find the best movie according to their interest in different genres and displays it based on the IMDB ratings and the number of users watching. This also includes series recommenders too, like web series. The same process is applied to book recommender. The books are displayed according to user interests based on author and genres (romcoms, thrillers, etc.). Because of the rapid spread of Covid-19, precautions should be taken mandatorily. All the Covid symptoms are stored in our database, through which users can receive information and advice based on their symptoms. All these processes work under AI modules like speech recognition, pyttsx3, and operating system.

Keywords: Speech recognition, pyttsx3, operating system

*Corresponding author: swathigowroju@sreyas.ac.in
