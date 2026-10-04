# Generate Custom Bitstream

To generate a custom bitstream to deploy a deep learning network to your target device, use the dhldl.ProcessorConfig object.

+   1. Create a dhldl.ProcessorConfig object.

+   hPC = dhldl.ProcessorConfig;
2. Setup the path to your design tool. For example, set the path to the Vivado® design tool, enter:
dissetuppath('Toolname','Xilinx Vivado','ToolPath','C:\Xilinx\Vivado\2019.2\bin\vivado.bat');
3. Generate the custom bitstream.

+   dhldl.buildProcessor(hPC);
4. After the bitstream is completed, you can locate the bitstream file at cwd\dhldl_prj\vivado_ip.prj\runs\impl_1\ where cwd is your current working directory. The name of the bitstream file is system_top_wrapper.bit. The associated system_wrapper.mat file is located in the top level of the cwd.

To use the generated bitstream for the supported Xilinx boards, you should copy the system_top_wrapper.bit and system_top_wrapper.mat files to the same folder.

| | | | | |
|---|---|---|---||
| codegen | 7/14/2020 4:10 AM | File folder | | |
| dhldl_prj | 7/14/2020 5:02 AM | File folder | | |
| hdlsrc | 7/14/2020 4:57 AM | File folder | | |
| slprj | 7/14/2020 4:57 AM | File folder | | |
| cksm_Network | 7/14/2020 4:10 AM | MATLAB Data | 6 KB |
| DeployableNetwork | 7/14/2020 4:10 AM | MATLAB Data | 6 KB |
| inputP1_seqimg | 7/14/2020 4:10 AM | MATLAB Data | 1 KB |
| inputP1_seqResult | 7/14/2020 4:10 AM | MATLAB Data | 1 KB |
| OPOthResult | 7/14/2020 4:41 AM | MATLAB Data | 205 KB |
| system_top_wrapper.bit | 7/14/2020 7:09 AM | BIT File | 25,890 KB |
| system_top_wrapper | 7/14/2020 5:06 AM | MATLAB Data | 15 KB |

To use the generated bitstream for the supported Intel boards, you should copy the system_core.rbf, system.mat, system_periph.rbf, and system.so files to the same folder.