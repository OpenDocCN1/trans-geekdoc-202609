
Go is kind of like the “Grail” for artificial intelligence researchers. Most of the “combinatorial games” we saw in [chapter 5](#ch05.xhtml#chapter5), like chess or checkers, are resolved by a computer using the minimax algorithm. Not Go, though.

## [THE QUEST FOR THE GRAIL](#contents.xhtml#toc2_136)

A Go board has 361 intersections where you can place a white or a black stone. That makes 3^(361) possible game situations. Written out, that number is:

174089650659031927907188238070564367946602724950

263541194828118706801051676184649841162792889887

149386120969888163207806137549871813550931295148

03369660572893075468180597603

To give you an idea of the magnitude, let’s consider the number of atoms in the universe (10^(80)), which is pretty much the gold standard for big numbers in artificial intelligence. Now, imagine that our universe is but one atom in a larger universe. You make a universe containing as many universes as our universe contains atoms. And you count the number of atoms in this universe of universes. That adds up to lots and lots and lots of atoms. It’s enough to make you dizzy.

To have as many atoms as there are situations in Go, you need to make a trillion universes like this! In short, we are very far from any modern computer’s processing capacity. As with chess, we have to use an AI algorithm.

Unfortunately, the minimax algorithm isn’t going to do it for us.

## [A BIT OF CALCULATION](#contents.xhtml#toc2_137)

Remember, this algorithm relies on the idea of trying all the game possibilities on a few moves, and choosing the one that leads to the best result. With 361 possible moves at the start of the game, the number of situations to examine increases very quickly. For instance, to evaluate all four-move games alone, the minimax algorithm must consider 361 × 360 × 359 × 358 possibilities – more than 16 billion configurations. It will take several seconds to process this with a modern computer.

With only four moves examined, the minimax algorithm will play like a novice. A game of Go consists of several hundred moves. Given the billions of possible situations after only four moves, it is not possible to see your opponent’s strategy at all! We need to come up with a better method.

![image](images/inline14_1.jpg)

*In Go, players take turns placing black and white stones on the board to form territories. The white player just made his second move. It is hard to say exactly how the game will turn out at this point*.

## [WANT TO PLAY AGAIN?](#contents.xhtml#toc2_138)

The algorithm used by computers to win at Go has been known since the late 1940s by the name “Monte Carlo Tree Search,” a reference to the casino located in Monaco.

What an odd name for an algorithm! It was given this name because this algorithm relies on chance to resolve problems.

For each of the 361 possible moves, we’re going to play a thousand games at random. Completely at random. The opponent’s moves and the computer’s responses are drawn at random. We make note of the game’s outcome, and we start over one thousand times. Each time, we start over with the same initial configuration.

To evaluate each of the 361 moves, the algorithm makes a statistical calculation on the scores obtained for the thousand games played at random. For example, you can calculate the mean of the scores (in practice, computer scientists use slightly more complex calculations). The Monte Carlo algorithm makes the hypothesis that, with some luck, the best move to make is the one that leads the board to produce the best statistics. This is the move that will be chosen.

![image](images/inline14_2.jpg)

By assuming that each game lasts under 300 moves (which is a reasonable limit if we base this on games played by humans), we will have made a maximum of 300,000 calculations for each of the 361 “first moves” that we have to evaluate, which is around 130 million operations in total. This is more than reasonable for a modern computer.

## [RED, ODD, AND LOW!](#contents.xhtml#toc2_139)

Monte Carlo algorithms have been used in this way since the 1990s to win at Go. In 2008, the program MoGo, written by researchers at Inria, the French Institute for Research in Digital Science and Technology, achieved a new feat by repeatedly beating professional players. By 2015, programs had already made a lot of progress in official competitions, although they had failed to beat the champions.

However, in March 2016, the program AlphaGo defeated the world champion, Lee Sedol, four matches to one. For the first time, a computer achieved the ninth Dan, the highest level in Go, and was ranked among the best players in the world!

To achieve this feat, the engineers at Google used a Monte Carlo algorithm combined with deep neural networks.

As with any Monte Carlo algorithm, lots of matches are played at random to determine the best move. However, the computer scientists do not make the computer play completely at random. Not only is the computer unable to truly choose at random (there is always some calculation), but it would also be unfortunate to play completely at random, since even the greenest Go players know how to spot the worst moves.

This is where AlphaGo’s first neural network comes in. The Google team refers to this as the “policy network.” This is about teaching a neural network how to detect the worst moves by giving it game examples as input. This prevents the Monte Carlo algorithm from producing too many bad matches and improves the accuracy of its statistical calculations.

A deep neural network doesn’t work much differently than Rosenblatt’s perceptron: the input is a 19 × 19 three-color grid (black, white, and “empty”), and the output, instead of a simple “yes” or “no,” is a value for each possible move. With a deep neural network and some graphics cards to do some GPU processing, this is feasible.

## [NO NEED TO BE STUBBORN](#contents.xhtml#toc2_140)

The other improvement AlphaGo makes consists of stopping before the game is over, since often there is no point in continuing when it becomes clear the game is going so poorly for one of the players. Once again, this is a problem that is well suited for a neural network, where the input is the state of the board and the output is a yes or no answer to the question “Is the game completely lost for one of the players?” The Google engineers call this the “value network” – that is, a network that measures the value of the game.

The interest in ending the game before it’s over is to play shorter games… and thus play more every time. Instead of only one thousand games for each move, the algorithm can simulate two to three times more… and the statistical calculation to determine the best move will be even better.

![image](images/inline14_3.jpg)

## [A BIT OF REINFORCEMENT](#contents.xhtml#toc2_141)

By combining a Monte Carlo algorithm with neural network algorithms, the AlphaGo team was able to program a computer that quickly and correctly decides what move to make.

However, to program these two neural networks, the AlphaGo team has to have examples of Go matches. Indeed, it’s not enough to show the computer a Go board and tell it “Go on, learn!” The policy network has to be told which configurations contain good moves and which moves are to be avoided. The value network has to be shown thousands of Go matches and told, every time, which ones can be chalked up as a loss and which ones are sure to be a victory.

Whatever learning method you use, you have to provide the machine with lots of examples. It is not possible to find all the examples manually by searching in the Go archives. The solution used by the AlphaGo team relies on another artificial intelligence technique: *reinforcement learning*.

## [STRONGER THAN EVER!](#contents.xhtml#toc2_142)
