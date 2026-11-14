target position was of no concern but the orientation of the active vehicle was, a Cubic Bezier curve was used to generate the spline for the vehicle to follow.

![](bbox=[0.162, 0.143, 0.833, 0.369])

**IMAGE 23.2** A simple Cubic Bezier Spline. Note that the spline starts at the front of the car and not in the middle. This is because the steering controllers would minimise the error at the front of the vehicle when calculating the steering direction.

A Cubic Bezier Spline requires three points and is depicted in Image 23.2. P0 is the vehicle's initial position and P2 is the target position. But where should P1 be placed? Since we want the spline to start with the orientation of the vehicle, P1 needs to be somewhere along a line through P0 in the vehicle's facing direction (V). But how far along this line should P1 be placed? Through experimentation, it was found that a good spline that the vehicles could follow could be created by placing P1 at a projected position along the line V, 1/3rd of the length between P0 and P2 provided that P2 was not behind P0. A minimum distance from P0 was also always adhered to and, again, this distance was determined through experimentation. This was calculated as follows:

```
float Dist=(P2-P0).Length();
float ProjectionDist=(Dist/3)<MinDist ? MinDist : (Dist/3);
Vector3 P1=P0+V * ProjectionDist;
```

# 23.3.2 SPLINE FOLLOWING

Once an appropriate path had been generated, to make the vehicle follow it requires converting the Bezier curve into a Catmull-Rom spline. Although it is possible to follow a Bezier curve directly, all the systems in the AI engine were already set up to follow Catmull-Rom splines, so converting a generated curve to this format meant that there was no need to change any of the spline following code (remember, there was less than five months development time to build these systems). One of the advantages of the Catmull-Rom spline is that it goes through every point, so converting to a Catmull-Rom spline just means sampling and storing the points along the curve (Dunlop, 2005).