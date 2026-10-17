
### The Software Approach to Firmware Acquisition

In the software approach to dumping `UEFI` firmware from the target system, you read the contents of the `SPI` flash from the operating system. You can access modern systems’ `SPI` controllers through registers in the `PCI configuration space` (a block of registers that specify device configuration on the PCI bus). These registers are memory mapped, and you can read and write to them using regular memory read and write operations. In this section, we’ll demonstrate how to locate these registers and communicate with the `SPI` controller.

Before we proceed, you should know that the location of an `SPI` register is chipset specific, so in order to communicate with an `SPI` controller, we need to refer to the chipset dedicated to the platform we’re targeting. In this chapter, we’ll demonstrate how to read the `SPI` flash on chipsets in Intel’s 200 Series (the location of `SPI` registers can be found at [www.intel.com/content/www/us/en/chipsets/200-series-chipset-pch-datasheet-vol-2.html](https://www.intel.com/content/www/us/en/chipsets/200-series-chipset-pch-datasheet-vol-2.html)), which are the latest chipsets for desktop systems at the time of this writing.

- [费曼学习法](https://wiki.example.org/feynmans_learning_method)的灵感源于诺贝尔物理奖获得者 Richard Feynman。

1. 运用费曼技巧，你只需花上 `20 min` 就能深入理解知识点，而且记忆深刻，难以遗忘。

```
if (condVar > someVal) {console.log("xxx")}
```

一旦我们通过设置 HSFC 寄存器的 FGO 字段启动 SPI 循环，就可以通过查看 `hardware sequencing flash status (HSFS)` 寄存器来确定循环何时完成。该寄存器由多个字段组成，提供所请求操作的状态信息。在 `Table 19-2` 中可以看到用于读取 SPI 镜像的 HSFS 字段。

**Table 19-2:** The SPI Register HSFS Fields

| Field offset | Field size | Field name | Field description |
| --- | --- | --- | --- |
| `0h` | `1` | `FDONE` | Flash cycle done |
| `1h` | `1` | `FCERR` | Flash cycle error |
| `2h` | `1` | `AEL` | Access error log |
| `5h` | `1` | `SCIP` | SPI cycle in progress |

The `FDONE` bit is set by the chipset when the previous flash cycle (initiated by the HSFC register’s `FGO` field) is complete. The `FCERR` and `AEL` bits indicate that an error has occurred during the SPI flash cycle and that the returned data may not contain valid values, respectively. The `SCIP` bit indicates that the flash cycle is in progress. We set the `SCIP` by setting the `FGO` bit, and the `SCIP` clears when the value of `FDONE` is `1`. Based on this information, we can determine that the operation we initiated has completed successfully when the following expression is true:

```
(FDONE == 1) && (FCERR == 0) && (AEL == 0) && (SCIP == 0)
```

#### The FDATAX Registers

The `array of flash data (FDATAX)` registers hold the data to be read from or written to the SPI flash. Each register is 32 bits, and the total number of `FDATAX` registers in use depends on the amount of bytes to transfer, which is specified in the HSFC register’s `FDBC` field.

#### Reading Data from the SPI Flash

Now let’s put together all this information and see how to read data from the SPI flash using these registers. First, we locate the Root Complex Registers Block, from which we can determine the base address of SPI memory‑mapped registers and get access to those registers. By reading the `FREG1` SPI register, we can determine the location of the BIOS region on the flash—that is, the BIOS starting address and BIOS limit.

Next, we read the BIOS region using the SPI registers just described. This step is demonstrated in `Figure 19-5`.

![image](img/19fig05.jpg)

*Figure 19-5: Reading data from the SPI flash*

First, we set `FADDR` to the linear address of the flash memory region that we want to read ➊. Then we specify the total number of bytes to read from flash memory by setting the `FDBC` field ➋ of the flash control register. (A value of `111111b` would read 64 bytes per cycle.) Next we set the `FCYCLE` field ➌ with the `00b` value, which indicates the read cycle and sets the `FGO` bit ➍ that starts our flash reading operation.

Once we set the `FGO` bit, we need to monitor the flash status register to know when the operation is complete. We can do this by checking the `FDONE`, `FCERR`, `AEL`, and `SCIP` fields ➎. Once the read operation is finished, we read flash data from the `FDATAX` registers ➏. The `FDATAX[1]` register provides us with the first 4 bytes of flash memory at the target address specified in the `FADDR` register; `FDATAX[2]` provides us with the second 4 bytes of flash memory, and so on. By repeating these steps and incrementing the `FADDR` value by 64 bytes in each iteration, we read the whole BIOS region from the SPI flash.

#### Considering the Drawbacks of the Software Approach

The software approach to BIOS firmware dumping is convenient because it doesn’t require you to be physically present; with this method, you can read the contents of the SPI flash remotely. But it isn’t robust against an attacker who has already compromised the system firmware and can execute malicious code in SMM.

As we’ve noted, the HSFC register has an `FSMIE` bit that triggers an SMI when the flash cycle completes. If an attacker has already compromised SMM and is able to set the `FSMIE` bit before the firmware acquisition software sets the `FGO` bit, then the attacker will receive control once the SMI is generated and will be able to modify the contents of the `FDATAX` registers. As a result, the firmware acquisition software will read forged values from `FDATAX` and won’t be able to get an original image of the BIOS region. `Figure 19-6` demonstrates this attack.

![image](img/19fig06.jpg)

*Figure 19-6: Subverting a software BIOS acquisition via SMI*

Before the reader sets the `FGO` bit ➋ in the flash control register, the attacker writes 1 to the register’s `FSMIE` bit ➊. Once the cycle is finished and data is written back to the `FDATAX` registers, an SMI is triggered and the attacker receives control ➌. Then the attacker modifies the contents of the `FDATAX` registers ➍ to conceal the attack on the BIOS firmware. After regaining control, the reader will receive fake data ➎ and won’t detect the compromised firmware.

This attack demonstrates that the software approach doesn’t provide a 100 percent reliable solution for firmware acquisition. In the following section, we’ll discuss the hardware approach to obtaining system firmware for forensic analysis. Conducting forensic analysis by physically attaching a device to the SPI flash avoids the possibility of the attack depicted in `Figure 19-6`.

### The Hardware Approach to Firmware Acquisition

To guarantee we have acquired the actual BIOS image stored on the SPI flash and not one already compromised by an attacker, we can use the hardware approach. With this approach, we physically attach a device to the SPI flash memory and read its contents directly. This is the best solution because it’s more trustworthy than the software approach. As an extra benefit, this approach allows us to obtain other firmware stored on the SPI flash, like ME and GBE firmware, which might not be accessible with the software approach due to restrictions enforced by the SPI controller.

The SPI bus on modern systems allows multiple masters to communicate with the SPI flash. For instance, on systems based on the Intel chipset, there are generally three masters: the host CPU, the Intel ME, and GBE. These three masters have different access rights to different regions of the SPI flash. On most modern platforms, the host CPU can’t read and write to the SPI flash region containing the Intel ME and GBE firmware.

`Figure 19-7` demonstrates a typical setup for obtaining the BIOS firmware image by reading the SPI flash.

![image](img/19fig07.jpg)

*Figure 19-7: A typical setup for dumping the SPI flash image*
