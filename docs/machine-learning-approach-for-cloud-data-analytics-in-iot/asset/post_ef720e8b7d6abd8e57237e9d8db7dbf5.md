
node. Afterward, to sense information, every node sends this toward sink node with straightly else by sender node. Sender node uses cost function (CF) for selection. It is calculated for every nearer node that calculates CF that is depended upon path from sink node, power of transmission, as well as residual energy. Utilizing SNR as well as link standard is inspected too. Least CF of nearer node is chosen for sender.

## 11.3.2 Motivation

What we talk about in literature review, such larger part of suggested strategies utilize a sink node that gains information sensing from sensor nodes as well as sends this toward end server afterward accumulation. Moreover, nearly without protocol inside, WBAN utilizes clustering technology. For this cause, few issues appear that does not possess awareness like:

- At first, there are many possibilities of traffic phenomenon on sink node while every sensor nodes forward information at the same time, mostly on the condition of that censorious information.
- Secondly, WBAN's negligence of one sink node shows within absolute negligence while sink performs like the main hub.
- Thirdly, degradation of action on sink node occurs while several sensor nodes forward information on time that shows for short transport ratio.
- Fourth, to maximize anatomy description, requirement of many sensor nodes occurs as well as whether a cluster proposal is utilized that may generate burden at one sink node.
- Fifth, LOS transmission is needed within several plots that cannot be attained while anatomy is within movement.

Consequently, a routing strategy is presented by us known as DSCB that controls above-named lacks inside WBANs. Inside DSCB protocol, path-loss consequences reduction, load of network leveling, as well as achievement of LOS transmission occurs. Achievement of edges occurs accompanied by using clustering technology as well as formation of both sink nodes at human body.

## 11.3.3 DSCB Protocol

The suggested routing strategy is presented by us in such part known as Dual Sink Software Defined Networking proposal utilizing clustering inside BAN (DSCB) that improves WBAN's execution as applying clustering strategy between both sinks.

### 11.3.3.1 Network Topology

DSCB place both the sinks nodes which are called S1 and S2 between 10 sensor nodes at human anatomy. Sink nodes S1 and S2 are dissimilar with further distributed sensors at anatomy. The sink nodes possess superior assets by comparing with further sensor nodes like cell power, transmission power, and memory. Distribution of four sensor nodes occurs at anterior part of human anatomy accompanied by S1 like CH of them as well as four sensor nodes at behind of human anatomy accompanied by S2 like CH of them. A node is located at right hand's anterior part when a node is located at behind of left hand. The waist locates S1 as well as Lumbar locates S2. With the movable part, these nodes which connected toward hands are attached to one of two of sink nodes utilizing LOS transmission. Nodes 1 to 4 as well as, perhaps, 5 united by S1 build cluster 1 at which nodes 6 to 9 as well as feasibly node 10 united by S2 build cluster 2. Whether sensing of censorious information occurs, it is forwarded straightly toward associated CH, nevertheless whether information is not censorious and this is going to chase multi-hop transmission afterward choosing one sender node between nearer nodes. Figure 11.3 shows the suggested DSCB protocol's topology.

### 11.3.3.2 Starting Stage

Inside such stage [26], two sink nodes (S1 as well as S2) broadcast packets, i.e., “Hello” that carry IDs as well as places of them. On acceptance, every sensor node transmits “Reply” information that carries IDs, place, as well as residual energy. With such procedure, every node plus two sink nodes gain data regarding every further node. To find nearer nodes, this aids.

### 11.3.3.3 Cluster Evolution

Afterward, recognition of nearer is occurred then upcoming procedure is cluster evolution that occurs by data given before within “Hello” as well as “Reply” texts interchanged. Two sinks are known by CHs as individual clusters of them. CHs give to receive sensed information from sensors, combine, as well as forward this toward neighbor AP.

![](img/cbc35e0d02425baa6028b87d56263a7f_302_0.png)

Role of cloud computing in the field of body area network [9, 20].

Time periods location follows cluster evolution toward every cluster participants, occurred with the help of CHs utilizing TDMA protocol.

### 11.3.3.4 Sensed Information Stage

