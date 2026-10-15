![](bbox=[0.29, 0.157, 0.735, 0.276])

**Fig. (4.14).** Flowchart of the proposed Model.

The detection of sleep apnea from sleep studies generally consists of three basic steps. The first step is to collect data from the patient using SPO2 sensor to determine oxygen concentration in the blood, thermistor, nasal pressure and thoracic and abdomen movement. So, when apnea occurs, the sensors detect decreased nasal pressure, thoracic and abdomen movement as time-interval *T₁* in Fig. (4.15) compared to normal breathing levels and the brain will send some signals to muscle to perform breathing activity and this is detected by EEG. During apnea, there is a sudden change in brain activity which is called arousal as the brain shifts from deep sleep to lighter sleep depicted by time-interval *T₂* in Fig. (4.15). During the arousal event, suddenly the lungs cease to breath and thus the concentration of oxygen in the blood is disrupted causing oxygen desaturation as per the over lapping time-interval *T₂* and *T₃* in Fig. (4.15), which is detected by the SpO2 sensor [16, 17].

![](bbox=[0.31, 0.559, 0.737, 0.695])

**Fig. (4.15).** Timeline of events for when Sleep Apnea occurs.

The raw data collected is feed to user defined software which uses deep learning techniques for analysis. This is the second step in system design. It determines whether sleep apnea is occurring or not and if it is occurring what is its duration and various other information.