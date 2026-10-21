![](bbox=[0.16, 0.07, 0.85, 0.31])

Fig. 4. An example fragment of a job on the blockchain.

# F. Defects and Possible Solutions

Although this design uses the characteristics of the blockchain to effectively solve the problems of centralization and single point of failure, it also introduces some shortcomings. Firstly, if there are multiple volunteers in the standby state, that is, all tasks are currently being processed or have been processed, there are multiple volunteers that are not processing jobs and are waiting for new jobs to process. When a new job block is published, if multiple volunteers want to handle the job at the same time, they will tend to enter a competitive condition. At this time, multiple volunteers want to publish a processing block at the same time. Because the broadcast of the blockchain has a certain delay, it is easy to cause the blockchain to fork. Therefore, each volunteer should be required to process only one job at the same time, otherwise the request to enter the chain of a new processing block should be rejected to reduce the chance of competition, when a new job is released. And a certain blockchain consensus mechanism is needed to maintain the uniqueness of the chain. Secondly, since the key pair can be generated arbitrarily, this system cannot guarantee that each volunteer only has a single volunteer key. If a real volunteer controls multiple volunteer keys and submits the work result in multiple identities, it may affect the verification of the results. Therefore, this design may be more suitable for use in a small area of trust. If large-scale application is required, it may be necessary to establish a centralized or distributed verification mechanism to verify the identity of volunteers to prevent the aforementioned "puppet volunteers".

Anyone can search the blockchain to understand which volunteers participated in a computing for each computing job in history, and the adoption of the results provided by each volunteer. At the same time, the authenticity of history can be guaranteed with the help of the persistent and auditable properties of the blockchain. This paper also raises two possible problems. One is the consensus problem on the chain, and the other is the puppet volunteer problem. And proposed possible solutions to these two problems separately.

In terms of the job content in the job blocks, this paper did not specifically discuss its format. It can be in any format that is not restricted by source code, executables or URLs, or it can be a sandboxed program to achieve cross-platform features. But in the implementation, the packet format should be determined according to the actual situation, and the format should be convenient for volunteers to judge whether their equipment can handle the job.

Although anyone can know the participation of each volunteer through the blockchain, this paper does not discuss how to design rewards for volunteer work. In actual implementation, it is reasonable to consider rewarding volunteers in some way to encourage volunteers to participate in volunteer computing.

# III. CONCLUSION

This paper proposes a blockchain-based volunteer computing system design, which uses the decentralized characteristics of the blockchain to solve the single point of failure. At the same time, because there is no task server as a bottleneck, the scalability problem is solved. It also provides a certain traceability for volunteer computing.

# ACKNOWLEDGMENT

I would like to thank Professor Ming-Deh Huang (University of Southern California) for his guidance on cryptography. I would like to thank Mr. Yang for useful discussions. I would like to thank ATEE-Plan for support.

# REFERENCES

[1] L.F. Sarmenta. Sabotage-tolerance mechanisms for volunteer computing systems. In Proceedings First IEEE/ACM International Symposium on Cluster Computing and the Grid, 2001, pp. 337-346.

[2] E. J. Korpela, “Seti@ home, boinc, and volunteer distributed computing,” Annual Review of Earth and Planetary Sciences, vol. 40, pp. 69–87, 2012