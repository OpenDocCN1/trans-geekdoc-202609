space, and MIPS (Million of instructions per seconds) performance is responsible for scaling and processing cloudlet offloading and co-hosted application runtime. It allows round-robin processing of each cloudlet in the given time frames and onboards the highest priority of the cloudlet first. Further to save power which inherently affects the latency of the node, it encompasses with decision to shut down the server to reduce power utilization.

# 11.3.1.4 Users

Users are defined as client machines that offload tasks to the edge servers using the network switches. Users consist of geospatial information, which is the coordinate of the originating request, and the user class defines line in response from the edge servers, starvation of cloudlet, etc. Further, the user access pattern creates a cloudlet to be offloaded to the edge servers. The mobility pattern recognizes random pathways for the users.

# 11.3.1.5 Simulation Framework

To achieve the simulation of edge server cloudlet offloading, this study reviews various possible scenarios to compare the algorithms proposed. It utilizes a Python-based framework rather than creating a new simulation architecture in the interest of time and computation necessary for testing. The simulation framework adopted for this study is EdgeSimPy. It is a Python-based edge server simulation framework architecture that allows the simulation to be aided with pre-existing data sets consisting of stations, network switches, edge servers, and users. The simulation aids in the monitoring of data flow, resource utilization, bandwidth of the edge servers, and other parameters for comparison of the placement algorithm. SimPy is an abstract class over EdgeSimPy is a generic tool based on Python for simulation of different parameters. It is generally used for resource utilization simulation and EdgeSimPy is a specific case of SimPy for edge and cloudlet offloading scenarios.

# 11.3.2 Continuous Integration of Resource Allocation (CIRA)

CIRA ensures that the processes are optimally offloaded to the edge servers. The D2D and cloudlet offloading are synchronized to the cloudlet to utilize maximum resources, thus ensuring the absence of underutilization of resources. CIRA is also responsible for reducing starvation for processes within an edge server orchestration setup.

# 11.3.2.1 Network Architecture

The network architecture utilizes the physical layer and attributes, namely, base stations, network switches, edge servers, users, and simulation framework to create