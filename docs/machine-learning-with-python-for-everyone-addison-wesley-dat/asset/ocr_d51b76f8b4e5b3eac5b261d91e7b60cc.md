less difference—is called solving a dual problem or simply solving the dual of an original problem. In mathematics, the term dual refers to an alternative but equivalent way of representing or solving a problem.

Standard principal components analysis finds good directions—data-defined axes—for the data by breaking down the covariance matrix. However, it does this by implicitly using the SVD of the data. We could consider that to be an unnecessary detail, but the covariance matrix is merely one way to capture the similarities in our data in a feature-centric fashion. As we discussed in Section 13.2.3.2, dot products and kernels give us another way to capture similarities—now in an example-centric fashion. The net result is that we can plug kernels instead of covariances into PCA and get out more exotic creatures that have an equally exotic name: manifold methods.

# 13.3.6.1 Manifolds

Don't be scared by the name manifolds: it is simply a fancy term for things that can clearly be related to points, lines, and planes but aren't exactly these things. For example (Figure 13.4), if I draw a circle and label it like a watch dial—I, II, III, etc.—and I am willing to break the circle at XII (noon), I can very easily connect spots on the circle to spots on a line. The circle and the line share certain characteristics. Namely, take the times near 3 o'clock. It's neighbors are at 2:59 and 3:01 (sorry, I can't write minutes as Roman numerals). Those neighbors are the same whether we draw the times as a circular watch-face or flatten them out as a timeline.

![](bbox=[0.25, 0.58, 0.8, 0.8])

Figure 13.4 Viewing geometric objects as manifolds emphasizes the abstract similarity between different forms based on local neighbors. These neighbors remain unchanged by bending and looping.

Yes, you have a point: if we cut the watch face at the top, XII loses one side of its neighbors. Sacrifices must be made. As another example, if I unroll a lidless and bottomless aluminum can, I would have something looking like an aluminum cookie sheet—and again, away from the boundary where I cut the can, the local neighborhoods before and