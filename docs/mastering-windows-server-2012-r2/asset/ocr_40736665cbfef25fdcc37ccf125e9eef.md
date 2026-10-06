# FIGURE 29.17
RD web access page for VDI

![](bbox=[0.238, 0.103, 0.904, 0.467])

Figure 29.18 shows you the VMs related to the VDI deployment. Notice how one is in Saved state; this happens automatically, preserving resources on the box when they are not in use.

# Figure 29.18
VM view of a VDI deployment

![](bbox=[0.426, 0.566, 0.904, 0.715])

Now it's a fully working VDI solution. We mentioned earlier that VDI has been optimized to work with storage Dedup in Windows Server 2012. To give you a quick idea, when we created our gold image we had 8 GB VHDX file. When we created the two pools, a copy of the gold image for each pool was created. This totals to 24 GB of storage just in VHD files, making it a prime candidate for storage Dedup. You save nearly 60 percent of the storage costs by enabling Dedup. Remember, though, not to place your VDI files on the root volume because you cannot enable Dedup on it. From step 25 onward, we showed how to configure the path to ensure it is not the root volume.