
## CHAPTER 12
## Emerging Trends

Network science discipline crosses several boundaries. We have provided a snapshot of the state of the art in network science. However, the future beckons for extensive, active research as expected. In the remainder of this chapter, I highlight the research focuses in leading institutions.

Mining social media is a burgeoning trend (Bhat and Abulaisha, 2013; Tu et al., 2013). Online social networking has irrevocably changed human social life. At an extreme, friends and family members sitting in the same room prefer to tweet or post instead of speak. Prevalence of social media creates living, digital diaries that are semipublic. Identically, sharing of social data produces opportunities for ultrarapid reflection and analysis. An evidence for this is that politics have changed with instantaneous trend analysis. Arguing for the downside of social media proliferation, it might be argued that people are retreating behind digital walls for isolated lives as Putnam put it (Putnam, 2001).

On the positive side of this transformation, analyses in our age of big data (Mayer-Schönberger and Cukier, 2013) empower us to understand global shifts beyond nuance and biases at the individual level. “big” data analyses enable discoveries and deployment of solutions for social as well as medical maladies.

Advances in communication networks are herding 5G wireless cellular networks. An objective is to create globally resource-optimized and energy-efficient networks. There are well-known trade-offs between energy consumption and service delay. State-of-the-art is to enable communication networks that are ever more adaptive to traffic variations. Game theory has continued to play a role in this development (Menache and Ozdaglar, 2011; Antoniou and Pitsllides, 2013).

There has been a proliferation of mobile device networks, where the network is limited to the device. Starting in the year 2000, automobiles have carried controller area networks (CAN) that enable drive-by-wire controlled vehicles (Voss, 2005). A body area network (BAN) is composed of sensors and medical devices embedded in clothing, worn on, or implanted in the body (Gupta et al., 2013).

## 12.1 CONCLUSION

Clearly, we have witnessed only the tip of the emerging network science (Greve et al., 2014). With our primer and call to arms, we look forward to many developments over the horizon.

## REFERENCES

Antoniou, J., Pitsilled, A., 2013. Game Theory in Communication Networks. CRC Press.

Bhat, S., Abulash, M., 2013. Analysis and Mining of Online Social Networks: Emerging Trends and Challenges. New Jersey: Wiley.

Greve, H., Rowley, T., Shiplov, A., 2014. Network Advantage: How to Unlock Value From Your Alliances and Partnerships. Jossey-Bass.

Gupta, S., Mukherjee, T., Venkatasubramanian, K., 2013. Body Area Networks: Safety, Security, and Sustainability. Cambridge University Press.

Mayer-Schönberger, V., Cukier, K., 2013. Big Data: A Revolution That Will Transform How Live, Work, and Think. Eamon Dolan/Houghton Mifflin Harcourt.

Menache, I., Ozdaglar, A., 2011. Network Games: Theory, Models, and Dynamics. Morgan and Claypool.

Putnam, R., 2001. Bowling Alone. Simon & Schuster.

Tu, X., White, A., Lu, N.I. (Eds.), 2013. Social Networking: Recent Trends, Emerging Issues and Future Outlook. Nova Publishers.

Voss, W., 2005. A Comprehensible Guide to Controller Area Network. Copperhill Media Corporation.

## EXERCISES

- 1. How can we interface controller area network with body area network?
- 2. Discuss interfaces between 5G wireless cellular networks and device area networks such as BAN.

## APPENDIX

In order to run the NetLogo network generation code, install NetLogo 5.0.2 and create a model with the provided code.

This model is used interactively to generate and compare three different network generators in terms of their generated network properties including betweenness centrality, clustering coefficient, density, and average shortest distance. These network generators are Kleinberg's small world model, Barabasi and Barabasi's scale-free network generator, and Epstein and Wang's random network generator. All generated networks have the same number of vertices. After computing all generated network properties, the aforementioned models are compared to find out the main differences among these models.

```
;;;;; Code;
turtles-own {
  explored? ;; this is used to mark turtles we have already visited
  node-clustering-coefficient
  distance-from-other ;; list of distances of this node from other turtles
}
links-own{
  rewired? ;; keeps track of whether the link has been rewired or not
}
globals
  component-size ;; number of turtles explored so far in the current component
  giant-component-size ;; number of turtles in the giant component
  giant-start-node ;; node from where we started exploring the giant component
  clustering-coefficient ;; the clustering coefficient of the network; this is the
    ;; average of clustering coefficients of all turtles
  average-path-length ;; average path length of the network
  infinity
  connected? ;; are all nodes connected
  number-rewired ;; number of edges that have been rewired. used for plots.
}
;;;;;;;;;;;;;;;;;; Setup Procedures ;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;
to setup
  clear-all
  set-default-shape turtles "circle"
  set infinity 99999
```

```
go
if Network? = "Random Network" [
;; if the below condition is true then we have a fully connected network and
need to stop
if (2 * count links) >= (count turtles) * (count turtles - 1)) [
display
user-message "fully connected. No more edges can be added."
stop
]
-edge
find-all-components
color-giant-component
ask links [set color [color] of endl] ;; recolor all
nif Network? = "Small World Network" [
rewire-all
]
if Network? = "Scale Free Network" [
ask links [set color gray]
make-nodes find-partner
]

do-calculations
tick
if Network? = "Random Network" [if giant-component-size = num-nodes [stop]]
 Network? = "Small World Network" [if giant-component-size = num-nodes [stop]]
 Network? = "Scale Free Network" [if giant-component-size = num-nodes [stop]]
```

```
100 Appendix
```
