
After the crossover is completed, mutation may occur. This is done to avoid all population solutions falling into a local best of the current problem. The encoding as well as the crossing influences the mutation. When encoding permutations, for example, the mutation could mean switching two genes [[20](#ch13.xhtml#r099)]. The new offspring are randomly altered by mutation as shown in [Figure 3.4](#ch13.xhtml#f7). We can encode binary data by altering a few randomly selected bits from 1 to 0 or 0 to 1. The mutations for the parent `10001011` could be `10001111` and for the parent `10011111` could be `10010111`.

![Figure 3.4 Mutation.⏎](html/images/9781032942346_C003_004.jpg)

**Figure 3.4** Mutation.[⏎](#ch13.xhtml#f7b)

### 3.3.4 Formulation of objective function and fitness function

The objective function is used to determine a solution's worth. The output of this objective function is then turned into a fitness value that is utilized to determine the quality of a solution. Because GA is an optimization tool, the objective function is often a maximization or minimization function that includes all variables. The fitness function was designed to create a bimodal histogram in the grey level intensities, allowing for automated image processing steps to evaluate the quality of the individuals throughout the optimization. Individuals with a histogram with two well-separated normal distributions and an equal distance from the optimal threshold are favored by the fitness function we utilize.

GAs have numerous benefits over classical optimization algorithms. These algorithms are very versatile and are capable of handling a wide range of objective functions. The objective function may be stable or dynamic, linear or nonlinear, continuous or discontinuous, or even affected by random noise. The ability of GAs to tackle complex problems and their inherent parallelism are the two most notable advantages. Because multiple offspring in a population operate independently, the population (or any subset) can hunt in multiple directions at the same time. This capability of GAs makes the parallelization of algorithms very easy, and it also simplifies the modification of different parameters and even groups of encoded strings. However, GAs have some drawbacks as well. The selection criteria for the new population, the design of objective function, the choice of population size, and the selection of key factors like mutation and crossover rates must be handled with utmost care. Any misstep in the choices of these parameters can make it difficult for the algorithm to converge optimally and resulting in ineffective outcomes. Despite these limitations, GAs are nevertheless extensively used nonlinear optimization strategies today.

As a result, GAs are being used extensively in the field of engineering over the past decade. GAs are now being seen as the powerful tool for design optimization. This research work explores the different applications of evolutionary algorithms to solve complex optimization problems, challenges, and managing uncertainty in typical industrial scenarios. Here, the GA is utilized as an optimization mechanism in the supply chain planning process under uncertainty to determine the best production, inventory level, and distribution strategies.

## 3.4 Methodology

This research work aims to create a framework for creating the finest possible images by using an algorithm that considers all restrictions to produce better outcomes. For accurate and efficient picture enhancement, it employs the GA. It takes a picture as input and then enhances it. We start by interpreting an image and setting up the fitness feature. The GA begins with a randomly produced image that is similar in shape to the input image. This randomly generated image is continuously evolved utilizing crossover and mutation, as well as GA, until it achieves a better solution than the original.

### 3.4.1 Data representation

The initial step in solving a GA optimization problem is to consider the best way to describe the data. The chromosome (i.e. solution) is accepted as a 1D row vector by GA, but the input image is not one-dimensional. If the image is binary or grayscale, it may be 2D. If the input image is color, there may be more than two dimensions. If the color is RGB, there are three dimensions, one for each channel. A 1D vector must be used to represent data with more than one dimension. How can we turn multidimensional (MD) data into a 1D vector?

Starting with the simplest scenario, transforming a 2D image (or 2D matrix) into a 1D vector necessitates merging the two dimensions into a single dimension as shown in [Figure 3.5](#ch13.xhtml#f8). The matrix has numerous rows, and all of these rows must be merged into a single row. This is accomplished by stacking the several rows together. The following diagram depicts this. The illustration depicts a three-row, three-column image/matrix. There are 3 × 3 = 9 elements in all.

![Figure 3.5 Data representation of input image.⏎](html/images/9781032942346_C003_005.jpg)

**Figure 3.5** Data representation of input image.[⏎](#ch13.xhtml#f8b)

The vector length will undoubtedly be 9 when converted to a 1D vector. The first three elements of this vector will be drawn from the image's first row. The vector's next three items will come from the second row, and the vector's last three elements will come from the last row.

### 3.4.2 Fitness function

The fitness or objective function is a key segment of the GA, as it determines the quality of each image iteration based on a set of quantitative indices. As greyness and spatial ambiguity measurements for image enhancement and segmentation challenges, the proposed technique uses entropy (H), compactness (COMP), index of area coverage (IOAC), and their combinations as quantitative indices for evaluating picture quality. The average amount of fuzziness in the greyness of an image (X) is the degree of difficulty (ambiguity) in identifying whether a pixel should be considered black (dark) or white (bright) based on global information. Compactness and IOAC take local information into consideration and indicate the degree of fuzziness in an image's shape and geometry (spatial domain). As a result, the concept of minimizing these ambiguous measurements can be used to build a fitness (assessment) function.

During each iteration, the fitness function calculates a composite score by applying a weighted formula that integrates these indices. Higher scores indicate better-defined image features and clearer contrasts, guiding the GA to select and breed images that move closer to an optimal, high-quality output. By evolving images towards a bimodal histogram with distinct peaks in intensity, the fitness function drives the enhancement process, ensuring the GA consistently favors improved clarity and contrast.

## 3.5 Experimentation and results

GA is utilized in a range of complicated problems; a second level job must be used to regulate their parameters for efficiency's sake. As previously stated, the rate of mutation and crossover is known to have a significant impact on the efficiency and behavior of GA. Some researchers utilize tuning of the different parameters to select them, such that it identifies the best value of the parameters before the execution and then run the GA with these. Alternatively, other researchers have proved that utilizing control parameters (deterministic, adaptive) is more efficient in generating best or near-best results.
