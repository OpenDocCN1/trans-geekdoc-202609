The advantage of the suggested controller is shown in multiple cases. The second step was real-time studies conducted in a laboratory setting. When we simulated the computer vision algorithm in the above settings, the following-ing ideas were proposed:

+   1. For the robotic hand to identify the objects in the simulated settings, it must travel at a minimum distance and pace.
2. The robotic hand knows every position in the simulated world.
3. There are obstacles that the robotic hand cannot find.
4. If two locations cannot be connected by a clear path, the robotic hand pauses. Frictional mistakes of all kinds are avoided.

# 12.3.1 MATLAB results

Here, various tests are carried out in conjunction with MATLAB simulation to evaluate the effectiveness of the suggested approach. Ten simulations using current methods and computer vision run to find the best path. To cut down on the amount of time elapsed, the computer vision method doesn't require a significant number of iterations. The robotic hand's actions are used to modify the threshold distance to pass an object. During the experiment, one pressure sensor was placed in the robotic hand. The robotic hand pressure was measured for 10 seconds, from 0 to 80 KPa, and then the pressure was decreased. The robotic hand has 180° bending angle when no pressure is applied. When the robotic hand is closed and the measured pressures fall between 60 and 80 KPa, it reaches its maximum bending angle. The bending angle decreases as the robotic hand opens further. The interaction between the front and backing layers is what causes the irregularity in the robotic hand's bending profile. We have simulated the robotic hand movement with pressure (KPa) vs. angle (degree). The computer vision algorithm's drawn graph under simulated conditions is displayed in Figure 12.7.

In each scenario, several iterations are made until the best results are chosen. Following a successful iteration, the computer vision produces its optimal values. Generally, we compared the output of the computer vision algorithm with existing techniques [7,8,10]. The comparison study carried out in simulated environment is shown in Table 12.1.

In all situations, the accuracy rate is high over 90% of the time. A percentage deviation of the computer vision is calculated in relation to the elapsed time for each scenario. The elapsed time is determined objectively and consistently. Next, the % deviation is computed using the measured values in each example. One deviation % is displayed on the time elapsed graph in Figure 12.8.

The computer vision approach has 9.17%, 6.60%, and 6.42% less variance in elapsed time when compared to other methods. Comparative