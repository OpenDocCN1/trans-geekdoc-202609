+   - valve
+     - trumpet
+     - french horn
+   - slide
+     - trombone
+   - woodwind
+     - reeded
+       - clarinet
+       - basoon
+     - non-reeded
+       - flute
+       - piccolo
+   - strings
+     - plucked
+       - harp
+     - bowed
+       - violin
+       - cello

Notice that we have formed a hierarchy, where there are clusters of instruments within other clusters, going all the way from a very high-level clustering, all the way down to each individual instrument. A common way to visualize hierarchies like this is with a graphical representation called a *dendrogram*. A possible dendrogram for our orchestra hierarchy is shown in figure 17.1.

Notice that at the bottom of the dendrogram, each instrument is represented by its own vertical line, and at this level, each instrument is considered to be *in a cluster of its own*. As we move up the hierarchy, instruments in the same cluster as each other are connected by a horizontal line. The height at which clusters merge like this is inversely proportional to how similar the clusters are to each other. For example, here I have (subjectively) drawn this dendrogram to suggest that the piccolo and flute are more similar to each other than how similar the basoon and clarinet are to each other.

Typically when finding a hierarchy in data like this, one end of the dendrogram displays every case in its own cluster, and these clusters merge upwards until eventually, all the cases are placed into a single cluster. As such, I’ve indicated the position of our strings, woodwind, brass, and percussion clusters, but have continued clustering these clusters until there is only one cluster containing all the cases.