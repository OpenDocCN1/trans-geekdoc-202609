![](bbox=[0.08, 0.09, 0.92, 0.32])

FIGURE 1.14 Single-phase asynchronous driven by an inverter chopper, power part.

![](bbox=[0.12, 0.39, 0.92, 0.63])

FIGURE 1.15 Single-phase asynchronous parameters.

Repeating Sequence Stair: This block represents the speed reference vector of output values: [400 800]. Sample time: 4.

Fen: This block represents the function of the reference that composes the PWMcontrolling the inverter.

The inputs of the “Fen” block consist of the amplitude and frequency, both sourced from the multiplexer (mux) component. These parameters are essential in controlling the reference PWM function, enabling precise modulation of the output signals that drive the single-phase asynchronous motor.

Repeating Sequence: This block represents the carrier signal that constitutes the other part of the PWM controlling the inverter. Time values: [0 .25 .5 .75 1]/5000 and output values: [0 → 1 0 1 0].