
| | | | |
|---|---|---|---|
| 8 | 1.07 | 3.47 | 17.1 |
| 9 | 4.25 | 3.74 | 14.5 |
| 10 | 4.19 | 3.35 | 16.3 |

- 2. Read and run the response:

```
Sure! Here's an R function that loads and plots the given data
using a line plot:
```r
plot_sample_data <- function() {
# Define the data
sample1 <- c(2.85, 2.78, 2.09, 1.22, 4.29, 2.48, 3.48, 1.07, 4.25, 4.19)
sample2 <- c(3.61, 1.58, 2.75, 3.56, 2.89, 1.77, 3.66, 3.47, 3.74, 3.35)
sample3 <- c(16.7, 16.6, 17.2, 16.0, 16.2, 16.5, 15.0, 17.1, 14.5, 16.3)

# Create a data frame
data <- data.frame(sample1, sample2, sample3)

# Plot the data
plot(data$sample1, type = "l", col = "blue", ylim = 
range(data), xlab = "Index", ylab = "Value", main = "Sample Data")

lines(data$sample2, col = "red")
lines(data$sample3, col = "green")
}
```
```

```
# Add a legend
legend("topright", legend = c("Sample 1", "Sample 2", "Sample 3"), col = c("blue", "red", "green"), lty = 1)

```

You can call the function `plot_sample_data()` to load and
plot the data. It will generate a line plot with three lines
representing the three samples. The x-axis represents the index,
and the y-axis represents the corresponding values. The plot
will have a legend indicating the sample colors.

- 3. Update the prompt to be more clear:

That seems fine, but I'd like a ggplot2 plot of all sample against
the others in a point plot

- 4. Read and run the response:

```
Certainly! Here's an updated version of the function that uses
`ggplot2` to create a point plot comparing all the samples
against each other:
library(ggplot2)
```

```
plot_sample_data <- function() {
# Define the data
sample1 <- c(2.85, 2.78, 2.09, 1.22, 4.29, 2.48, 3.48, 1.07, 4.25, 4.19)
sample2 <- c(3.61, 1.58, 2.75, 3.56, 2.89, 1.77, 3.66, 3.47, 3.74, 3.35)
sample3 <- c(16.7, 16.6, 17.2, 16.0, 16.2, 16.5, 15.0, 17.1, 14.5, 16.3)

# Create a data frame
data <- data.frame(sample1, sample2, sample3)

# Convert the data to long format
data_long <- tidyr::gather(data, key = "Sample", value = "Value")

# Plot the data using ggplot2
ggplot(data_long, aes(x = Sample, y = Value, color = Sample)) +
  geom_point() +
  labs(x = "Sample", y = "Value", title = "Sample Data") +
  theme_minimal()
}
```

You can call the function `plot_sample_data()` to load and plot the data. It will generate a point plot where each point represents a value from one of the samples. The x-axis represents the samples, and the y-axis represents the corresponding values. Each sample is color-coded for easy identification.

- 5. Try again, adding detail to the prompt:

That's not what I meant! I want a faceted plot of sample 1 vs 2, sample 1 vs 2 vs 3.

- 6. Read and run the response:

Apologies for the misunderstanding. Here's an updated version of the function that uses `ggplot2` to create a faceted plot of sample 1 vs 2, sample 1 vs 3, and 2 vs 3:

```
library(ggplot2)

plot_sample_data <- function() {
# Define the data
sample1 <- c(2.85, 2.78, 2.09, 1.22, 4.29, 2.48, 3.48, 1.07, 4.25, 4.19)
```

This is how we get ChatGPT to attempt to draw plots with code for us. The difficulty is explaining what we want. If we can't explain something clearly, ChatGPT doesn't have an internal representation of what the response should be to give something quite right that needs a lot of work.

## Turbo-Charging Development in R with ChatGPT

### How it works...

In step 1, we give ChatGPT some sample data to draw a plot with. The prompt isn't specific though and the code we receive in step 2, while working, generates Figure 13.1, which isn't what we're after:

# Sample Data
![](img/dd0d9aaacf96c4d0e31d378b3_0.png)

Figure 13.1 – ChatGPT's first attempt, with a minimal prompt

In step 3, we generate a more detailed instruction and get the response and code in step 4. When we run that, we get the plot in Figure 13.2:

# Sample Data
![](img/dd0d9aaacf96c4d0e31d378b3_1.png)

Figure 13.2 – ChatGPT's second attempt, with a more detailed prompt

The plot is a bit better but still not as we wanted. We try again in step 5, mentioning facets to get a multiple-style plot but end up with generated code in step 6 that actually errors out.

The recipe shows that ChatGPT can generate code, but it takes a combination of factors for it to be accurate. If the topic of the code is sufficiently covered in tutorials on the internet, we will have the best chance of getting code work. If the topic is not well covered or is absent, ChatGPT will not be able to work out what you mean – it can't be creative and create an interpretation based on your idea. This is because it is a model that knows about language and not general-purpose intelligence. ChatGPT just generates the most likely answer from all the things it has trained on.

The code is not without value though; we have a good starting point and can develop things from there using ChatGPT and other sources to assist us in our reading and research.

### There’s more...

ChatGPT and others are developing code-specific plugins and extensions that will be available to paid subscribers of ChatGPT Plus. At the time, these are in beta test and have a waiting list, but could be worth checking out if you really need that extra.

## Writing documentation for R functions with ChatGPT

ChatGPT is valuable for generating R documentation because it has been trained on a wide range of text sources, including programming documentation. It can understand user queries related to R functions, packages, and contents, and generate informative and accurate documentation snippets. With its language understanding capabilities, ChatGPT can provide descriptions, parameter details, usage examples, and even explanations of complex concepts in R. This assists developers in quickly accessing relevant information, clarifying doubts, and understanding the functionality of R functions or packages. ChatGPT serves as a handy tool for enhancing the accessibility and comprehensibility of R documentation, supporting users in their programming and analysis tasks.

In this recipe, we will use ChatGPT to help us with the normally tedious task of generating documentation and examples for our own function.

### Getting ready

We just need an account at ChatGPT: https://chat.openai.com/.

### How to do it

To make ChatGPT assist you with code documentation, proceed as follows:

- Write a prompt and paste in the code:

```
Write Roxygen2 styled documentation for the following R function:
```

## Turbo-Charging Development in R with ChatGPT

```
factorise_cols <- function(df, col_list ) {
  not_all_na <- function(x) any(!is.na(x))

  for (i in col_list) {
    df <- df %>% dplyr::mutate(!!(i) := as.factor(!!(i))
  }
  df %>% dplyr::select_if(not_all_na)
}
```

Check the response:

```
# Factorise Selected Columns
#
# This function factorises the selected columns in a data frame.
#
# @param df data frame.
# @param col_list A character vector specifying the names of the columns to be factorised.
# @return A modified data frame with the selected columns factorised.
#
# @export
#
# @examples
# df <- data.frame(
# coll = c("A", "B", "C", NA),
# col2 = c(1, 2, 3, 4),
# col3 = c("X", "Y", "Z", NA)
# )
# factorise_cols(df, c("col1", "col3"))
#
# @import dplyr
# @importFrom base as.factor
factorise_cols <- function(df, col_list) {
  not_all_na <- function(x) any(!is.na(x))

  for (i in col_list) {
    df <- df %>% dplyr::mutate(!!(i)) := as.factor(!!(i))
  }
  df %>% dplyr::select_if(not_all_na)
}
```

And that's all we need to create documentation.
