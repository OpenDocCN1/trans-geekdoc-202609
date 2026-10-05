
For example, in the case of a network slowdown, the following questions can help troubleshooters identify the symptoms of a problem:

- Are all of the user's applications affected or just some of them? Which ones?
- Is the network slowdown continuous or intermittent? When or under what conditions slowdowns occur?
- Are other users experiencing the same problem? What other users?
- How far does the problem extend from the initial complaint? Is the entire network affected or just the immediate area?

## Determine if Anything Has Changed

One of the most important questions IT personnel might ask of end users is whether anything in their computer hardware, software, or configuration settings has changed recently. A new piece of hardware or software or a change in configuration settings can easily be the cause of many common problems.

However, getting users to admit to changes can sometimes require additional interrogation. As a result, IT people should be familiar with the log files and places where types of changes are documented so that they can determine for themselves what recent modifications have been made.

## Duplicate the Problem, if Possible

One of the most common experiences for IT helpdesk personnel is being told by users that they have received an error message. When asked what the error message said, users frequently have no idea. When this occurs, the next step is to try reproduce the error by having users repeat their actions. A problem that can readily be duplicated is much easier to troubleshoot one that appears intermittently.

## Approach Multiple Problems Individually

A problem does not necessarily have only one cause. For example, users reporting a significant reduction in network speed does not mean that there is just one problem causing the bottleneck. There can be several contributing factors, so IT technicians should not stop troubleshooting when they detect one cause of a problem. There might be others, so a properly methodical troubleshooting procedure should proceed until all possible causes have been examined.

When a troubleshooter detects multiple problems that each require remediation, the best practice is to approach the problems individually, creating a separate trouble ticket for each one. This ensures that each of the problems receives its due attention and also allows supervisors to delegate the various issues to different personnel.

## ESTABLISH A THEORY OF PROBABLE CAUSE

After identifying the problem, the next step in a scientific troubleshooting method is to hypothesize a theory of the problem's possible cause. The first probable cause a troubleshooter comes up with might not be the correct one, however. At this point, it is still just a theory. In fact, it might be necessary to repeat this theory several times and test several possible causes.

## Question the Obvious

When hypothesizing about the possible causes of a problem, it is important not to neglect the most obvious ones. In the case of a network communication failure on a particular workstation, for example, before initiating a detailed protocol analysis of the network's traffic, a troubleshooter should make sure the network cable isn't plugged in and that otherwise, simple causes have never been overlooked.

## Consider Multiple Approaches

To prove a cause, troubleshooters should work methodically through a process that investigates all of a problem's possible causes. There are several approaches that break down the networking process for examination, including the following:

- **Top-to-bottom/bottom-to-top OSI model:** Proceeding through the layers of the OSI model, either upward or downward, is one to perform a comprehensive examination of the networking process in relation to the problem. As troubleshooters gain experience, they typically develop instincts about the general location of a particular type of problem, which enables them to decide whether it would be more efficient to proceed through the OSI model from the top or the bottom.
- **Divide and conquer:** In some cases, the troubleshooter's instinct might point to a possible cause somewhere in the middle of the OSI model. Instead of wasting time starting from the top or bottom layer and working towards the middle, a divide and conquer approach might be preferable, in which the troubleshooter starts from the suspected layer and works up or down from there. In the same way, a troubleshooter might be able to divide a process into multiple subprocesses and examine each one individually.

## TEST THE THEORY TO DETERMINE THE CA

Once a troubleshooter has a theory of probable cause, the next step is to perform tests to confirm or disprove the theory. Note, however, that this step in the process is devoted to testing the efficacy of the theory only. This is not the time to actually address the problem.

## Establish a Plan of Action to Resolve the Problem and Identify Potential Effects

For a simplistic example, a troubleshooter might be investigating why a particular server is not available on the network and arrive at the theory that the server might be powered down. To test the theory, the troubleshooter should go to the server closet and see that the server is indeed powered down.

However, this does not mean that the troubleshooter should resolve the problem by switching the server back on right then. There could be any number of reasons else powered the server down, and resolving the problem requires a carefully planned course of action after investigating these reasons. In a simple situation like this, troubleshooters should follow a prescribed method.

Depending on the results of the testing, the troubleshooting process should continue in one of the ways:

**If the theory is confirmed, determine the next steps to resolve the problem.** Testing a theory of probable cause is usually more complicated than visually inspecting a component. The test should be carefully planned and executed. After confirming a theory of probable cause, the troubleshooter can go on to the next step: creating a plan for resolving the problem.

**If the theory is not confirmed, establish a new theory or escalate.** When testing indicates that the troubleshooter's hypothesis is incorrect and the suspected case is not the source of the problem, then the troubleshooter must repeat this process by devising another theory of probable cause and testing it. If the theory is incorrect and the troubleshooter is not able to come up with another probable cause, then it is time to escalate the problem within the IT department or consult a third party.

> EXAM TIP: The network troubleshooting methodology described in this objective provides high-level guidance, but it does not include the specific details of how the troubleshooter should go about identifying the problem, establishing a theory of probable cause, and testing that theory. However, candidates for the Network exam are expected to be familiar with the tools and procedures for doing these things, as discussed in the previous chapters.

## ESTABLISH A PLAN OF ACTION TO RESOLVE THE PROBLEM AND IDENTIFY POTENTIAL EFFECTS

After a troubleshooter successfully identifies the cause of a problem, they can proceed to create a detailed plan of action for resolving it. In the previous example, the actual solution to the problem might be simply switching on the server that was found to be powered down. However, in a methodical troubleshooting process, it is important to consider all the possible side effects the solution might have on the rest of the network.

Before switching the server, the troubleshooter must determine why it is off in the first place. Was it powered down deliberately by another technician, or did some operative condition cause it to power down by itself? If someone else in the IT department is working on that server, there should be records of that process that specify what is happening.

If there is no apparent reason why the server was powered down, the troubleshooter might have to check the logs on the server itself to determine what happened. If there is a server malfunction that shut the computer, then this would lead to the creation of an entirely new ticket for the malfunctioning server. The entire troubleshooting process would then repeat from the beginning.

It is also important for the troubleshooter to consider all possible ramifications of the resolution process and incorporate them into the plan of action. In many situations, fixing one problem could conceivably cause another one, and troubleshooters must try to anticipate these possibilities. If a troubleshooter suspects that a dangerous side effect of the solution would affect network productivity, the plan of action could call for the solution to be implemented during non-business hours. There should also be a detailed rollback plan in place if the solution ends up worse than the original problem.

Here again this step in the troubleshooting process calls only for the plan of the solution, not its implementation. In many cases, troubleshooters might have to seek approval from supervisors before the actual implementation can occur. It might also be necessary to seek permission from (or at least notify) other departments when a service interruption is expected.

## IMPLEMENT THE SOLUTION OR ESCALATE AS NECESSARY

With a plan of action in place and all the necessary approvals and permissions secured, the troubleshooter can proceed to implement the solution to the original problem. As in the example mentioned earlier, the implementation of the solution might be as simple as flipping a power switch. However, it can also be much more complex and require additional IT resources, such as help from other technicians, replacement hardware components, or assistance from outside service providers.

In some cases, the implementation of a particular solution might be beyond a troubleshooter's job description and require the case to be escalated to a more senior technician for implementation. For example, a troubleshooter's plan of action might include changes to the configuration of certain switchports in the data center. If the troubleshooter is not authorized to access the switches or make those changes, then they will have to escalate the implementation—or at least part of it—to someone who is authorized.
