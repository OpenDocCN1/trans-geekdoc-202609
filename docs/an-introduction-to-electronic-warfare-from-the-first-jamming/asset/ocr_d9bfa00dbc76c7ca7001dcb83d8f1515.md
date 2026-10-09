![](bbox=[0.25, 0.11, 0.75, 0.29])

Figure 2.3 A diagram of the Blumlein transmission line.

a 1 µs pulse, the transmission distance is about 180 m. Since this method requires that the signal travels forward and back, the transmission line length is about 90 m. It should be clarified that, to generate a periodic short pulse, the switching frequency of this circuit does not need to be high as the PRF and is pretty modest (it is only 1 kHz in the previous example). This clever method solves the short pulse generation problem and similar circuits are still in use today.

Sections 2.6 and 2.7 describe a primary requirement of radar: generating a high frequency signal with short pulse width. To satisfy this requirement, special hardware needs to be developed.

# 2.8 High Power Microwave Source: Cavity Magnetron [6, 7]

As discussed in Section 2.5, a radar receives only a fraction of the transmitted energy. Energy equals signal power times the duration of the pulse. Since the pulse is very short, the microwave source must generate very high peak power, even at the megawatt level, although the average power is in the range of kilowatts. Cavity magnetron, a special vacuum tube, is used to generate high-power short-duration microwave radar signal. The working principle of the magnetron shown in Figure 2.4 is passing a stream of electrons through the openings of cavities in a magnetic field and generating an electromagnetic wave through interaction between electron and magnetic field. The frequency of the electromagnetic wave depends on the size of the cavities. In some sense, the way the cavity magnetron generates microwave signals of different frequency is similar to blowing air through the opening of a wind instrument to generate a certain note. An American engineer, Albert W. Hull, proposed the concept of using a magnetic field to control the electronic