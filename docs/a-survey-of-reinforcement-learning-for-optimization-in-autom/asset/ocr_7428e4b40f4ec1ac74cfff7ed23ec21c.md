| Feature/Criteria | Motion Planning | Manipulation | Multi-robot Coordination | Human-robot Collab |
| :--- | :--- | :--- | :--- | :--- |
| **Key Objectives** | Enable robots to navigate and perform tasks in dynamic environments | Enhance robotic interaction with objects and environments | Optimize collaborative actions of multiple robots for a common goal | Facilitate effective interaction and cooperation between humans and robots |
| **Challenges Addressed** | Navigating complex and dynamic environments, learning from interaction | Adapting to diverse objects, leveraging complex sensor inputs | Resource competition, obstacle avoidance in cooperative tasks | Adaptation to human behaviors, ensuring safety and making intelligent decisions |
| **RL Approaches** | PPO [50], Q-learning [51], Soft Actor-Critic (SAC) [52] | DDPG [53], Double DQN [54] | Multi-Robot Coordination with Deep Reinforcement Learning (MRCDRL) [55], Multi Agent Deep Reinforcement Learning [56] | DQN [57], [58], SAC [59], [60], DDPG [61], Double DQN [62] |
| **Methodology Highlights** | EfficientLPT [52] for space robots, curriculum learning for robotic arms | Visuo-motor feedback, dexterous grasping in sparse environments | MRCDRL [55] for cooperative action, MARL for pick-and-place optimization | Human-centered DRL, explainable RL for interaction quality enhancement |
| **Outcomes** | Improved planning accuracy, learning from human demonstrations | Significant outperformance in grasping tasks, adaptability to grippers | Effective resource allocation and dynamic obstacle avoidance, applicability in smart manufacturing | Enhanced coordination in packaging tasks, adaptability to user habits during collaboration |
| **Future Directions** | Integration with sensory feedback, real-time adaptation | Incorporation of more complex sensory modalities, tactile feedback | Scalable coordination strategies for larger teams, integration with smart environments | Personalized adaptation to human habits, enhancing safety and interpretability |
| **Representative Studies** | Wang et al. [63], Cao et al. [52], Zhou et al. [50], Yu and Chang [51] | Joshi et al. [54], Schuck et al. [53], Han et al. [64], Rivera et al. [65], Beigomi and Zhu [66] | Wang and Deng [55], Lan et al. [56], Yang [67], Lan et al. [68], Sadhu and Konar [69], Khamassi [70] | Ghadirzadeh et al. [57], Iucci et al. [58], Shafti et al. [59], Cai et al. [62], Thumm et al. [60], El-Shamouty et al. [61] |

TABLE III: Comparison of RL Approaches for Optimization in Robotics

dynamic tasks [55], [56], [67]-[70]. Human-robot collaboration (HRC) sees advancements through DRL's capacity for learning from interactions and adapting to human behaviors, significantly improving cooperation in tasks ranging from manufacturing to daily assistance [57]-[62]. Future research directions emphasize the integration of sensory feedback for real-time adaptation in motion planning, enhancing grasping tasks with complex sensory and tactile feedback, developing scalable coordination strategies for larger robot teams, and personalizing HRC to adapt to human habits while enhancing safety and interpretability. Table III succinctly encapsulates these domains by detailing key objectives, challenges addressed, RL approaches, methodology highlights, outcomes, and future directions, alongside representative studies demonstrating RL's transformative impact on robotics.

real-world applications where data collection is expensive or time-consuming [71], [72].
Current efforts to enhance sample efficiency and scalability include making past samples more reflective of the current model [71], [72], using evolution strategies and efficient memory in experience replay [73], [74], incorporating offline data for online learning [75], [76], and leveraging adaptive learning techniques [77], [78].
Future research should aim at algorithms with adaptive learning rates, domain-specific knowledge integration, efficient computational resource use, and cross-domain transfer learning to further improve sample efficiency and scalability in RL applications.

# III. CHALLENGES, STATE OF THE ART, AND FUTURE DIRECTIONS

There has been a significant progress in the field of RL for optimization in automation; however, there are still challenges to be addressed. Table IV gives a comparison of these challenges, along with the state of the art in the field and future directions that we will discuss in this section.

# A. Sample Efficiency and Scalability

Sample efficiency and scalability are vital in RL to minimize training data and ensure solutions scale with task complexity. These challenges are particularly important in

# B. Safety and Robustness

Ensuring safety and robustness in RL is crucial, especially for applications in critical domains like autonomous driving and healthcare. Safe RL algorithms aim to learn policies that satisfy safety constraints during both training and deployment [107].
Current strategies for ensuring safety include developing concepts of safety robustness [79], frameworks for robust policies [80], tackling observational adversarial attacks [81], integrating robust-control-barrier-function layers [82], managing safety requirements with robust action governor [83], enforcing safety via robust Model Predictive Control (MPC) [84], offering robustness guarantees [85], [86], improving policy robustness through falsification-based adversarial learning [87], and inducing a safety curriculum [108].