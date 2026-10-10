
# When selecting your business location, research the area you are considering

One of the key issues related to facility security would be the crime rate in the area you are considering. If an area has a high crime rate, it may not make sense to build or lease there because your organization may experience theft of or damage to its assets—or more importantly, your employees may not be safe in such an area.

Outside of crime rate, another consideration is whether the area is in a flood zone. Look into the history of floods and other natural disasters in the area because it may not be worth the risk of building a facility in an area that is prone to disasters.

Another point to consider when selecting your facility is how long it takes emergency services such as ambulance and the fire department to reach that area. If the area is difficult to reach, there is a potential safety risk to your employees and customers.

## Lighting and Windows

Ensure that the facility has proper lighting and that entrances and exits are properly marked, well lit, and accessible. Be sure that the parking area, as well as the pathways to and from it, have adequate lighting to help keep employees and visitors safe when arriving or leaving the facility.

It is critical that you equip the facility with emergency lighting units (see [Figure 14-1](#ch14.xhtml#ch14fig1)) that have a backup power source such as a battery. This battery does not have to be large and supply long periods of power; it only needs to power the emergency lights so personnel can safely evacuate the building.

![Image](f0587-01.jpg)

**FIGURE 14-1**  
Emergency lighting with backup power should be used in case the building loses power.

If you are in an area that has a high level of crime or vandalism, you may have to invest in windows with wire mesh or bars to deter vandals from smashing the windows to enter the facility.

## Doors, Windows, and Walls

When constructing your facility, ensure you plan the placement of facility entrances in such a way that they can be closely monitored, and be sure to offer a safe entrance and exit for employees. In highly secure environments, all entrances should have a security desk close by where security personnel can monitor who is coming and going.

Be sure that entrances to secure areas use secure doors that have hinges with pins that cannot be removed. Also ensure that each of the doors has a panic bar on it so that it can be opened with ease in case of emergency.

Verify that the walls go from the true floor to the true ceiling instead of using partitions to create different rooms. If a partition is used that does not go from the true floor to the true ceiling, then it is possible for an intruder to gain access to the secure area through the crawl space above a door (see [Figure 14-2](#ch14.xhtml#ch14fig2)) or below the floor.

![Image](f0588-01.jpg)

**FIGURE 14-2**  
Ensure that secure areas have walls that go from the true floor to the true ceiling.

If you do have ventilation ducts or utility tunnels in the facility, it is recommended that you place motion sensors in these areas so that you know if someone is compromising your facility by using them. The following are some common types of motion detectors:

- **Closed-circuit sensor** With a `closed-circuit sensor`, an electrical circuit exists that, when broken, triggers the alarm, indicating that someone is in the area. This is commonly used in windows (with tiny wires) so that if the window is smashed, the circuit is broken and the alarm signals.
- **Pressure mat sensor** You can also use pressure mats that are activated after working hours so that if an intruder enters the facility and walks on the material, the alarm will go off.
- **Proximity sensor** A `proximity sensor` emits a magnetic field that it monitors. When someone approaches, the motion of the intruder changes the field's frequency. The system detects this and sets off the alarm. This kind of motion sensor is prone to many false alarms.
- **Photoelectric sensor** With a `photoelectric sensor`, a beam of light is emitted from a transmitter to a receiver. When an intruder breaks the beam of light, it trips the alarm.

## Safety Concerns

A large part of physical security deals with ensuring you are creating a safe environment for your employees. For example, you want to ensure you have proper lighting in the facility and parking lot area to deter burglars. The following are some other examples of physical security components that add safety:

- **Signs** Ensure that the facility has proper signage labeling all exits so that employees can locate the exits quickly during an emergency.
- **Escape route** Ensure that escape routes have been created in case of emergencies such as fire or flooding.
- **Escape plans** Create escape plans and communicate them to all employees.
- **Drills** Perform regular drills, such as fire drills, to test escape plans and the timeliness of all employees using the appropriate escape route.
- **Testing controls** Test all security controls to ensure their effectiveness. For example, be sure to test fire alarms and fire extinguishers on a regular basis.

# CERTIFICATION OBJECTIVE 14.02

# Physical Access Controls

Once you have selected the location of the facility, you need to look at how to control access to the facility. This section addresses important concepts of physical access control—be prepared for questions on the Security+ exam about physical access controls.

## INSIDE THE EXAM

### The Value of Physical Security

For the Security+ exam, know that a hacker can easily bypass the security of a system if they can physically get to a system or server. Any security features of the operating systems are only valid if the operating system is running, so most hackers who wish to bypass the security of the operating system simply boot off a live disc.

In order to prevent this from happening, you need to implement physical security within the organization to ensure that you control who gains physical access to the systems. Remember for the exam that physical security is an important method to help keep unauthorized individuals from gaining access to critical systems and networks.

## EXERCISE 14-1

![Images](video.jpg)

### Gaining Access to a System with No Physical Security

In this exercise, you will boot off the Windows 10 installation media to create your own administrative account on a Windows 10 system that can then be used to gain access to the system. The point of this exercise is to show you that if someone can get physical access to a system, they can easily bypass most security controls. Ensure you are working on a test Windows 10 system and not on a production system.

1. On the Windows 10 VM, boot off the Windows 10 installation media (either ISO file, a DVD, or USB drive).
2. Once you're at the Windows Setup dialog box that asks you the language to install, choose `shift`-`f10` to open a command prompt.
3. Type the following commands to locate the partition where Windows was installed. You are looking for the drive that contains the Windows directory (it is most likely the `D:` drive or `E:` drive).

![Images](p0590-01.jpg)

4. In the command prompt, you are going to replace the `utilman.exe` file on the hard drive of the Windows system with `cmd.exe` by typing the following commands.

(Note that whichever drive has the Windows directory is the drive you use in the following commands.)

![Images](p0591-01.jpg)

In my case, the `E:` drive had the Windows directory, so I used the following commands:

![Images](p0591-02.jpg)

5. Close the command prompt and then click the Close button on the Windows Setup screen.
6. You are informed that the system will restart. You are then asked if you're sure you wish to cancel. Remove the installation media and then choose Yes.
