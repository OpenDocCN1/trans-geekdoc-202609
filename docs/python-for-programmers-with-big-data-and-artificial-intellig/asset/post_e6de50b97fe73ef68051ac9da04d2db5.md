
- Most apps created today use at least some open-source software. You’ll take advantage of many open-source libraries and tools throughout this book.

- Waze communicates information over the Internet between their servers and their users’ mobile devices. Today, such data often is transmitted in JSON (JavaScript Object Notation) format, which we’ll introduce in Chapter 9 and use in subsequent chapters. The JSON data is typically hidden from you by the libraries you use.

- Waze uses speech synthesis to speak driving directions and alerts to you, and speech recognition to understand your spoken commands. We use IBM Watson’s speech-synthesis and speech-recognition capabilities in Chapter 13.

- Once Waze converts a spoken natural-language command to text, it must determine the correct action to perform, which requires natural language processing (NLP). We present NLP in Chapter 11 and use it in several subsequent chapters.

- Waze displays dynamically updated visualizations such as alerts and maps. Waze also enables you to interact with the maps by moving them or zooming in and out. We create dynamic visualizations with Matplotlib and Seaborn throughout the book, and we display interactive maps with Folium in Chapters 12 and 6.

- Waze uses your phone as a streaming Internet of Things (IoT) device. Each phone is a GPS sensor that continuously streams data over the Internet to Waze. In Chapter 16, we introduce IoT and work with simulated IoT streaming sensors.

- Waze receives IoT streams from millions of phones at once. It must process, store and analyze that data immediately to update your device’s maps, to display and speak relevant alerts and possibly to update your driving directions. This requires massively parallel processing capabilities implemented with clusters of computers in the cloud. In Chapter 6, we’ll introduce various big-data infrastructure technologies for receiving streaming data, storing that big data in appropriate databases and processing the data with software and hardware that provide massively parallel processing capabilities.

- Waze uses artificial-intelligence capabilities to perform the data-analysis tasks that enable it to predict the best routes based on the information it receives. In Chapters 14 and 5 we use machine learning and deep learning, respectively, to analyze massive amounts of data and make predictions based on that data.

- Waze probably stores its routing information in a graph database. Such databases can efficiently calculate shortest routes. We introduce graph databases, such as Neo4J, in Chapter 16.

- Many cars are now equipped with devices that enable them to “see” cars and obstacles around them. These are used, for example, to help implement automated braking systems and are a key part of self-driving car technology. Rather than relying on users to report obstacles and stopped cars on the side of the road, navigation apps could take advantage of cameras and other sensors by using deep-learning computer-vision techniques to analyze images “on the fly” and automatically report those items. We introduce deep learning for computer vision in Chapter 15.

## 1.9 INTRO TO DATA SCIENCE: ARTIFICIAL INTELLIGENCE—AT THE INTERSECTION OF CS AND DATA SCIENCE

When a baby first opens its eyes, does it “see” its parent’s faces? Does it understand any notion of what a face is—or even what a simple shape is? Babies must “learn” the world around them. That’s what artificial intelligence (AI) is doing today. It’s looking at massive amounts of data and learning from it. AI is being used to play games, implement a wide range of computer-vision applications, enable self-driving cars, enable robots to learn to perform new tasks, diagnose medical conditions, translate speech to other languages in near real time, create chatbots that can respond to arbitrary questions using massive databases of knowledge, and much more. Who’d have guessed just a few years ago that artificially intelligent self-driving cars would be allowed on our roads—or even become common? Yet, this is now a highly competitive area. The ultimate goal of all this learning is *artificial general intelligence*—an AI that can perform intelligence tasks as well as humans. This is a scary thought to many people.

## Artificial-Intelligence Milestones

Several artificial-intelligence milestones, in particular, captured people’s attention and imagination, made the general public start thinking that AI is real and made businesses think about commercializing AI:

- In a 1997 match between **IBM’s DeepBlue** computer system and chess Grandmaster Gary Kasparov, DeepBlue became the first computer to beat a reigning world chess champion under tournament conditions. 9 IBM loaded DeepBlue with hundreds of thousands of grandmaster chess games. 0 DeepBlue was capable of using *brute force* to evaluate up to 200 million moves per second! 1 This is big data at work. IBM received the Carnegie Mellon University Fredkin Prize, which in 1980 offered $100,000 to the creators of the first computer to beat a world chess champion. 2

9 https://en.wikipedia.org/wiki/Deep_Blue_versus_Garry_Kasparov.
0 https://en.wikipedia.org/wiki/Deep_Blue_(chess_computer).
1 https://en.wikipedia.org/wiki/Deep_Blue_(chess_computer).
2 https://articles.latimes.com/1997/jul/30/news/mn-17696.

