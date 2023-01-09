---
layout: default
parent: Statistics
grand_parent: Essentials
nav_order: 2
title: Probability calculus
---

# Probability calculus

## Chain rule




In the last section we saw that we can take a joint probability $$\mathbb{P}(X=x, Y=y)$$ and write it as 
$$\mathbb{P}(X=x) \cdot \mathbb{P}(Y=y \mid X=x)$$.


This is called the **chain rule** of probability theory, and this generalizes. For example:

$$\mathbb{P}(X=x, Y=y, Z=z) = \mathbb{P}(X=x) \cdot \mathbb{P}(Y=y, Z=z \mid X=x)$$

and thus

$$\mathbb{P}(X=x, Y=y, Z=z) = \mathbb{P}(X=x) \cdot \mathbb{P}(Y=y \mid X=x) \cdot \mathbb{P}(Z=z \mid X=x, Y=y).$$

At this point, it becomes a bit convoluted to write $$X=x$$ every time, so we might right this also as

$$\mathbb{P}(X, Y, Z) = \mathbb{P}(X) \cdot \mathbb{P}(Y \mid X) \cdot \mathbb{P}(Z \mid X, Y)$$

to exactly mean the same thing. In its most general glory, it would say that

$$\boxed{\mathbb{P}(X_1, \cdots, X_n) = \prod_{k=1}^n \mathbb{P}(X_k \mid X_1, \cdots, X_{k-1})}$$


## Conditional probabilities


We can understand the conditional probability as follows. Suppose we have random variables $$X$$ and $$Y$$ 
with the joint distribution $$\mathbb{P}(X=x, Y=y)$$. Intuitively, you can consider the probability 
that $$X=x$$ and $$Y=y$$ as just the probability that $$X=x$$ and that $$Y=y$$ given that $$X=x$$, i.e.

$$\mathbb{P}(X=x, Y=y) = \mathbb{P}(X=x) \cdot \mathbb{P}(Y=y \mid X=x).$$

And similarly, we have that

$$\mathbb{P}(X=x, Y=y) = \mathbb{P}(Y=y) \cdot \mathbb{P}(X=x \mid Y=y).$$

Therefore, we can define 

$$\boxed{\mathbb{P}(X=x \mid Y=y) = \frac{\mathbb{P}(X=x, Y=y)}{\mathbb{P}(Y=y)}}$$

given that $$\mathbb{P}(Y=y) \neq 0$$.


## Marginal probabilities



Another very important fact of probability theory is 'marginalization'. It says that if we have two random variables $$X$$ 
and $$Y$$, we can understand $$\mathbb{P}(X=x)$$ also as a 'summed out' version join probabilities with $$Y$$, i.e.

$$\boxed{\mathbb{P}(X=x) = \sum_{y} \mathbb{P}(X=x, Y=y)}$$ 

Here, we say that $$\mathbb{P}(X)$$ is a **marginal distribution.** This intuitively makes sense: the probability of $$X$$ 
happening is just the combined probability of it happening in all possible different scenarios. 


## Bayes rule


Last, but certainly not least, is something else we saw earlier. We observed that $$\mathbb{P}(X, Y) = \mathbb{P}(X) \cdot \mathbb{P}(Y \mid X)$$ 
and also $$\mathbb{P}(X, Y) = \mathbb{P}(Y) \cdot \mathbb{P}(X \mid Y)$$. It is not hard to see that

$$\boxed{\mathbb{P}(X \mid Y) = \frac{\mathbb{P}(Y \mid X) \cdot \mathbb{P}(X)}{\mathbb{P}(Y)}}$$ 

This is called **Bayes' rule** and gives us a very nice way to 'swap' the variables in a conditional distribution. 

All these rules hold in general and are super important ones, so keep them in your back pocket. 