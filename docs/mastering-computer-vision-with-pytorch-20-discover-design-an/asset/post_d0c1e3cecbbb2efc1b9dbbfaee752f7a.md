
example input and returns a ScriptModule that you can save and load in Python or C++.

While tracing is great for straightforward modules that don’t involve control flow (like conditionals and loops), it can struggle with modules where the flow of execution depends on the values in tensors. This is because it only captures the operations performed during the single execution used for tracing, not the control flow itself.

## Scripting

Scripting, on the other hand, captures the control flow in your model by directly analyzing the Python code of your model. It does this via a decorator, @torch.jit.script.

Here’s an example of how you might script a module:

```
import torch

class MyModule(torch.nn.Module):
    def __init__(self, N, M):
        super(MyModule, self).__init__()
        self.weight = torch.nn.Parameter(torch.rand(N, M))

def forward(self, input):
    if input.sum() > 0:
        output = self.weight.mv(input)
    else:
        output = self.weight + input
    return output

my_module = MyModule(10,20)
sm = torch.jit.script(my_module)
```

In this example, we define a simple module that uses control flow in its forward method. We then create an instance of this module and pass it to torch.jit.script to generate a ScriptModule. This module will behave exactly like the eager mode version but also has its Python code serialized in TorchScript format.

## Conclusion

In conclusion, TorchScript gives you the power to optimize your models, leverage the PyTorch C++ runtime environment for deployment, and serialize your models for use in different platforms (for example, serving via a Python server, deploying on mobile devices, and so on). It’s an essential tool for any practitioner who wishes to take their PyTorch models beyond the research environment, especially in the field of computer vision, where models are typically complex and computational resources are at a premium.

In this chapter, we have walked through the journey of PyTorch’s creation and evolution. We saw how it rapidly rose in popularity due to its developer-friendly approach, flexibility, and strong support for GPU acceleration and distributed computing. We discussed its inherent Python-first philosophy, which ensures that the library integrates smoothly into the Python ecosystem, making it an excellent tool for both research and development.

We then explored the key improvements brought in by PyTorch 2.0, highlighting its robust capabilities in GPU acceleration and distributed computing. We saw how PyTorch facilitates the seamless migration of tensor computations to the GPU, thereby drastically speeding up the training process. Furthermore, we learned how PyTorch supports distributed computing, enabling us to handle large-scale deep-learning tasks effectively.

The chapter also introduced us to the concept of dynamic computation graphs (DCGs), which, by following a define-by-run paradigm, provide PyTorch with a competitive edge, especially when it comes to debugging and prototyping. The AutoGrad system’s simplicity and efficiency in calculating derivatives automatically is another significant advantage of PyTorch that we looked into.

Lastly, we delved into TorchScript, a tool that enables PyTorch models to transition from research to production seamlessly. We discovered that it allows for the serialization of models in a form that can be run and optimized in non-Python environments, demonstrating its importance in deploying models at scale in production settings.

All these factors combined make PyTorch an ideal choice for tackling complex tasks in computer vision, driving us towards its use throughout this book.

As we move on to the next chapter titled PyTorch Basics, we will start building upon the foundation laid in this chapter. We will dive deeper into the fundamental building blocks of PyTorch - tensors and explore how they are used in various operations and computational graphs. This will provide us with the necessary tools to start creating and manipulating models in PyTorch, propelling us further into our journey of mastering computer vision with PyTorch 2.0.

## CHAPTER 2

## PyTorch Basics

### Introduction

In the realm of machine learning and deep learning, PyTorch stands tall and is revered for its flexibility and capabilities to architect and train intricate neural network architectures. Whether it’s a budding AI enthusiast or an established research scientist, many have come across this name, but not everyone delves deep enough to understand the pillars upon which this powerful framework stands. At the heart of PyTorch’s prowess lies a seemingly simple yet profoundly powerful concept: tensors.

### Structure

In this chapter, we will cover the following topics:

- Introduction to Tensors
- Tensor Operations in PyTorch
- Understanding Computational Graphs in PyTorch
- Automatic Differentiation in PyTorch: The Power of Autograd
- Conclusion

### Understanding the Essence of Tensors

In the broadest sense, a tensor is a generalization of scalars, vectors, and matrices. It’s a multi-dimensional container that can store data with varying dimensions. Imagine a scalar, a mere number; it’s dimensionless—a point. Extend that into a line, and you have a vector—a 1-dimensional sequence of numbers. Push it into a plane, and you have a matrix—a 2-dimensional grid of numbers. Now, imagine stretching this structure into the third, fourth, or even the nth dimension; you are envisioning tensors.

```
# A scalar (0D tensor)
scalar = torch.tensor(5)

# A vector (1D tensor)
vector = torch.tensor([1, 2, 3, 4])

# A matrix (2D tensor)
matrix = torch.tensor([[1, 2], [3, 4], [5, 6]])
```

For those acquainted with Python, one can think of tensors as somewhat analogous to NumPy arrays. Yet, tensors boast features far beyond array-like data structures in Python. Their seamless adaptability to GPU acceleration is one such superpower, ensuring that data-intensive operations, particularly common in deep learning, aren’t bottlenecked by the CPU’s computational limits. We will look into tensors in detail in the following sections.

### The Imperative Nature of PyTorch

But why does PyTorch place such emphasis on tensors? The answer lies in the very design philosophy of PyTorch. The framework operates in an imperative or define-by-run mode, which means the computations are executed immediately. There is no symbolic graph waiting in the wings; the graph is constructed dynamically, as operations are defined. This approach is in stark contrast to the define-and-run paradigm, where one first defines a computation graph, and then the data is run through it.

Imagine you’re following a cooking recipe. There are two ways you can approach it:

- Read the entire recipe first (from ingredients to the final step), prep everything, lay out your tools and ingredients, and then start cooking. This is like the **define-and-run** approach: you’re defining everything you need first and then executing.

- Read a step, do the step. Read the next step, do the next step, and so on. You’re learning and adjusting as you go along, perhaps even tweaking the recipe based on the ingredients you have at hand. This is like PyTorch’s **define-by-run** approach: everything is dynamic and on-the-fly.

PyTorch follows the second method. When it processes data (like our cooking ingredients), it doesn’t wait for the entire computational blueprint (our recipe) to be defined upfront. Instead, as soon as you define a computation, it runs it. This makes PyTorch very flexible and adaptable, like a chef who adjusts based on the ingredients in the pantry.

In simpler terms, with some other frameworks, you might first tell the computer as follows: First, I’ll do A, then B, then C, and only after you’ve laid out the entire plan will you start feeding in your data. But with PyTorch, you can tell the computer to do A, and it will do A right away. Then you ask it to do B", and it promptly does B. It’s like a conversation with immediate responses.

This dynamic nature is like building with Lego blocks. You can stack a block, decide if it looks good, maybe remove it, or add another type; all without having to plan the entire structure beforehand.

Consider a navigation system. The define-and-run method is like deciding on the entire route before starting your car. You can’t change the route once you start driving. On the other hand, PyTorch’s method is like a GPS that recalculates the route as you drive, based on real-time traffic data. You can take a different turn, and the system will adapt instantly.
