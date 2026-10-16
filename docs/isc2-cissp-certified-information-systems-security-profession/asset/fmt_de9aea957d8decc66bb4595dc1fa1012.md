
The Software Engineering Institute (SEI) at Carnegie Mellon University introduced the Capability Maturity Model for Software, also known as the Software Capability Maturity Model (abbreviated as SW-CMM, CMM, or SCMM), which contends that all organizations engaged in software development move through a variety of maturity phases in sequential fashion. The SW-CMM describes the principles and practices underlying software process maturity. It is intended to help software organizations improve the maturity and quality of their software processes by implementing an evolutionary path from ad hoc, chaotic processes to mature, disciplined software processes. The idea behind the SW-CMM is that the quality of software depends on the quality of its development process.

The stages of the SW-CMM are as follows:

# Level 1: Initial
In this phase, you’ll often find hardworking people charging ahead in a disorganized fashion. There is usually little or no defined software development process.

# Level 2: Repeatable
In this phase, basic lifecycle management processes are introduced. Reuse of code in an organized fashion begins to enter the picture, and repeatable results are expected from similar projects. SEI defines the key process areas for this level as `Requirements Management`, `Software Project Planning`, `Software Project Tracking and Oversight`, `Software Subcontract Management`, `Software Quality Assurance`, and `Software Configuration Management`.

# Level 3: Defined
In this phase, software developers operate according to a set of formal, documented software development processes. All development projects take place within the constraints of the new standardized management model. SEI defines the key process areas for this level as `Organization Process Focus`, `Organization Process Definition`, `Training Program`, `Integrated Software Management`, `Software Product Engineering`, `Intergroup Coordination`, and `Peer Reviews`.

# Level 4: Managed
In this phase, management of the software process proceeds to the next level. Quantitative measures are utilized to gain a detailed understanding of the development process. SEI defines the key process areas for this level as `Quantitative Process Management` and `Software Quality Management`.

# Level 5: Optimizing
In the optimized organization, a process of continuous improvement occurs. Sophisticated software development processes are in place that ensure that feedback from one phase reaches to the previous phase to improve future results. SEI defines the key process areas for this level as `Defect Prevention`, `Technology Change Management`, and `Process Change Management`. For more information on the Capability Maturity Model for Software, visit the Software Engineering Institute’s website at [`www.sei.cmu.edu`](http://www.sei.cmu.edu).

## IDEAL Model

The Software Engineering Institute also developed the IDEAL model for software development, which implements many of the SW-CMM attributes. The IDEAL model has five phases:

# I: Initiating
In the initiating phase of the IDEAL model, the business reasons behind the change are outlined, support is built for the initiative, and the appropriate infrastructure is put in place.

# 2: Diagnosing
During the diagnosing phase, engineers analyze the current state of the organization and make general recommendations for change.

# 3: Establishing
In the establishing phase, the organization takes the general recommendations from the diagnosing phase and develops a specific plan of action that helps achieve those changes.

# 4: Acting
In the acting phase, it’s time to stop “talking the talk” and “walk the walk.” The organization develops solutions and then tests, refines, and implements them.

# 5: Learning
As with any quality improvement process, the organization must continuously analyze its efforts to determine whether it has achieved the desired goals and, when necessary, propose new actions to put the organization back on course.

The IDEAL model is illustrated in [Figure 20.4](#c20.xhtml#figure20-4).

``` 
![FIGURE 20.4 The IDEAL model ](images/c20f004.jpg)
```

[**FIGURE 20.4**](#c20.xhtml#figureanchor20-4) The IDEAL model 

### Gantt Charts and PERT

A Gantt chart is a type of bar chart that shows the interrelationships over time between projects and schedules. It provides a graphical illustration of a schedule that helps to plan, coordinate, and track specific tasks in a project. [Figure 20.5](#c20.xhtml#figure20-5) shows an example of a Gantt chart.

![FIGURE 20.5 Gantt chart ](images/c20f005.jpg)

[**FIGURE 20.5**](#c20.xhtml#figureanchor20-5) Gantt chart 

Program Evaluation Review Technique (PERT) is a project-scheduling tool used to judge the size of a software product in development and calculate the standard deviation (SD) for risk assessment. PERT relates the estimated lowest possible size, the most likely size, and the highest possible size of each component. PERT is used to direct improvements to project management and software coding in order to produce more efficient software. As the capabilities of programming and management improve, the actual produced size of software should be smaller.

### Change and Configuration Management

Once software has been released into a production environment, users will inevitably request the addition of new features, correction of bugs, and other modifications to the code. Just as the organization developed a regimented process for developing software, they must also put a procedure in place to manage changes in an organized fashion. Those changes should then be logged to a central repository to support future auditing, investigation, and analysis requirements.

The change management process has three basic components:

**Request Control** The request control process provides an organized framework within which users can request modifications, managers can conduct cost/benefit analysis, and developers can prioritize tasks.

**Change Control** The change control process is used by developers to re-create the situation encountered by the user and analyze the appropriate changes to remedy the situation. It also provides an organized framework within which multiple developers can create and test a solution prior to rolling it out into a production environment. Change control includes conforming to quality control restrictions, developing tools for update or change deployment, properly documenting any coded changes, and restricting the effects of new code to minimize diminishment of security.

**Release Control** Once the changes are finalized, they must be approved for release through the release control procedure. An essential step of the release control process is to double-check and ensure that any code inserted as a programming aid during the change process (such as debugging code and/or back doors) is removed before releasing the new software to production. Release control should also include acceptance testing to ensure that any alterations to end-user work tasks are understood and functional.

In addition to the change management process, security administrators should be aware of the importance of configuration management. This process is used to control the version(s) of software used throughout an organization and formally track and control changes to the software configuration. It has four main components:

**Configuration Identification** During the configuration identification process, administrators document the configuration of covered software products throughout the organization.

**Configuration Control** The configuration control process ensures that changes to software versions are made in accordance with the change control and configuration management policies. Updates can be made only from authorized distributions in accordance with those policies.

**Configuration Status Accounting** Formalized procedures are used to keep track of all authorized changes that take place.
