```
```python
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
```