
- Deep learning: a subset of machine learning that uses an artificial neural network to imitate the design of the human brain to find generalizations in complex data that can be used for decision-making.
- Proof of work: a consensus mechanism requiring cryptominers to solve complex problems to add a new block to the blockchain.

This realization gained momentum as machine learning models, especially deep learning models, became more complex and required significant computational power for training. By the mid-2000s, GPUs had become essential tools in the field of AI and machine learning, transforming how data scientists and researchers approached problems, significantly reducing the time it took to train complex models.

## Blockchain and cryptocurrency mining

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_15_0.png)

The cryptocurrency boom – at its peak in November 2021, the total market capitalization of cryptocurrencies reached approximately $3 trillion

In 2010, the use of GPUs for Bitcoin mining surged as miners discovered that GPUs significantly outperformed CPUs in solving cryptographic puzzles, such as finding the nonce in the hashing algorithm for the proof-of-work system. This realization led to a dramatic shift towards GPU mining. The cryptocurrency boom between 2017 and 2021 further escalated the demand for GPUs, resulting in skyrocketing prices and global shortages.

As of 2023, this demand had reduced somewhat and prices of GPUs were becoming more stable. This was for a number of reasons:

- ■ The volatility and reduced profitability of cryptocurrency mining had led to less demand for GPUs, specifically for mining purposes.
- ■ Big manufacturers had increased production to meet the demands.
- ■ Application-Specific Integrated Circuits (ASICs), which are specifically designed for mining, had largely replaced the use of GPUs in many mining operations.

### REVIEW QUESTIONS

- 1 What is the role of a graphics processing unit (GPU) in a computer?
- 2 How do GPUs enhance the performance of video games and video processing tasks?
- 3 Why have GPUs become essential in fields such as artificial intelligence, machine learning and cryptocurrency mining?

## A1.1.3 Differences between the CPU and the GPU (HL)

The central processing unit (CPU) and the graphics processing unit (GPU) are both core components of modern computers. They are designed differently, which is why they are used for different kinds of tasks. The CPU is great for handling various jobs, but the GPU is better for doing the same job many times on a lot of data at once.

### Design philosophies

CPUs are generally called "general-purpose processors" because they can handle many types of tasks. They are designed to run the operating system, process user input and manage programs. CPUs are good at tasks where decisions need to be made quickly, and where different types of work are being done at the same time.

GPUs are specialized processors because they focus on specific types of tasks. They are made for processing large amounts of data in parallel. This means they can work on many calculations at the same time. For example, GPUs are used to process images and videos because they can work on thousands of pixels at once.

### Core architecture

The CPU has only a few cores, but these cores are very powerful. Each core can handle many different instructions, but it works best when doing one task at a time. This makes the CPU very good for such tasks as running the operating system, where quick responses are needed. CPUs also have features including branch prediction (where the CPU tries to guess what will happen next) and out-of-order execution (where the CPU can work on tasks that are ready before others).

The GPU has many smaller cores. These cores are not as powerful as the CPU cores, but there are thousands of them, and they all work at the same time. This is why the GPU is very good for tasks such as rendering 3D images, where many similar calculations need to happen at once. The GPU's architecture is designed to work on large sets of data all at the same time.

### Memory access and power efficiency

The CPU and GPU access memory differently. The CPU uses a smaller, high-speed memory cache to get data quickly. This is useful when the CPU needs to access small amounts of data many times, such as when running programs or handling user inputs.

The GPU uses its own special memory called VRAM (video RAM). VRAM has a very high bandwidth, meaning it can move large amounts of data at once, such as images and videos.

However, the GPU uses more power because it must process a lot of data at the same time, especially when rendering videos or running complex simulations.

### Comparison of central processing units (CPUs) and graphics processing units (GPUs)

| Processor | Processing | Architecture | Functionality |
| :--- | :--- | :--- | :--- |
| CPU | It is a **general** purpose processor, capable of handling many different tasks. It executes the instructions of computer programs, involving operations such as arithmetic, logic and controlling input / output (I/O) operations, as directed by the operating system. | CPUs generally have fewer cores. General user devices tend to have between 4 and 8 cores; however, there are some advanced CPUs that now have 64 cores or more. Each core is very versatile, making it capable of handling complex computations that require sequential processing. | Allows the user to switch between multiple tasks and applications. This makes it ideal for running the operating system and general software applications. |
| GPU | It is a **specialized** processor, with a focus on handling graphics, rendering images, video and animations. | Composed of hundreds or thousands of small cores that are well-suited for tasks that can be run in parallel. While each core is not as powerful as a standard CPU core, the high number of cores allows them to perform a large number of calculations simultaneously, making them perfect for graphical processing. | Suited for tasks that require simultaneous processing of large blocks of data, such as rendering images, video processing and deep learning applications. |

- Rendering: the process of generating an image from a model by means of computer programs.

### Key information

To summarize, CPUs are better for tasks that require high-speed, complex decision-making and versatility. GPUs are better when the same operation needs to be performed on many data points simultaneously. This means that for tasks such as gaming, video editing and computational research (AI and machine learning), GPUs often significantly outperform CPUs.

### How the CPU and GPU work together to increase video-game performance

When playing video games, the CPU and GPU work together to deliver a seamless and immersive experience. The CPU handles the game's core logic, including rules, physical calculations and AI behaviour. It processes the inputs from the player (processing the outcomes of their actions and updating the game state accordingly). The GPU's primary role is to render the game's visuals. It processes vertex and pixel data to draw images onto the screen, including 3D objects, textures and effects such as lighting and shadows.

- Vertex and pixel data: data used by the GPU to render 3D objects and images.
- Frame: a single image in a sequence of images that makes up a video or animation.

### PROGRAMMING EXERCISE

Run benchmark software on your device to see your overall system performance. There are many options out there that you can search for; https://novabench.com and www.userbenchmark.com have free versions.

### Typical scenario

- 1 **Player input**: The player presses a key to move a character. The CPU processes this input, updates the character's position based on game physics and determines the new game state.
- 2 **Data preparation**: The CPU prepares the new position and state data and sends it to the GPU.
- 3 **Rendering**: The GPU updates the frame with the character's new position, applies lighting and shading and renders the scene.
- 4 **Display**: The rendered frame is displayed on the screen, providing immediate feedback to the player.

### REVIEW QUESTIONS

- 1 How do the CPU and GPU work together to enhance video-game performance?
- 2 Why is a GPU better suited than a CPU for tasks such as video rendering or AI computations?
- 3 What are shaders and textures, and how do they contribute to the rendering process handled by the GPU?

## A1.1.4 Purposes of different primary memory types

### Memory types

The primary memory of the computer stores data and instructions that the CPU needs in order to process tasks. Primary memory includes several different types: RAM (random access memory), ROM (read-only memory), caches and registers (covered in Section A1.1.1). These are all types of primary memory, meaning they are used directly by the CPU.
