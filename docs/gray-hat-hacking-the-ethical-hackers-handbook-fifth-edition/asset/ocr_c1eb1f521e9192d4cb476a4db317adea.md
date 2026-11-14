from the associated decompiled line of code. Note, however, that this is not an exact one-to-one mapping because there are usually multiple assembly instructions associated with a single line of decompiled C.

# Collaborative Analysis

Collaboration and information documentation during reverse engineering are interesting yet often overlooked topics. When you’re dealing with a complex RE target, it is often the case that multiple people are looking at it at the same time. Over the years, several attempts and various approaches have been made to implement efficient collaboration workflows. Following is a timeline of the notable IDA plug-ins and their approach to collaboration using IDA:

+   - IDA Sync A plug-in developed by Pedram Amini that uses client/server architecture. Clients connect to a server, and all changes to the IDB done using the specific plug-in hotkeys are immediately transmitted to other clients. The server keeps a copy of the changes and makes them available for new clients. This plug-in is not actively developed anymore, and the last update was in 2012.

+   - CollabREate A plug-in developed by Chris Eagle and Tim Vidas that provides similar functionality as IDA Sync but improves support for different actions that are monitored and shared with clients. It works similar to a software versioning and revision control system because it allows users to upload and download changes made to the IDB but also to fork the IDB markups to the new project.

+   - BinCrowd A plug-in developed by Zynamics that uses a different approach to collaboration. Unlike the previous two plug-ins, BinCrowd is not designed for active collaboration on the same IDB. Instead, it builds an annotated function database that can be reused on many different samples that share some of the functions. It uses fuzzy matching to find similar functions and renames the matched functions in IDB. The client tool is released as an open source plug-in, but the server component was never released and the project has been discontinued.

+   - IDA Toolbag A plug-in developed by Aaron Portnoy, Brandon Edwards, and Kelly Lum. This plug-in offers limited collaboration capabilities and is aimed mainly at sharing annotations made with the plug-in. Unfortunately, the plug-in is no longer actively developed.

+   - CrowdRE A plug-in developed by CrowdStrike that is the reincarnation of the BinCrowd plug-in. Unlike the other mentioned plug-ins, this one hasn’t been open-sourced. The IDA plug-in is tied to the CrowdStrike server, which provides a function-matching service. This service-based approach may not be appealing to researchers who don’t wish to share their samples or IDB information with a third party, so you are encouraged to read the EULA before using this plug-in.

+   - FIRST A plug-in developed by Cisco TALOS that provides functionality similar to