vehicle state and is related to the detection of an anomaly or a failure in a critical component of the vehicle. The trigger event, in this case, is the activation of an alarm in the vehicle cockpit. Further developments of the VCM module are mainly addressed to the introduction of predictive/forecasting functions capable of detecting incipient risks and originating different operational states (e.g. regular, cautious/degraded and emergency/critical) as in similar referenced systems (Xu et al 2021).

# 30.5.4 Sensing Layer and Perception Module

The sensing layer provides the vehicle (and the driver) with real-time information about the operating environment. It is designed to improve or augment the operator’s capabilities by means of sensors such as: CCTV cameras, ultrasonic, radar, Radio Frequency Identification (RFID), etc. The sensing layer implemented in the vehicle considered in this research involves the systems described below.

GPS tracking system: The GPS tracking system is based on the commercial GPS module previously described and is designed to constantly track the vehicle trajectory through the determination of the instant position and the current speed vector. Such information is constantly transferred to the VCM module to detect divergences from the trajectory assigned to the vehicle.

Vision system: The vision system implements four FLIR Blackfly colour cameras for rear, right, front and left directions. The cameras are equipped with a 1/1.2" sensor for a maximum resolution of 1,900×1,200 at 41 frames per second. F2.4 lenses are coupled to the cameras, yielding a horizontal field-of-view of 75°. The information from the vision system can be transferred to the centralized traffic control system when an object is detected that prevents following the assigned trajectory.

Obstacle detection: Obstacle detection plays a critical role in enhancing the safety of the transport system. The system is based on ultrasonic obstacle detection technology which is now mature and widely employed in the automotive and industrial sector and consists in transmitting acoustic waves at a frequency between 25 and 50kHz (above the human hearing range) at a pre-established time length and spacing. The presence of an obstacle is then detected through the variations in the reflected pulses which are converted into electrical signals and passed to a signal processing system for their interpretation.

# 30.5.5 Actuation Module

The actuation module controls all the actuators of the vehicle and has the fundamental function of translating the manoeuvres requested by the driver acting on the pedals and steering wheel into actual movements of