Activation of sensor nodes occurs just within assigned time period of them or sensor nodes possess snooze way. As sensor node turns agile, this initializes to sense information. That information sensing is inspected for cruciality firstly. If it is critical, it is sent directly to sink node; else, it is sent to sink node via multi-hop.

### 11.3.3.5 Choice of Forwarder Stage [26, 27]

DSCB calculates sender node with the help of link’s SNR, Distance ($d_i$) in distinction to sink, Residual energy ($E_{Rn}$) as well as Transmission power ($T_P$).

The estimation of threshold considering SNR possesses default inside DSCB protocol that is same with “1”. Whether one sensor node does sense little information as well as which is not censorious, this chooses one node in distinction to nearby table of that. After that, numerous hops to sink are added up for selecting nearby direct toward sink. Whether numerous hops possess zero, such node is regarded by straightly attached toward sink as well as so this transmission occurs straightly with no sending node with among. Or SNR of link is computed whether less than 1, for becoming forwarder, it rejects such node as well as it records data of itself. Whether the SNR of link is greater than 1 after that node's function of cost (FC) be about is computed. For calculating sensor node’s residual energy ($E_{Rn}$), this equation is used by us:

$$
\begin{gather*}
\mathrm{E}_{\mathrm{Rn}}=\mathrm{E}_{\mathrm{In}}-\mathrm{E}_{\mathrm{Cn}}\tag{11.1}
\end{gather*}
$$

At which n indicate numerous nodes utilized, $\mathrm{E}_{\mathrm{Rn}}$ is called as residual energy, $\mathrm{E}_{\mathrm{In}}$ is called as initial energy as well as $\mathrm{E}_{\mathrm{Cn}}$ is called as energy consumption node that computes the equation as below.

$$
\begin{gather*}
\mathrm{E}_{\mathrm{Cn}}=\mathrm{E}_{\mathrm{Tr}}+\mathrm{E}_{\mathrm{Re}}+\mathrm{E}_{\mathrm{Cty}}\tag{11.2}
\end{gather*}
$$

At which $\mathrm{E}_{\mathrm{Tr}}$ as well as $\mathrm{E}_{\mathrm{Re}}$ are accordingly, the energy consumption's quantity with the help of node transceiver radio at the time of information's transmission as well as reception as well as $\mathrm{E}_{\mathrm{Cty}}$ is called as consumption of energy occurred with the help of electronic circuitry of node. The node $\mathrm{n}_{\mathrm{j}}^{\mathrm{i}}$ energy absorbs at the time of setup period $\mathrm{P}_{\mathrm{su}}$, beginning on time 0 as well as consumption of energy occurred in every round $\mathrm{E}_{\mathrm{Rnd~j}}^{\mathrm{i}}(\mathrm{ti})$ is

$$
\begin{gather*}
\mathrm{E}_{\mathrm{Rnd~j}}^{\mathrm{i}}(\mathrm{ti})=\int_{\mathrm{ti}}^{\mathrm{ti}+\mathrm{Psu}}\mathrm{E}_{\mathrm{Cnj}}^{\mathrm{i}}(\mathrm{t})d t\tag{11.3}\\
=\int_{\mathrm{ti}}^{\mathrm{ti}+\mathrm{Psu}}\left(\mathrm{E}_{\mathrm{Trj}}^{\mathrm{i}}(\mathrm{t})+\mathrm{E}_{\mathrm{Rej}}^{\mathrm{i}}(\mathrm{t})+\mathrm{E}_{\mathrm{Ctyj}}^{\mathrm{i}}(\mathrm{t})\right)d t\tag{11.4}
\end{gather*}
$$

At which $\mathrm{E}_{\mathrm{Rnd~j}}^{\mathrm{i}}=$energy needed with the help of node $\mathrm{n}_{\mathrm{j}}^{\mathrm{i}}$ at time of period $\mathrm{P}_{\mathrm{su}}$ also in every cycle.

For finding energy value needed considering the transmission as well as reception, we use these equations:

$$
\begin{gather*}
\mathrm{E}_{\mathrm{Tr}}(\mathrm{k}, \mathrm{di})=\mathrm{E}_{\mathrm{Tr-Cty}} * \mathrm{k}+\mathrm{E}_{\mathrm{Tr-am}}(\mathrm{k}, \mathrm{di})\tag{11.5}
\end{gather*}
$$
