14. Sensors are expected to return data in certain ranges, e.g., [1 ... 100].nWhen ranges are violated, rules may be needed of whether to control over to a human or machine when ignoring out-of-bounds data is inappropriate.

15. Sensors may be disposable or serviceable in terms of calibration, sensitivity, or other forms of refresh. Complex and expensive sensors may be repaired instead of replaced.

16. Sensors may be powered in a variety of ways including alternating current (AC), solar, wind, battery, or passively via radio waves.

17. Sensors may be acquired off the shelf or built to specification.

18. Sensors acquire data that can be event-driven, driven by manual input, command-driven, or released at predefined times.

19. Sensors may have a level of data integrity encrypted to void some security concerns.

20. Sensors may have the capability to be authenticated as genuine.

21. Sensor data may be sent and communicated to multiple NoTs. A sensor may have multiple recipients of its data. Sensor data may be leased to one or more NoTs.

22. The frequency with which sensors release data impacts the data’s currency and relevance. Sensors may return valid data state. Sensor data may be ‘at rest’ for long periods of time.

23. A sensor’s precision may determine how much information is provided.
certainty of sensor data should be considered.

24. Sensors may transmit data about the “health” of a system, such as is done in prognosis and health management (PHM).

25. In this document and model, we do not classify sensors as humans; humans are classified as an uEntity, our fourth primitive (see Section 2.4), and/or classified as our fourth element, owner (see Section 2.3). When classified as an uEntity, humans can still act in a sensor-like role by manually feeding data into a NoT’s workflow and dataflow.

26. Humans can influence sensor performance through failure to follow policy, sensor misplacement, or (or their possible analogs). Humans are potential contributors to sensor factors

27. Security is a concern for sensors if they are tampered with, stolen, deleted, dropped, or transmitted insecurely so it can be accessed by unauthorized parties. Building security into specific sensors may or not be necessary for the overall system design.
Reli is a concern for sensors.

# 2.3.2 PRIMITIVE #2: AGGREGATOR

An aggregator is a software implementation based on mathematical function(s) that transforms groups of raw data into intermediate, aggregated data. Raw data can come from any source. Aggregators help in managing ‘big’ data. Basic properties, assumptions, recommendations, and general statements about aggregator include the following: