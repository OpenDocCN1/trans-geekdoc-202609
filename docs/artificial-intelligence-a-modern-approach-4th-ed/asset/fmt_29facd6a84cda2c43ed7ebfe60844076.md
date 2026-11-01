
Once we have a path, the task of executing a sequence of actions to follow the path is called trajectory tracking control. A trajectory is a path that has a time associated with each point on the path. A path just says “go from A to B to C, etc.” and a trajectory says “start at A, take 1 second to get to B, and another 1.5 seconds to get to C, etc.”

Trajectory tracking control
Trajectory

## 26.5.1 Configuration space

Imagine a simple robot, `R`, in the shape of a right triangle as shown by the lavender triangle in the lower left corner of [Figure 26.11](#Chapter26-05.xhtml#fig26-11). The robot needs to plan a path that avoids a rectangular obstacle, `O`. The physical space that a robot moves about in is called the workspace. This particular robot can move in any direction in the `x – y` plane, but cannot rotate. The figure shows five other possible positions of the robot with dashed outlines; these are each as close to the obstacle as the robot can get.

Description
The workspace and the configuration spaces are shown in the `x y` coordinate planes. Workspace: A small shaded triangle labeled `R` is placed with its vertex at the origin. A rectangle labeled `O` is aligned at the center of the first quadrant. Two and three dashed right triangles are aligned at the bottom and left end, respectively, of the rectangle. Configuration space: The outlines formed by the right triangles in the Workspace are also included with the rectangle `O` and the whole structure is labeled `C_obs`.

![Fig-374.jpg](images/Fig-374.jpg)

Figure 26.11 A simple triangular robot that can translate, and needs to avoid a rectangular obstacle. On the left is the workspace, on the right is the configuration space.

Workspace

The body of the robot could be represented as a set of (`x`, `y`) points (or (`x`, `y`, `z`) points for a three-dimensional robot), as could the obstacle. With this representation, avoiding the obstacle means that no point on the robot overlaps any point on the obstacle. Motion planning would require calculations on sets of points, which can be complicated and time-consuming.

We can simplify the calculations by using a representation scheme in which all the points that comprise the robot are represented as a single point in an abstract multidimensional space, which we call the configuration space, or `C-space`. The idea is that the set of points that comprise the robot can be computed if we know (1) the basic measurements of the robot (for our triangle robot, the length of the three sides will do) and (2) the current pose of the robot—its position and orientation.

Configuration space
C-space

For our simple triangular robot, two dimensions suffice for the `C-space`: if we know the (`x`, `y`) coordinates of a specific point on the robot—we’ll use the right-angle vertex—then we can calculate where every other point of the triangle is (because we know the size and shape of the triangle and because the triangle cannot rotate). In the lower-left corner of [Figure 26.11](#Chapter26-05.xhtml#fig26-11), the lavender triangle can be represented by the configuration (`0`, `0`).

If we change the rules so that the robot can rotate, then we will need three dimensions, (`x`, `y`, `θ`), to be able to calculate where every point is. Here `θ` is the robot’s angle of rotation in the plane. If the robot also had the ability to stretch itself, growing uniformly by a scaling factor `s`, then the `C-space` would have four dimensions, (`x`, `y`, `θ`, `s`).

For now we’ll stick with the simple two-dimensional `C-space` of the non-rotating triangle robot. The next task is to figure out where the points in the obstacle are in `C-space`. Consider the five dashed-line triangles on the left of [Figure 26.11](#Chapter26-05.xhtml#fig26-11) and notice where the right-angle vertex is on each of these. Then imagine all the ways that the triangle could slide about. Obviously, the right-angle vertex can’t go inside the obstacle, and neither can it get any closer than it is on any of the five dashed-line triangles. So you can see that the area where the right-angle vertex can’t go—the C-space obstacle—is the five-sided polygon on the right of [Figure 26.11](#Chapter26-05.xhtml#fig26-11) labeled `C[obs]`

C-space obstacle

In everyday language we speak of there being multiple obstacles for the robot—a table, a chair, some walls. But the math notation is a bit easier if we think of all of these as combining into one “obstacle” that happens to have disconnected components. In general, the C-space obstacle is the set of all points `q` in `C` such that, if the robot were placed in that configuration, its workspace geometry would intersect the workspace obstacle.

Let the obstacles in the workspace be the set of points `O`, and let the set of all points on the robot in configuration `q` be `A(q)`. Then the C-space obstacle is defined as

`C[obs] = { q: q ∈ C and A(q) ∩ O ≠ {} }`

and the free space is `Cfree = C – Cobs`.

Free space

The `C-space` becomes more interesting for robots with moving parts. Consider the two-link arm from [Figure 26.12(a)](#Chapter26-05.xhtml#fig26-12). It is bolted to a table so the base does not move, but the arm has two joints that move independently—we call these degrees of freedom (`DOF`). Moving the joints alters the (`x`, `y`) coordinates of the elbow, the gripper, and every point on the arm. The arm’s configuration space is two-dimensional: (`θshou`, `θelb`), where `θshou` is the angle of the shoulder joint, and `θelb` is the angle of the elbow joint.

Description
The workspace is a box with a flat obstacle hanging from the ceiling. The robot arm is placed inside the box. The shoulder part is labeled `psi_shou` and the elbow part is labeled `psi_elb`. The arrangement is as follows. The shoulder part is on a block structure and is oriented toward the upper right. The flat obstacle is very close to the upper part of the shoulder. The elbow part is connected to the upper end of the shoulder and is oriented toward the lower right.

![Fig-375.jpg](images/Fig-375.jpg)

Figure 26.12(a) Workspace representation of a robot arm with two degrees of freedom. The workspace is a box with a flat obstacle hanging from the ceiling. (b) Configuration space of the same robot. Only white regions in the space are configurations that are free of collisions. The dot in this diagram corresponds to the configuration of the robot shown on the left.

Degrees of freedom (DOF)

Knowing the configuration for our two-link arm means we can determine where each point on the arm is through simple trigonometry. In general, the forward kinematics mapping is a function

Forward kinematics

`ϕ[b]: C → W`

that takes in a configuration and outputs the location of a particular point `b` on the robot when the robot is in that configuration. A particularly useful forward kinematics mapping is that for the robot’s end effector, `ϕ[EE]`. The set of all points on the robot in a particular configuration `q` is denoted by `A(q) ⊂ W` :

```
A(q) = { ∪_b { φ_b(q) } }.
```

The inverse problem, of mapping a desired location for a point on the robot to the configuration(s) the robot needs to be in for that to happen, is known as inverse kinematics:

Inverse kinematics

`IK[b]: x ∈ W ↦ { q ∈ C s.t. ϕ[b](q) = x }`.

Sometimes the inverse kinematics mapping might take not just a position, but also a desired orientation as input. When we want a manipulator to grasp an object, for instance, we can compute a desired position and orientation for its gripper, and use inverse kinematics to determine a goal configuration for the robot. Then a planner needs to find a way to get the robot from its current configuration to the goal configuration without intersecting obstacles.
