---
title: "How Neural networks are tied to probability distributions"
date: 2025-01-12
draft: false
summary: "Clarifying the relation between neural networks and probability distributions"
---

This article will focus on exploring the relationship between probability (or, more specifically, probability distributions) and neural networks in an intuitive manner.

As previously stated, neural networks represent a parameterized family of functions. If the parameters were fixed, the neural network would essentially become a function (or, more generally, a map). However, academicians often state that neural networks represent probability distributions, which implies randomness, a concept that does not sit well when you think of neural networks in terms of deterministic functions.

Upon receiving the same input x multiple times, a given neural network should produce the exact same output in almost all cases (I say almost all cases because sometimes random noise is added within a neural network to regularize it during training). So, where does this randomness come from? And if there is randomness in a neural network, why do we need it? Since I have built enough suspense now, I will answer these questions by delving into the basic core concepts and throwing a new light on them. I will begin by explaining the need for randomness in deep learning.

#### Everything is random, but nothing is random.
Before we begin, I want to redefine the concept of randomness by using two basic examples.

1. **The coin flip** - One of the most used examples of 'random experiments', the coin flip experiment goes like this: Given a coin that is equally weighted on both sides (that is, it is unbiased), if we flip the coin, will we get heads or tails? Intuitively, we would say that since either outcome is equally likely, there is no way for us to predict what the actual outcome will be; it is truly a random phenomenon. But is it actually random? Let us pretend to be geniuses with a profound knowledge of rotational mechanics, and we are provided with data such as the force used to flip the coin, the torque applied to the coin, its thickness, weight distribution, the air resistance, and the exact gravitational acceleration at that point, using which we could determine the number of rotations the coin would make before landing back on our hand and thus predict the outcome of the coin flip. In this case, we were able to determine the outcome of the coin flip without observing it, meaning that for us, it is not a random phenomenon but a deterministic one.
2. **Guessing game** - Assuming you have friends, let's say you are playing a guessing game with one of them. In this game, your friend will choose a number in their head, multiply it by 3, and add 5 to it. Your job is to guess the resulting number. Can you do it? You know that the resulting number will be the result of multiplication and addition operations, but since you do not know the original number that your friend had chosen, you cannot predict the resulting number. In other words, it is random for you. However, your friend, who knows the original number, thinks of the resulting number as deterministic, as it was calculated from the given operations.

These two examples suggest that randomness is subjective rather than objective. For the observer with no knowledge or information about the coin, the coin flip can be seen as random, while for the observer with knowledge and information about the coin's dynamics, the coin flip is a function of some given variables. The same contrast applies to the second example between you and your friend.

If we have complete and sufficient information about a phenomenon (or process), we can theoretically predict its outcome. Randomness arises when we have incomplete information, in which case we use extrapolation techniques to try and determine the outcome (which is just a fancy way of saying 'educated guesses').

Our daily lives are full of random phenomena, and when faced with one, we subconsciously assign a probability to each outcome and choose the outcome with the highest probability. We assign these probabilities by referring to our past experience or by suitably restructuring our knowledge system. Regardless of the method, this mapping of outcomes to a corresponding probability is similar to what a probability distribution does.

The tasks that deep learning methods solve are similar in this sense; the features do not contain sufficient information, but deep learning methods learn to assign probabilities to different outcomes from the given information. Hence, randomness is a part of everyday life, which translates to deep learning applications as well.

`
My interpretation of randomness is very loose and non-technical. There are some edge cases that do not follow this interpretation, but it would be impractical to cover them here as they serve no purpose.
`

#### Probability distributions and parameters
Loosely speaking, probability distributions are maps that assign a probability measure to an outcome. (The probability measure of an outcome refers to the odds of that outcome occurring.) Probability distribution functions (pdf's) provide an analytical method for assigning probability measures to outcomes. Some standard distribution functions include

*The Gaussian distribution for continuous-valued variables*, 

$$f(x \mid \mu, \sigma^2)
= \frac{1}{\sqrt{2\pi\sigma^2}}
\exp\!\left(-\frac{(x-\mu)^2}{2\sigma^2}\right),
\qquad x \in \mathbb{R}.
$

*The Bernoulli distribution for binary variables*,

$$
f(x \mid p) = p^x(1-p)^{1-x},
\qquad x \in \{0,1\},\; 0 \le p \le 1.
$$

etc. One will notice that these distribution functions have an unknown value, which we refer to as the parameter of that distribution function. These parameters largely influence the probability distribution function, changing its shape, position, and scale significantly. In the case of the Gaussian distribution, the mean and variance controlled the location and shape of the bell curve. In the case of the Bernoulli distribution, the parameter would control the weight of the probability of one variable. *Thus, probability distributions are characterized by a set of values referred to as their parameters.*

`
Probability distribution functions with variable parameters represent a family of distributions.
`

#### Relating Neural networks and probability distributions
Now that we have our basic concepts cleared, it will be easy to define a relationship between the two. However, our initial statement that neural networks represent probability distributions needs a slight modification. Technically, neural networks parameterize probability distributions. The output of a neural network is used as the parameters in a given probability distribution. The family of distributions that the neural network parameterizes mainly depends on the architecture of the neural network and the loss function used to train it.

For example, if we were to consider the task of classifying whether a car is present in a given image, let us assume that the neural network outputs a single scalar value whose range is from 0 to 1 (1-> Car is present in the image, 0-> Car is not present in the image). Since the two events are mutually exhaustive, we can assume the neural network is parameterizing a Bernoulli distribution, that is, it outputs the value p. Given p, we can plug it into the Bernoulli distribution function and determine the mode of the distribution, thus obtaining our answer.

`
In the event that the output is a real number, the neural network would most likely parameterize a Gaussian distribution. Given that its mean, median, and mode are the same, determining only the mean as a parameter is enough. Similarly, by imposing suitable constraints, we can make the neural network explicitly parameterize the distribution we want.
`

Thus, this article has explored the relation between neural networks and probability as promised. As a bonus, we also discovered a new perspective on randomness and why incorporating it in deep learning is so important.