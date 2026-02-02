---
title: "Understanding Neural Networks"
date: 2025-01-12
draft: false
summary: "An intuitive approach to understanding neural networks that does not sacrifice generality"
featured: true
toc: false
---
If you like reading tech news or articles, you've probably come across the term neural networks at some point. People love throwing this term around and treat it like a black box with the ability to perform any task, but there is much more to it. In this post, I will give an intuitive and formal explanation of neural networks. This post talks about what neural networks are, not how they are trained or why they work so well. I will dissect those concepts in later posts.

`
P.S. If you have already studied neural networks, I would recommend FORGETTING whatever you have learned before reading this. It'll help you get a new perspective.
`

#### What exactly is a neural network?
Academics describe neural networks as a range of functions represented by directed acyclic graphs where vertices represent some kind of constrained functions, and edges represent the composition of those functions. This explanation is intuitively useless (although very important in a formal setting). When most people describe a neural network, they actually describe a _fully connected neural network_, which leads to confusion later on.

To answer the question of what exactly is a neural network, we take small steps

- The first thing you need to know is that neural networks represent very complex functions (By complex, I mean the function is hard to mathematically model, I do not mean that it has an imaginary part), they take an input and give a corresponding output. Theoretically, there is no constraint on the dimensionality of the input or output.
- The term network in neural networks points to the presence of an architecture. Every neural network is characterized by an architecture. The architecture of the neural network largely influences the nature of the function it represents. Every architecture is usually composed of multiple elementary and differentiable functions and their compositions.
- A neural network with a given architecture represents a *family of functions*. This family of functions is usually parameterized by a continuous high-dimensional variable θ, and training usually consists of manipulating θ according to our needs.

`
For those who don't remember, a family of functions is a group or set of functions with a similar characteristic feature. For example, f(x) = θx + 2 represents a family of functions. f(x) = x + 2 and f(x) = 2x + 2 are part of the same family. Here θ parameterizes the family and ties all the functions together (The similar characteristic feature I mentioned).
`

So far, we have defined two characteristics of a neural network: Its *architecture* and *parameters*. Training the neural network consists of changing/manipulating the parameters until the neural network performs well on a given task (When I say performs well, I don't mean it subjectively, there are objective metrics that measure the performance of a neural network, and they vary for each task).
Thus, our intuitive definition of neural networks up to now is: *Neural networks represent a parameterized family of functions that is decided by the network's architecture and parameter set. Training the network involves changing the parameters in accordance with a training algorithm A.*

`
Parameter set refers to the set of values that the parameter(s) is/are allowed to take.
`

- However, this definition is missing one crucial component, it doesn't tell us what a neural network is used for.

#### Why do we use neural networks?
To answer this question, I will go on a small tangent; please bear with me. What if I told you that every single phenomenon or mechanism in this world has an underlying function? Better yet, what if I told you that it is possible to approximate these functions? Let me explain with an example:

Suppose I take all the pictures in the universe, and I have to decide whether that picture contains a car or not. To do so, I will look for the features of a car: 4 wheels, a medium-sized body, windows, headlights, etc. We look for these features because they make sense to us, it's how we have been taught to identify cars. But maybe there are more *abstract features* that we cannot identify, but are unique to the given task. Moreover, these features can be used by a machine or mathematical model to identify whether a car is present in the picture. So when I talk about the underlying function, I talk about a function that can extract these underlying features from the image and use them to identify the presence of a car. More often than not, these functions exist and are smooth and well-behaved.

*Neural networks try to approximate these complex underlying functions by manipulating their parameters.* I will not go into details about how because that requires its own blog, but for now, just take my word for it (Or do some research of your own). Now, let us try and formulate our very own definition of neural networks one more time

#### Definition of Neural Network
*A neural network with a given architecture and parameter set represents a parameterized family of functions. Given a task T, the neural network tries to approximate the underlying function responsible for T by manipulating its parameters in accordance with a training algorithm A.*

So the next time somebody asks you what a neural network is (Yes, I mean in interviews as well), rattle off something like the above definition and I guarantee they will be impressed.

But in all honesty, there is still a lot that I have not said about neural networks as I only wrote this blog intending to create a general and easy-to-understand definition of them. I will not be explaining fully connected neural networks because there are plenty of materials on them already. However, I will be talking about the implications of different architectures, loss functions, and the representation perspective of neural networks in the future.

Until then, happy learning \:)