- In 2011, **IBM’s Watson** beat the two best human Jeopardy! players in a $1 million match. Watson simultaneously used hundreds of language-analysis techniques to locate correct answers in 200 million pages of content (including all of Wikipedia) requiring four terabytes of storage. 3 4 Watson was trained with machine learning and reinforcement-learning techniques. 5 Chapter 13 discusses IBM Watson and Chapter 14 discusses machine-learning.

3 https://www.techrepublic.com/article/ibm-watson-the-inside-story-of-how-the-jeopardy--winning-supercomputer-was-born-and-hat-it-wants-to-do-next/.
4 https://en.wikipedia.org/wiki/Watson_(computer).
5 https://www.aaai.org/Magazine/Watson/watson.php, AI Magazine, Fall 2010.

- Go—a board game created in China thousands of years ago 6 —is widely considered to be one of the most complex games ever invented with 10^170 possible board configurations. 7 To give you a sense of how large a number that is, it's believed that there are (only) between 10^78 and 10^87 atoms in the known universe! 8, 9 In 2015, AlphaGo—created by Google's DeepMind group—used deep learning with two neural networks to beat the European Go champion Fan Hui. Go is considered to be a far more complex game than chess. Chapter 15 discusses neural networks and deep learning.

6 http://www.usgo.org/brief-history-go.
7 https://www.pbs.org/newshour/science/google-artificial-intelligence-beats-champion--at-worlds-most-complicated-board-game.
8 https://www.universetoday.com/36302/atoms-in-the-universe/.
9 https://en.wikipedia.org/wiki/Observable_universe#Matter_content.

- More recently, Google generalized its AlphaGo AI to create AlphaZero—a game-playing AI that teaches itself to play other games. In December 2017, AlphaZero learned the rules of and taught itself to play chess in less than four hours using reinforcement learning. It then beat the world champion chess program, Stockfish 8, in a 100-game match—winning or drawing every game. After training itself in Go for just eight hours 0, AlphaZero was able to play Go vs. its AlphaGo predecessor, winning 60 of 100 games. 0

0 https://www.theguardian.com/technology/2017/dec/07/alphazero-google-deepmind-ai-beats-champion-program-teaching-itself-to-play-our-hours.

## A Personal Anecdote

When one of the authors, Harvey Deitel, was an undergraduate student at MIT in the mid-1960s, he took a graduate-level artificial-intelligence course with Marvin Minsky (to whom this book is dedicated), one of the founders of artificial intelligence (AI). Harvey:

Professor Minsky required a major term project. He told us to think about what intelligence is and to make a computer do something intelligent. Our grade in the course would be almost solely dependent on the project. No pressure!

I researched the standardized IQ tests that schools administer to help evaluate their students' intelligence capabilities. Being a mathematician at heart, I decided to tackle the popular IQ-test problem of predicting the next number in a sequence of numbers of arbitrary length and complexity. I used interactive Lisp running on an early Digital Equipment Corporation PDP-1 and was able to get my sequence predictor running on some pretty complex stuff, handling challenges well beyond what I recalled seeing on IQ tests. Lisp's ability to manipulate arbitrarily long lists recursively was exactly what I needed to meet the project's requirements. Python offers recursion and generalized list processing (Chapter 5).

I tried the sequence predictor on many of my MIT classmates. They would make up number sequences and type them into my predictor. The PDP-1 would “think” for a while—often a long while—and almost always came up with the right answer.

Then I hit a snag. One of my classmates typed in the sequence 14, 23, 34 and 42. My predictor went to work on it, and the PDP-1 chugged away for a long time, failing to predict the next number. I couldn’t get it either. My classmate told me to think about it overnight, and he’d reveal the answer the next day, claiming that it was a simple sequence. My efforts were to no avail.

The following day he told me the next number was 57, but I didn’t understand why. So he told me to think about it overnight again, and the following day he said the next number was 125. That didn’t help a bit—I was stumped. He said that the sequence was the numbers of the two-way crosstown streets of Manhattan. I cried, “foul,” but he said it met my criterion of predicting the next number in a numerical sequence. My world view was mathematics—his was broader.

Over the years, I’ve tried that sequence on friends, relatives and professional colleagues. A few who spent time in Manhattan got it right. My sequence predictor needed a lot more than just mathematical knowledge to handle problems like this, requiring (a possibly vast) world knowledge.

## Watson and Big Data Open New Possibilities

When Paul and I started working on this Python book, we were immediately drawn to IBM’s Watson using big data and artificial-intelligence techniques like natural language processing (NLP) and machine learning to beat two of the world’s best human Jeopardy! players. We realized that Watson could probably handle problems like the sequence predictor because it was loaded with the world’s street maps and a whole lot more. That
