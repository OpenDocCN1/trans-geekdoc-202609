

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_252_0.png)

## 强化学习流程图

与大多数机器学习算法一样，强化学习引入了一些需要考虑的新术语：

- 代理：决定做什么的机器学习模型。
- 环境：代理感知到的世界。
- 状态：世界在某一时刻的快照。状态是传达当前情况或环境的数据。在开发强化学习算法时，仔细考虑状态数据至关重要。你会向代理提供什么数据来帮助它学习你交给它的任务？例如，在训练代理玩贪吃蛇游戏时，你是向它提供指示苹果距离和方位的值，还是整个世界的像素地图？
- 动作：代理在环境中可以执行的操作或行为（例如向前走、向左转、向右转）。
- 奖励：环境对代理动作的即时反馈。奖励可以是正的或负的（惩罚）。
- 策略：代理用于将状态映射到动作的策略。可以将策略视为代理的心理 if-then-then 列表。

一般过程如下：

- 代理通常会从随机策略开始，因为它对环境没有任何现有知识。
- 代理观察环境。根据其感知到的内容以及迄今记录的策略，代理选择执行一个动作。
- 代理执行所选动作。
- 环境更新到新状态。
- 环境通过奖励向代理提供反馈。
- 代理根据收到的奖励反馈更新其策略。
- 过程重复。

强化学习通常涉及探索和利用的结合。“探索”是指代理忽略其已学习的策略并尝试新事物。“利用”是指代理遵循已学习的策略，并根据其所学内容行事。通常，算法开始时会大量强调探索，因为算法尚未有太多机会学到任何东西。随着时间的推移，探索/利用比率（称为“学习率”）的超参数应进行调整，以便开始更多地依赖所学数据。

## Q学习

代理的策略负责维护代理已学习的内容。虽然有几种方法，但最常见的一种称为“Q学习”。Q学习可以被视为使用二维数组或其他数据结构，为每个可能的状态和动作组合创建一个巨大的查找表。它为两者的每个可能排列存储一个值，以预测在每个场景中会获得什么奖励。

| | 动作 1 | 动作 2 | 动作 3 | 动作 4 |
|---|---|---|---|---|
| 状态 1 | -50 | 0 | 10 | 0 |
| 状态 2 | 10 | 20 | 0 | 10 |
| 状态 3 | 0 | -10 | 0 | 50 |

该表说明了 Q 学习二维数组的简化版本。数据表明：

- 当出现状态 1 时，代理能做的最好的事情是执行动作 3，并且应该避免执行动作 1。
- 当出现状态 2 时，代理应该执行动作 2，但动作 1 和 4 也会给它带来奖励。
- 当出现状态 3 时，代理应该执行动作 4 以获得大奖励（可能赢得游戏），并避免动作 2。

考虑到数组大小由所有可能的状态和所有可能的产生的动作决定，Q 学习表可能非常大。当数据需求无法实现地大时，替代方法是使用人工神经网络来了解状态及其产生的输出动作的概括。当使用神经网络时，它被称为“深度 Q 网络”。

以下是该过程的伪代码概述：

```
Initialize the Q-table with all zeros (or some initial values)
for each round:
  Initialize the state S to the starting point of the game
  while the episode is not finished:
    Choose action A from state S using a policy derived from Q
    Take action A
    Observe the immediate reward R and the next state S'
    Update the Q-table value for the original state S and action A:
      Q(S, A) <- Q(S, A) + alpha * (R + gamma *
             max(Q(S', all_actions)) - Q(S, A))
    S <- S' # Move to the next state
  end while
end for
```

关于此伪代码有几条注释：

- 选择动作 A 时，应考虑算法是应该利用其 Q 表还是探索其他替代方案。
- 此处的 Alpha 指的是学习率。较高的 alpha 意味着较新的信息对更新 Q 值有更大的影响，使代理能够快速适应环境的变化。较低的 alpha 会导致更新变慢，使代理更稳定但学习速度也更慢。起始值在 0.01 到 0.05 之间是正常的。
- 此处的 Gamma 指的是折扣因子，用于决定时应考虑多少未来预期奖励。大多数场景的最终目标是找到一种能提供最大累积奖励的最优策略。Gamma 值接近 0 会使代理变得“近视”（短视），大幅优先考虑即时奖励。反之，Gamma 接近 1 会鼓励代理更强烈地考虑未来奖励，将其视为几乎与即时奖励同样重要。这使代理变得“远视”，在更长的时间跨度上进行规划。
- 伪代码中的这一行被称为“贝尔曼方程”：

```
Q(S, A) <-- Q(S, A) + alpha * (R + gamma * max(Q(S', all_actions)) - Q(S, A))
```

它指出，状态-动作的 Q 值等于即时奖励加上下一步中最佳动作的折扣值，并根据学习率进行调整。

## 示例：Pong! 游戏

以下示例是一款 Pong! 风格的挡板弹球游戏。它使用 pygame-ce 库进行图形处理，并使用 numpy 数组作为 Q 表。正如结果图表所示，该代理需要大约 20 分钟的训练才能开始显示出可接受的结果。

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_254_0.png)

Pong! 游戏

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_254_1.png)

Pong! 游戏：随时间变化的净奖励

```python
import pygame
import random
import numpy as np
import matplotlib.pyplot as plt
# Constants
WIDTH, HEIGHT = 200, 400
FPS = 30
PADDLE_WIDTH, PADDLE_HEIGHT = 30, 15
BALL_RADIUS = 7
BALL_COLOUR = (255, 255, 64)
PADDLE_COLOUR = (255, 64, 255)
BACKGROUND_COLOUR = (64, 64, 128)
# Initialise Pygame
pygame.init()

screen = pygame.display.set_mode((WIDTH, HEIGHT))
clock = pygame.time.Clock()

class Paddle:
    def __init__(self, x, y):
        self.rect = pygame.Rect(x, y, PADDLE_WIDTH, PADDLE_HEIGHT)
    def move(self, x):
        self.rect.x += x
        self.rect.x = max(self.rect.x, 0)
        self.rect.x = min(self.rect.x, WIDTH - PADDLE_WIDTH)
    def draw(self):
        pygame.draw.rect(screen, PADDLE_COLOUR, self.rect)

class Ball:
    def __init__(self, x, y):
        self.rect = pygame.Rect(x, y, BALL_RADIUS*2, BALL_RADIUS*2)
        self.dx = random.choice([-4, 4])
        self.dy = random.choice([-4, 4])
    def move(self):
        self.rect.x += self.dx
        self.rect.y += self.dy
        if self.rect.top <= 0 or self.rect.bottom >= HEIGHT:
            self.dy = -self.dy
        if self.rect.left <= 0 or self.rect.right >= WIDTH:
            self.dx = -self.dx
    def draw(self):
        pygame.draw.ellipse(screen, BALL_COLOUR, self.rect)

# Game objects
paddle = Paddle(WIDTH//2 - PADDLE_WIDTH//2, HEIGHT - PADDLE_HEIGHT)
ball = Ball(WIDTH//2, HEIGHT//2)

# Q-learning parameters
LEARNING_RATE = 0.05
DISCOUNT_FACTOR = 0.99
epsilon = 0.1

# Let state have 10 positions for paddle and ball
# (reduces demands on Q-Table)
def get_state():
    paddle_mid = paddle.rect.x + PADDLE_WIDTH // 2
    ball_mid = ball.rect.x + BALL_RADIUS
    return (paddle_mid//20, ball_mid//20)
```

