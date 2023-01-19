---
layout: default
parent: Statistics
grand_parent: Essentials
nav_order: 2
title: Probability calculus
---

# Probability calculus

In this section we will deep dive into the calculus of probability. Specifically, we will learn how to answer queries
such as marginals and conditionals given our joint distribution. For this, we need to meet a series of rules that will be some or our
best friends when doing probability theory first.

## Chain rule and conditional probabilities

Suppose we have two random variables $$X$$ and $$Y$$ with joint distribution $$\mathbb{P}(X, Y)$$. We understand 
$$\mathbb{P}(X=x, Y=y)$$ as the probability that $$X$$ has outcome $$x$$ and $$Y$$ has outcome $$y$$. Intuitively, we
can also understand that joint probability as follows: my believe that $$X$$ will take on outcome $$x$$ and $$Y$$ takes on
outcome $$y$$ can be 'decomposed' into my belief that $$X$$ will take on $$x$$ in general, and then that $$Y$$ takes on 
value $$y$$ given that $$X$$ has taken on value $$x$$. For example, my belief in me studying well and passing the exam is 
simply my belief in me studying well in general combined with my belief that if I study well, I will pass the exam. Formally,
we write this as 

$$\mathbb{P}(X=x, Y=y) = \mathbb{P}(X=x) \cdot \mathbb{P}(Y=y \mid X=x).$$

Actually, the oposite reasoning also goes, so

$$\mathbb{P}(X=x, Y=y) = \mathbb{P}(Y=y) \cdot \mathbb{P}(X=x \mid Y=y).$$

This is called the **chain rule** of probability theory, and this rule you will use over and over when doing probability
calculus. At this point, it becomes a bit convoluted to write $$X=x$$ every time, so we might right this also as

$$\mathbb{P}(X, Y) = \mathbb{P}(X) \cdot \mathbb{P}(Y \mid X),$$

to mean that $$\mathbb{P}(X=x, Y=y) = \mathbb{P}(X=x) \cdot \mathbb{P}(Y=y \mid X=x)$$ for all $$x$$ and $$y$$. 

Moreover, this rule generalises, e.g.

$$\mathbb{P}(X, Y, Z) = \mathbb{P}(X) \cdot \mathbb{P}(Y, Z \mid X)$$

and thus

$$\mathbb{P}(X, Y, Z) = \mathbb{P}(X) \cdot \mathbb{P}(Y \mid X) \cdot \mathbb{P}(Z \mid X, Y).$$

In its most general glory, it would say that

$$\boxed{\mathbb{P}(X_1, \cdots, X_n) = \prod_{k=1}^n \mathbb{P}(X_k \mid X_1, \cdots, X_{k-1})}.$$

Actually, this also gives us a way to define conditional probabilities directly. Since

$$\mathbb{P}(X, Y) = \mathbb{P}(X) \cdot \mathbb{P}(Y \mid X),$$

we know that 

$$\boxed{\mathbb{P}(Y \mid X) = \frac{\mathbb{P}(X, Y)}{\mathbb{P}(X)}}$$

given that $$\mathbb{P}(X) \neq 0$$.



## Marginalization and marginal probabilities

Another very important fact of probability theory is **marginalization**. It says that if we have two random variables $$X$$ 
and $$Y$$, we can understand $$\mathbb{P}(X=x)$$ also as a 'summed out' version join probabilities with $$Y$$, i.e.

$$\boxed{\mathbb{P}(X=x) = \sum_{y} \mathbb{P}(X=x, Y=y)}.$$ 

Equivalently, we can say that 

$$\boxed{\mathbb{P}(X=x) = \sum_{y} \mathbb{P}(X=x \mid Y=y) \cdot \mathbb{P}(Y=y)}.$$ 

This definition makes intuitive sense: my believe in $$X$$ taking on outcome $$x$$ in general, is simply a combined version
of $$X$$ taking on $$x$$ given that $$Y=y$$, weighted by my belief in $$Y=y$$. Here, we say that $$\mathbb{P}(X)$$ is a **marginal probability.**  


## Bayes rule


Last, but certainly not least, is a rule that follows directly from the chain rule we covered earlier. We observed that 
$$\mathbb{P}(X, Y) = \mathbb{P}(X) \cdot \mathbb{P}(Y \mid X)$$ and also $$\mathbb{P}(X, Y) = \mathbb{P}(Y) \cdot \mathbb{P}(X \mid Y)$$. 
It is not hard to see that

$$\boxed{\mathbb{P}(X \mid Y) = \frac{\mathbb{P}(Y \mid X) \cdot \mathbb{P}(X)}{\mathbb{P}(Y)}}$$ 

This is called **Bayes' rule** and gives us a very nice way to 'swap' the variables in a conditional distribution. 
 