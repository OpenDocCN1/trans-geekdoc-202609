![](bbox=[0.43, 0.12, 0.68, 0.32])

**FIGURE 8.17**
Density-reachability and density-connectivity in DBSCAN.

threshold of dense regions. An object is a **core object** if the \(\epsilon\)-neighborhood of the object contains at least \(MinPts\) objects, otherwise, it is **noise**. Core objects are the pillars of dense regions.

Given a set, \(D\), of objects, we can identify all core objects with respect to the given parameters, \(\epsilon\) and \(MinPts\). The clustering task is therein reduced to using core objects and their neighborhoods to form dense regions, where the dense regions are clusters.

Two core objects \(p\) and \(q\) are \(\epsilon\)**-reachable** if \(d(p, q) \le \epsilon\), that is, \(p\) is in the \(\epsilon\)-neighbor of \(q\) and vice versa. Two core objects \(p\) and \(q\) are **density-connected** if \(p\) and \(q\) are \(\epsilon\)-reachable or transitively \(\epsilon\)-reachable, where \(p\) and \(q\) are transitive \(\epsilon\)-reachable if there exist one or multiple core objects \(r_1, ..., r_l\) such that \(p\) and \(r_1\) are \(\epsilon\)-reachable, \(r_i\) and \(r_{i+1} (1 \le i < l)\) are \(\epsilon\)-reachable, and \(r_l\) and \(q\) are \(\epsilon\)-reachable. Then, a cluster \(C\) with respect to parameters \(\epsilon\) and \(MinPts\) is simply a nonempty maximal subset of core objects that every pair of objects in \(C\) is density connected.

In DBSCAN*, a cluster contains only core objects. However, it is easy to assign a noncore object that is in the \(\epsilon\)-neighborhood of a core object to the cluster containing that core object. DBSCAN explicitly identifies such noncore objects as **border objects**, and DBSCAN* can use a postprocessing step to pick up those border objects. Those objects that do not belong to any \(\epsilon\)-neighborhood are outliers.

**Example 8.7.** Density-reachability and density-connectivity. Consider Fig. 8.17 for a given \(\epsilon\) represented by the radius of the circles, and, say, let \(MinPts = 3\).

Of the labeled objects, \(p\), \(m\), \(o\), \(q\), and \(t\) are core objects, since each of the \(\epsilon\)-neighborhoods (dashed circles in the figure) of them contains at least three objects. Objects \(p\) and \(o\) are \(\epsilon\)-reachable, so are \(o\) and \(q\). Thus \(p\) and \(q\) are density-connected.

It can be verified that the core objects \(p\), \(m\), \(o\), \(q\), and \(t\) form a cluster, since each two among them are density-connected and no other core objects can be added into this group so that the pairwise density-connectivity is maintained.

Object \(s\) is not a core object, since the \(\epsilon\)-neighborhood of \(s\) contains only two objects. However, \(s\) is in the \(\epsilon\)-neighborhood of core object \(p\), thus \(s\) is a border object.

Objects \(u\) and \(v\) are not core objects, and they do not belong to the \(\epsilon\)-neighborhood of any core objects. Thus they are outliers.