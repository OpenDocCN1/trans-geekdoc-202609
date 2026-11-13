```
update_q_table(state, action, next_state, reward)
if reward > 0:
    PADDLE_COLOUR = (0, 255, 0)
elif reward < 0:
    PADDLE_COLOUR = (255, 0, 0)
# Update nett reward for graph
nett += reward
cumulative.append(nett)
# Draw the game to screen
pygame.display.flip()
clock.tick(FPS)
pygame.quit()
# Graph results
time = [i/FPS for i in range(len(cumulative))]
plt.plot(time, cumulative)
plt.title("Pong: Reinforcement learning results")
plt.xlabel("Time (seconds)")
plt.ylabel("Nett reward")
plt.grid(True)
plt.show()
```

# See also

Gymnasium is a popular library for learning about reinforcement learning. It provides a number of pre-written environments that you can experiment with: https://gymnasium.farama.org

> Genetic algorithm: imitates the concept of survival of the fittest and evolution by testing a population of possible solutions to a problem, using properties from the best-performing solutions to create a new population of possible solutions, and then repeating the process until a suitably performing solution has been identified.

# A4.3.7 Genetic algorithms

Genetic algorithms are not normally classified within the traditional categories of “supervised learning”, “unsupervised learning” or “reinforcement learning”. They are considered an evolutionary algorithm. They learn through a process of optimization inspired by the process of natural selection.

+   A high-level overview of the algorithmic process is:
+   * Start with a population of possible solutions to the problem. This may be in the form of an array of strings, for instance, where each string is a randomly generated possible solution.
+   * Each item within the population is evaluated through a fitness function that returns a metric for how good the possible solution is.
+   * Pairs of solutions are selected for reproduction. Various algorithms will be discussed that make these selections, but generally the better the fitness function score, the more likely a solution is to be selected.
+   * The selected pairs then undergo reproduction using a crossover algorithm, where part of the genetic code of each parent is selected and then combined together to create a new possible solution.
+   * The new offspring may then undergo mutation. Random number functions are generally used so that only a small percentage of offspring undergo mutation, and then those selected have parts of their genetic code (their “solution” to the problem) randomly altered.