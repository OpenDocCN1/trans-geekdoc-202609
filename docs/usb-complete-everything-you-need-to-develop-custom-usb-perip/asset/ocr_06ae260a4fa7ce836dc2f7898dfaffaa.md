![](bbox=[0.19, 0.11, 0.83, 0.63])

Figure 16-5: The Power Options Properties in Windows' Control Panel enable users to specify power-saving schemes that determine when USB devices must enter the Suspend state.

the S3 state, false device removal and arrival notifications on resuming, resetting of devices during suspend and resume, and failure to resume fully.

To enable or disable remote wakeup capability for a specific device that supports remote wakeup, in Windows' Device Manager, select the device, right-click, select Properties > Power Management, and check or uncheck Allow this device to bring the computer out of standby.

On some early Intel host controllers, a suspended root port didn't respond correctly to a remote wakeup. In addition, using remote wake-up requires