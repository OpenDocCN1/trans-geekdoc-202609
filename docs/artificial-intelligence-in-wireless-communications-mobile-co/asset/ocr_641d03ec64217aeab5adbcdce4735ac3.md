the cognitive engine. First, as we will be discussing in more detail, is the GNU Radio system, and open source SDR. We have also built an interface for Implementing Radio in Software (IRIS), developed by CTVR at Trinity College, Dublin [8]. The Kansas University Agile Radio (KUAR) is an SDR developed by the team at Kansas University. While we have not developed an interface for this radio, we include it in the figure because of our knowledge of the radio system as a viable candidate for such purpose [9].

Each component is launched as a separate process that interfaces and exchanges data with other processes through some generic interface (e.g., sockets or a messaging interface).

The architecture is designed around two important aspects. First, it allows development, testing, and launching of each component separately for low coupling between processes. This feature also enables distributed processing, where different components can reside on different processors or hosts with little change in behavior. Second, this architecture enables the testing of different types of algorithms and processes to realize each component. For example, many sensors may be defined for different purposes and easily fit into the system, or different optimization functions may be developed and compared for performance. This architecture encourages both research and development.

# 2.3 Component Descriptions

The following sections provide more detail about the purpose and design of the system components.

Along with a standard interface to transfer information, the system also requires a eXtensible Markup Language (XML) as our method of conveying data and information. Using this standard satisfies a couple of competing goals. XML provides a method of encoding data that is open, flexible to support new and developing sensors, and both human and machine readable. XML also has a standardized format and methods of verifying the format, via a document type definition (DTD), to make integration with the cognitive controller easy. Finally, XML is an open, simple standard with many tools available to read and write it, including libraries for almost any programming language.

# 2.3.1 Sensors

Sensors collect data from the radio or other systems to describe and model the environment. Environmental data can include anything that will