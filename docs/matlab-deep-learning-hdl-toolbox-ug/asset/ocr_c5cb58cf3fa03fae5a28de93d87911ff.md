![](bbox=[0.06, 0.12, 0.86, 0.31])

# # Manually Enable Multiple Frame Mode

After the deep learning network has been deployed, you can manually enable the multiple frame mode by writing the number of frames through a network configuration (NC) port. To manually enter the multiple frame mode at the MATLAB command line enter:

```
dnfpga.hwutils.writeSignal(1, dnfpga.hwutils.numToHex(addrMap('nc_op_image_count'))),15,hT);
```

The function addrMap('nc_op_image_count') returns the AXI register address for nc_op_image_count, 15 is the number of images and hT represents the dl. Class that contains the board definition and board interface definition. For more information about the AXI register addresses, see "Deep Learning Processor Register Map" on page 12-9.

# ## See Also

compile | dldl.Target | dldl.Workflow

# ## More About

+   * Prototype Deep Learning Networks on FPGA and SoCs Workflow" on page 5-2