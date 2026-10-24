This is the code to retrieve the structure:

```
```cpp
BOOLEAN Result;
HIDD_ATTRIBUTES Attributes;

// Set the Size member to the number of bytes
// in the structure.
Attributes.Size = sizeof(Attributes);
Result = HidD_GetAttributes
    (DeviceHandle,
    &Attributes);
```
```

The application can then compare the Vendor ID and Product ID to the desired values:

```
```cpp
const unsigned int VendorID = 0x0925;
const unsigned int ProductID = 0x1234;

if (Attributes.VendorID == VendorID) {
    if (Attributes.ProductID == ProductID) {
        // The Vendor ID and Product ID match.
    }
    else {
        // The Product ID doesn't match.
        // Close the handle.
    }
}
else {
    // The Vendor ID doesn't match.
    // Close the handle.
}
```
```

# Visual Basic

The HIDD_ATTRIBUTES structure contains information about the device:

```
```vb
<StructLayout(LayoutKind.Sequential)> _
Public Structure HIDD_ATTRIBUTES
    Dim Size As Integer
    Dim VendorID As Short
    Dim ProductID As Short
    Dim VersionNumber As Short
End Structure
```
```