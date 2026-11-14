```
if (PloutusService.MemoryData.GuiEnable)
{
    if (KeyData.KeyCode == System.Windows.Forms.Keys.F1)
    PloutusService.Keyboard.ProcessCommandGui(1);
    if (KeyData.KeyCode == System.Windows.Forms.Keys.F2)
    PloutusService.Keyboard.ProcessCommandGui(2);
    if (KeyData.KeyCode == System.Windows.Forms.Keys.F3)
    PloutusService.Keyboard.ProcessCommandGui(3);
    if (KeyData.KeyCode == System.Windows.Forms.Keys.F4)
    {
    PloutusService.Program.NCRV.UIDisable(); ①
    PloutusService.Program.NCRV.ClearText();
    PloutusService.MemoryData.Command = System.String.Empty;
    }
    if (KeyData.KeyCode == System.Windows.Forms.Keys.F5)
    PloutusService.Program.NCRV.KeyControlUp();
    if (KeyData.KeyCode == System.Windows.Forms.Keys.F6)
    PloutusService.Program.NCRV.KeyControlDown();
    if (KeyData.KeyCode == System.Windows.Forms.Keys.F7)
    PloutusService.Program.NCRV.KeyControlNext();
    if (KeyData.KeyCode == System.Windows.Forms.Keys.F8)
    PloutusService.Program.NCRV.KeyControlBack();
}
```

The second form of interaction is via the pinpad, where the attackers enter a combination
of numbers in order to bring up the malware interface. In order to accomplish this, the
malware needs to use the XFS APIs, as shown earlier in Figure 20-5, where the command
PIN_GET_DATA is reading the information entered.

The last form of interaction is via the ATM's card reader. Similar to the pinpad strategy,
the malware uses the XFS APIs, but this time to interact with the target device and read the
data on tracks 1 and 2 from the debit card. If the magic number expected by the attackers is
provided, the GUI will be activated. In cases like Ripper, that's the trigger to start emptying
the ATM.

# How the Information or Money Is Stolen

In cases where the cardholder data is the target, if skimmers are used, these devices already
come with wireless protocols such as GSM that allow the attackers to receive the stolen
information in real time. When malware is used to accomplish this goal, as in the cases of
PanDeBono or NeaBolsa malware, the stolen information is copied into the attackers' USB
that's plugged into the ATM.

Regarding cash, all the threats interact with the ATM dispenser (no need for an exploit or
authentication bypass) just by using the XFS APIs, and without any restrictions the
dispenser will start providing money. Refer to the section “ATM Malware
Countermeasures,” later in this chapter, for recommendations of how to mitigate these
risks.