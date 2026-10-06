# CHAPTER 22 ADDING MORE LOCATIONS: SITES IN ACTIVE DIRECTORY

Once you tell AD all these things about sites, a souped-up version of the Knowledge Consistency Checker called the Inter-Site Topology Generator (ISTG) identifies links to use and when to use them. One DC at each site is automatically designated as the ISTG.

You can identify which server is the ISTG by viewing the NTDS Sites properties sheet. Select the site, and double-click NTDS Site Settings to access this page. However, the ISTG needs very little oversight.

An important function of the ISTG is to assign bridgehead servers. Additionally, you can override the ISTG by assigning preferred bridgehead servers.

# Bridgehead Servers

A bridgehead server is a DC within a site that will replicate to DCs in other sites. Every site will have only one active bridgehead server at any time.

The Inter Site Topology Generator designates a DC as a bridgehead server and periodically checks this DC to ensure it's operational. If this DC crashes or is taken offline, the ISTG will automatically designate another server as the bridgehead server.

At least this is the way it works normally, assuming you haven't overridden the ISTG by assigning a preferred bridgehead server.

# PREFERRED BRIDGEHEAD SERVERS FOR EXCLUSION MANAGEMENT

Occasionally, you may want to exclude a DC from becoming a bridgehead server. For example, a DC may be close to full capacity with the processing power hovering close to 80 percent and the paging file usage excessively high. When the ISTG designates this as the bridgehead server, the processing power could peak at 100 percent, significantly impacting the performance of other functions on the server.

> Notice the subtlety. You aren't picking a DC as a preferred bridgehead server because you want it to be the bridgehead server as much as you don't want another DC to be a bridgehead server. In other words, you select preferred bridgehead servers to exclude one or more DCs from the selection process. designate any DC as a preferred bridgehead server, the ISTG will only pick preferred bridgehead servers to fill this role.

You can't exclude a DC as a preferred bridgehead server. However, you designate other DCs as preferred bridgehead servers. For example, if you have four DCs and you don't want BF4 to be a bridgehead server, you designate BF1, BF2, and BF3 as preferred bridgehead servers.

This brings up a special consideration. If you designate a single DC as a preferred bridgehead server, you should also designate at least one DC as a preferred bridgehead server. If only one is designated and it fails, the ISTG will not automatically switch the role to other DCs.