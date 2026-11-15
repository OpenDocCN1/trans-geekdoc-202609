findings, underline the key points and consequences of our research, and propose a road map for future research.

# 2.2 LITERATURE REVIEW ON DECISION-MAKING FOR UAVS

There are various algorithms for decision-making for UAVs, which help to increase the efficiency of the system. While choosing an algorithm, we need to keep in mind the environment and other parameters, as different algorithms perform differently in different scenarios.

# 2.2.1 CENTRALIZED DECISION-MAKING (CD)

The centralized decision-making approach uses various methods to centrally decide and plan the paths for the UAVs. No information related to the environment is used here. Authors in [4] have proposed a CD approach for optimizing the routes and depicting exposures in the case of two robots hunting for a moving point. The terrain is modeled through streamlining of the graphs where the vertices symbolize the waypoints of the UAVs while the edges represent the connection among the waypoints. Retreating-horizon optimization is used to decide the routes in such a way as to reduce the time needed to search for a target. Daniel et al. in [5] have examined the centralized mobility algorithms in the case of multiple robots covering a given region. They also avoided spare compliances of similar regions. However, their work does not discuss tasks related to information-gathering. Rather, it concentrates on channel-apprehensive mobility.

# 2.2.2 DISTRIBUTED DECISION-MAKING

The distributed decision-making (DD) approach uses various technologies to distribute the decision-making process to plan the routes of UAVs. Information related to the area of search of the targets is not used. In [6, 7, 8], the authors proposed a distributive collaboration of some decision-making algorithms for UAVs which do not require a hunt chart. The authors induced excellent results for temporal and spatial information about the hunt region. In [6, 8], the authors put forward several configurations for