
### 9. Discuss ethical scenarios autonomous vehicles may face such as having to choose whether to harm passengers or pedestrians in a collision. How should vehicles be programmed to handle such scenarios?

### 10. Forecast how self-driving technologies could affect vehicle ownership models, taxi/ride-hailing services, mobility for older adults and people with disabilities. Will personal car ownership eventually decline due to new mobility services enabled by autonomy?

## Multiple choice Questions

### 1\. Which of the following is NOT a core technical challenge for autonomous vehicles?

A) Perception and environment understanding  
B) Navigation and path planning  
C) User experience and interface design  
D) Long-term decision making  

The correct option is C User experience and interface design.

### 2\. Which company is operating an autonomous taxi service today?

A) Waymo  
B) Cruise  
C) Tesla  
D) Argo AI  

The correct option is A Waymo.

### 3\. Which sensor(s) does Tesla's Autopilot system rely on primarily?

A) Lidar  
B) Radar  
C) Cameras  
D) Lidar and Radar  

The correct option is C Cameras.

### 4\. SAE International defines what level as full driving automation?

A) Level 2  
B) Level 3  
C) Level 4  
D) Level 5  

The correct option is D Level 5.

### 5\. What is Argo AI focused on developing?

A) Integrated self-driving software platform  
B) Autonomous long-haul trucks  
C) Consumer vehicles with partial automation  
D) Purpose built robotsaxis  

The correct option is A Integrated self-driving software platform.

### 6\. Which segment is viewed as a more achievable near-term commercial application?

A) Autonomous long-haul trucks  
B) Autonomous personal vehicles  
C) Robo-taxis in dense cities  
D) Autonomous snowploughs  

The correct option is A Autonomous long-haul trucks.

### 7\. Which company spun out of Google's self-driving project and now operates a commercial ride-hailing service?

A) Cruise  
B) Argo  
C) Waymo  
D) Tesla  

The correct option is C Waymo.

### 8\. Achieving performance even better than humans is important for AVs to gain:

A) Market share  
B) Cruise control functionality  
C) Public trust  
D) Automated manufacturing  

The correct option is C Public trust.

### 9\. What factors could most set back progress of AVs if incidents occurred?

A) Software bugs found through testing  
B) Higher than expected manufacturing costs  
C) Collisions causing injuries while in autonomous mode  
D) Strict and inconsistent regulations between jurisdictions  

The correct option is C Collisions causing injuries while in autonomous mode.

### 10\. According to NHTSA guidelines, what level involves conditional driving automation using specific conditions?

A) Level 2  
B) Level 3  
C) Level 4  
D) Level 5  

The correct option is B Level 3.

## Summary: Key Concepts and Formulas

This summary aims to cover the most important ideas, technologies, challenges and approaches discussed in Chapter 8 regarding autonomous vehicles. Key topics will be explained at a conceptual level along with relevant formulas where applicable, focusing only on information directly presented in the chapter.

### Levels of Vehicle Automation

SAE International defines standard levels of driving automation from 0 (no automation) to 5 (full autonomy). Level 3 involves conditional driving automation that still requires a human driver to respond in some conditions. Level 4 denotes high driving automation where the vehicle can handle all aspects of driving in select environments without human intervention. Level 5 refers to full driving automation under all roadway and environmental conditions.

### Perception and Environment Understanding

Accurately perceiving the external driving environment in real-time is critical for autonomy. The chapter outlined sensors commonly used which can be modeled by formulas:

**Camera Vision:** `I = f(L)`

Where `I` is image captured and `L` is light intensity value

**Lidar Depth Estimation:**

Where `D` is distance, `c` is speed of light, `τ` is time of flight for reflection

Radar Detection:

Where `R` is object range and `Rx`, `Ry` represent coordinates on receive antenna

### Decision Making and Trajectory Planning

This formula calculates the probability of a path based on predicted state transitions and policy over actions.

Advanced machine learning techniques must also be applied to train perception and decision making systems from large datasets to handle uncertain and evolving driving scenarios.

### Vehicle Localization and Mapping

Vehicles localize themselves on high-precision vector maps of the road geometry, landmarks and traffic rules. Simultaneous localization and mapping (`SLAM`) algorithms fuse sensor data in real-time to localize the vehicle and incrementally build out the map representation. A Kalman filter is commonly used for localization:

```
x(t) = Fx(t-1) + w
z(t) = Hx(t) + v
```

Where `x` is true state, `z` is measurement, `F` is state transition model, `H` is observation model, and `w`, `v` are noise terms.

### Hardware Components

Multiple sensing modalities are required for redundancy. The chapter outlined Lidar advantages for accuracy but also high costs limitations. Currently most companies pair Lidar with cameras and radars for robust perception. Processing this data requires powerful on-board computers and specialized neural network accelerator chips are being developed.

## Part 5

### Data Science for Business Applications

### Chapter 9

### Implementing ML Solutions in Business

![Image](images/image-8.jpeg)

As machine learning algorithms and techniques have rapidly advanced, businesses have sought innovative ways to apply these powerful tools to gain competitive advantages. Machine learning holds immense promise for automating tasks, analyzing vast amounts of data, and powering personalized customer experiences at scale. However, successfully implementing machine learning solutions within an organization presents unique technical, operational and strategic challenges. This chapter will explore how companies can identify high-impact use cases, develop robust ML systems, and integrate them responsibly into business processes.

The first step in any ML implementation is defining clear business objectives and scoping the problem appropriately. Data-driven strategies require assessing available assets and identifying leverage points within business domains like marketing, logistics or customer support. One highly impactful area is predictive analytics to anticipate customer needs or behaviors. For example, an e-commerce retailer analyzed purchasing patterns and recommended complimentary products, resulting in a 12% increase in cart values.

Large corporations also face governance and oversight complexities when deploying learning models. Ensuring fairness, explainability and accountability is essential for bolstering consumer and employee trust. A major airline works closely with regulators to receive approval for an AI-powered pilot assistance system, demonstrating model outputs and failure scenarios through rigorous testing and documentation. Proper change management is likewise critical, as ML solutions may disrupt workflows or potentially replace roles over time.

## Understanding Business Requirements

Proper definition of business requirements is crucial for developing IT solutions that align with organizational objectives and add value. Capturing requirements accurately from the outset sets projects up for success by guiding solution design and development efforts. However, eliciting requirements is also an iterative process of progressive understanding as stakeholder needs become clearer over time. This section will explore effective techniques for eliciting, documenting and managing requirements to meet stakeholder needs. A holistic requirements management approach ensures solutions continue satisfying changing needs while maintaining compliance and delivering promised benefits.

### Defining Scope and Goals
