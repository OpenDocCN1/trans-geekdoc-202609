
# Industrial Safety and Protection Systems

Industrial production and utility environments tend to be inherently more hazardous than enterprise network environments. Basically, if a word processor crashes or is compromised, the user might be upset and likely have to do a lot more typing to recover their lost information. However, if an industrial control process is compromised, the organization could suffer loss of productivity, profitability, equipment, a portion of the community, or worse.

As an example, re-examine the simple liquid heating process described in [Figure 1.2](#c01.xhtml#c01-fig-0002) and represented in [Figure 1.28](#c01.xhtml#c01-fig-0028). While this process already has a `process control system` in place to control the temperature of the fluid in the tank, there are several potentially hazardous conditions that could occur if any part of that system malfunctioned or failed. As such, these hazards become part of the risk analysis process that makes it different than a risk assessment performed for an enterprise environment.

![FIGURE 1.28 A simple heating process revisited](images/c01f028.png)

**[FIGURE 1.28](#c01.xhtml#R_c01-fig-0028) A simple heating process revisited**

A quick examination of the process shows several potential hazards:

*   The tank is heated with a gas-fed heating system.
*   The tank contains a liquid that is being heated.
*   The temperature sensor, controller, and solenoid valve all represent single points of failure.

The process control system depicted offers no provisions for monitoring or controlling the gas other than the single solenoid valve. As such, the gas heating system represents a number of potentially explosive conditions, as any leak in the system provides an opportunity for uncontrolled ignition.

For example, if the gas piping `outside the tank` developed a leak, the gas would exit the pipe and fill the space around the leak. If an ignition source is introduced within the area where the gas is accumulating, an explosion will occur. In addition, the unignited gas could become a hazard to humans working in the area as it mixes with the air they are breathing.

There is also no provision for monitoring the condition of the gas within the tank. If the fire at the burner went out, this system would still provide gas to the burner. This would allow the gas to build up inside the tank, posing possible uncontrolled combustion hazards if the burner is reignited or personnel open the tank to examine the burner system.

The liquid being heated inside the tank may also be a source of uncontrolled explosion. As the liquid is heated, its molecules gain energy, move more rapidly, and move farther apart (the liquid expands). At some point, it will change from a liquid state to a gaseous state. When this occurs, the pressure inside the tank increases. If left unvented, the pressure can eventually increase to the point that the tank ruptures—maybe violently. The process control system depicted has no provision for monitoring the amount or condition of the liquid inside the tank.

The fact that many of the process control system's devices are the only devices performing a given function makes them all potential sources of problems. For example, if the temperature sensor fails for any reason, the controller will not receive the feedback signal it needs to control the process properly. If the sensor fails so that the controller thinks the temperature is lower than its set point, it will continue to apply gas to the burner, causing the same hazard conditions described earlier.

If the controller fails, the actuator will not receive the error correction signal it requires to control the gas flow and heating process. Depending on the nature of the failure and the design of the final control element, the tank could be allowed to overheat and produce the potential explosion hazards described earlier. Ideally the design of the system is such that any failure would cause the final control element to `fail safe` (shut down the gas flow to the burner).

As you can see, even simple processes like the one presented here provide multiple potential threats to equipment, personnel, and productivity. As such, industrial safety systems must be added to the basic process control system to mitigate the risks pointed out by these concerns. This concept is discussed in detail in [Chapter 10](#c10.xhtml), "ICS Security Monitoring and Incident Response." The remainder of this chapter will be used to introduce safety instrument systems and discuss common safety and protection subsystems.

## Safety Instrument Systems

`Safety instrument systems` (`SISs`) are basically automated process control systems specifically designed to monitor and control conditions in and around the process that have been defined as unsafe or potentially unsafe. The SIS is typically created as an integral part of the overall ICS package (but not the same components). The SIS must be able to successfully perform its functions when the process control system fails. Together these two systems are referred to as the `integrated control and safety system` (`ICSS`).

Like the ICS, the SIS is composed of sensors, controllers, and actuators. What the SIS does and to what level is determined through a formal `hazard and operability` (`HAZOP`) study performed as part of the `process hazard analysis` (`PHA`) process required for every industrial process. This process is used to identify hazardous scenarios that require `safety instrumented functions` (`SIFs`) to mitigate. The IEC 61508, 61511, and ANSI/ISA 84 standards define a SIF as "a safety function with a specific `Safety Integrity Level` (`SIL`) which is necessary to achieve functional safety." This process will also be discussed in detail in [Chapter 10](#c10.xhtml).
