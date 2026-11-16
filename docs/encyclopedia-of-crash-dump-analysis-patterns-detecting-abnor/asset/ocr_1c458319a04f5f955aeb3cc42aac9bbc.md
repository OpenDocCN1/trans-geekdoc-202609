MISCV - IA32_MCi_MISC Register Valid
Indicates that the IA32_MCi_MISC register contains additional information regarding the error. When clear, this flag indicates that the IA32_MCi_MISC register is either not implemented or does not contain additional information regarding the error.

ADDRV - IA32_MCi_ADDR register valid
Indicates that the IA32_MCi_ADDR register contains the address where the error occurred.

PCC - Processor Context Corrupt
Indicates that the state of the processor might have been corrupted by the error condition detected and that reliable restarting of the processor may not be possible.

BUSCONNERR - Bus and Interconnect Error BUS{LL}_{PP}_{RRRR}_{II}_{T}_err
These errors match the format 0000 1PPT RRRR IIIL

Concatenated Error Code:
___VAL_UC_EN_MISCV_ADDRV_PCC_BUSCONNERR_1F

This error code can be reported back to the manufacturer. They may be able to provide additional information based upon this error. All questions regarding STOP 0x9C should be directed to the hardware manufacturer.

BUGCHECK_STR: 0x9C_IA32_GenuineIntel

DEFAULT_BUCKET_ID: DRIVER_FAULT

PROCESS_NAME: Idle

CURRENT_IRQL: 2

LAST_CONTROL_TRANSFER: from 80a7fbd8 to 8087b6be

```
STACK_TEXT:
f773d280 80a7fbd8 00000009 00000000 f773d2b0 nt!KeBugCheckEx+0x1b
f773d3b4 80a7786f f7737fe0 00000000 00000000 hal!HalpMcaExceptionHandler+0x11e
f773d3b4 f75a9ca2 f7737fe0 00000000 00000000 hal!HalpMcaExceptionHandlerWrapper+0x77
f78c6d50 8083abf2 00000000 0000000e 00000000 intelppm!AcpiC1Idle+0x12
f78c6d54 00000000 0000000e 00000000 00000000 nt!KiIdleLoop+0xa
```