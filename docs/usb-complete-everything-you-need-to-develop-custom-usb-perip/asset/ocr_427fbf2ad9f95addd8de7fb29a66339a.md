As another example, specifying velocity in centimeters per second requires a Unit value that contains units of both centimeters and seconds. From Table 12-4, the Unit value to use is 1011h. Nibble 0 = 1 to select the SI measuring system, nibble 1 = 1 to select length in centimeters, and nibble 3 = 1 to select time in seconds.

To show how complicated it can get, the Unit value for volts is F0D121h, which indicates the SI Linear measuring system in units of (cm²)(gm)/(sec³)(amp⁻¹). However, remember that the Unit value only specifies the units. All the receiver has to do is identify the Units value and assign the units to received data; there’s no need to do the calculations implied in the Units value.

# Describing the Data’s Size and Format

Two Global items describe the size and format of the report data.

**Report Size** specifies the size in bits of a field in an Input, Output, or Feature item. Each field contains one piece of data.

**Report Count** specifies how many fields an Input, Output, or Feature item contains.

For example, if a report has two 8-bit fields, Report Size is 8 and Report Count is 2. If a report has one 16-bit field, Report Size is 16 and Report Count is 1.

A single Input, Output, or Feature report can have multiple items, each with its own Report Size and Report Count.

# Saving and Restoring Global Items

The final two Global items enable saving and restoring sets of Global items. These items allow flexibility in the report formats while using minimum storage space in the device.

**Push** places a copy of the Global-item state table on the CPU’s stack. The Global-item state table contains the current settings for all previously defined Global items.