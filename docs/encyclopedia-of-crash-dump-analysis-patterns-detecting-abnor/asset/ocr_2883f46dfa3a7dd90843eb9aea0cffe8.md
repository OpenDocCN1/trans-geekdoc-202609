# No System Dumps

This is a corresponding pattern similar to **No Process Dumps** (page 740) where the system bluescreens either on demand or because of a bugcheck condition but no kernel or complete dumps are saved. In such cases, we would advise checking free space on a drive where memory dumps are supposed to be saved. This is because crash dumps are saved to a page file first and then copied to a separate file at boot time, by default to memory.dmp file<sup>157</sup>. In case we have enough free space but not enough page file space we might get an instance of **Truncated Dump** (page 1015) or **Corrupt Dump** (page 137) patterns.

# Comments

In some cases of severe corruption or system malfunction, the system doesn’t have any chance to execute system code to save a dump and display a blue screen. To check this case, it is recommended to disable “Automatically Restart” option in Control Panel. I once experimented with a driver by calling a user space code from kernel mode and from it tried to call a GDI32 function. The system rebooted instantly without BSOD screen.

<sup>157</sup> Savedump.exe and Pagefile, Memory Dump Analysis Anthology, Volume 1, page 628