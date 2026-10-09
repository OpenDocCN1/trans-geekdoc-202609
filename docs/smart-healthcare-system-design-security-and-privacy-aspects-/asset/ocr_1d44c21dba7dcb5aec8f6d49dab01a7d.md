![](bbox=[0.15, 0.08, 0.85, 0.38])

**Figure 10.7** Raspberry Pi board (model RasPi B).

IoT device to collect the data from six sensors deployed in the test section, then to process information, and send this information to the end-user (monitoring server).

The output of these sensors is voltages, and the RasPi converts the out-put data into pressure using the digital manometer and Equation (10.1). For a given voltage (V, milli-volts), the pressure (p, mbar) is given by:

Pressure (P) = (261.95 * V) - 129.96 (10.1)

Where V is the aggregated data from a single sensor. The RasPi was integrated with Wi-Fi, ethernet port and Adafruit IO as an IoT platform. It also included USB ports, general purpose input/output (GPIO) pins to interface with LEDs, high definition multimedia interface (HDMI) port, and others. The digital manometer device includes calibration facilities and can be used to measure low-pressures [4].

# ### 10.2.5 Custard Pi Add-On Board

The Cpi board is a range of cards that connect to the GPIO pins of the RasPi to provide a variety of options [19]. The RasPi GPIO does not support any analog inputs and thus, Cpi was added. The Cpi has 8 analog channels with 12-bit analog-to-digital (ADC). The Cpi 1 and 2 use non-stackable connectors. Hence, once the board is fitted into the RasPi, nothing else can