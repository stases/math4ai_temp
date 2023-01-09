---
layout: default
parent: Statistics
grand_parent: Essentials
nav_order: 3
title: Distributions
---

# Distributions


One of the key objects we will look at is **distributions**. Suppose we have some random variable $$X$$ which has as support 
$$\mathbb{N}$$, i.e. we have probabilities for outcomes $$X=1$$, $$X=2$$, and so on. We can visualize the probability 
of the outcomes of the events using the **probability mass function**, which simply plots the probability values of each 
outcome. For example, our random variable could look something like this: 

**add**

This probability mass function (or: pmf) gives us something we call a distribution, it quite literately tells how the 
different probability values are distributed over the outcomes of $$X$$. Now, the beauty of the world of statistics is 
that we can now name different distributions and then classify different random variables as being of the same type of distribution. 
It so turns out that in the actual world a lot of processes follow only a very select set of distributions. For example, 
the number of visits on this website per hour, the number of arrivals at the university per minute, and the number of books 
handed out by the library per day, all follow a so-called _Poisson_ distribution. Similarly, the height of a given person, 
grades obtained in some university course, and the age at which professional MMA fighters quit fighting in competitions, 
are all random variables following a _Normal_ distribution. If some random variable $$X$$ follows a distribution called 
$$\mathsf{Dist}(\theta)$$ we write $$X \sim \mathsf{Dist}(\theta)$$, where $$\theta$$ denotes any extra information 
needed to specify the distribution. If the probability mass function of variable $$X$$ is given by function $$p_{X}$$, 
we can write that $$\mathbb{P}(X=x) = p_{X}(x).$$ Please now take your time to understand the difference between 
writing $$\mathbb{P}(X=x)$$ and $$p_X(x)$$, where the left-hand side can be considered asking a question the right-hand side answers. 


The distribution we will look at is the Poisson distribution. To specify a Poisson distribution, we need one parameter 
called the 'rate' of the distribution. We write $$X \sim \mathsf{Pois}(\lambda)$$ to denote that random variable $$X$$ follows 
a Poisson distribution with parameter $$\lambda$$. Here are some examples of the probability mass function of $$\mathsf{Pois}(\lambda)$$ 
for different values of $$\lambda$$:

The pdf of the Poisson is given by:

$$p_X(x) = \frac{\lambda^x e^{-\lambda}}{x!}.$$

This is pretty neat. If I now know the $$\lambda$$ which describes the distribution of the Poisson I care about for any 
experiment I care about, I can tell you how likely all the different outcomes of the experiment are. Also, since we have 
this nice formulation for the pdf, we can prove other stuff such as that the mean of a Poisson is always $$\lambda$$, 
the mode (i.e. highest value) is always $$\lfloor \lambda \rfloor$$, among other things.[^1]

Now you may wonder: this is all cute, but if we do not know $$\lambda$$ then why should I care? And you would be very much 
right, which is exactly why we are going to try and find these $$\lambda$$ values based on the data we collect. 
That is, suppose we have dataset $$\mathcal{D}$$ of observation, e.g. $$\mathcal{D} = \{2, 2, 3, 1, 2, 4, 5, 3, 5\}$$, 
we can use statistics (and machine learning) to find which $$\lambda$$ fits the data the best. 
This is done using techniques such as maximum likelihood estimation (MLE) and maximum a posteriori estimation (MAP). 
In this case, the $$\lambda$$ with the highest likelihood based on the data would be given by the average of the dataset, 
or $$\lambda_{\text{MLE}} = 3$$. The actual way in which you could derive the MLE or MAP estimate is a separate story,
but you just took the first step in understanding estimators.


[^1]: Here, $$\lfloor \cdot \rfloor$$ is the 'floor function', simply around down the input to the nearest integer.
