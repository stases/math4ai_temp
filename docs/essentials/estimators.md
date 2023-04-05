---
layout: default
parent: Statistics
grand_parent: Essentials
nav_order: 5
title: Estimators
---


# Estimators

{: .motivation }
Suppose we know what distribution our data follows - e.g. since we know that Poisson distributions typically model the number
of times an event occurs per time unit, we might use some Poisson to model the average number of emails you receive per day. 
The most important next question is: to specify a Poisson, the need to select its $$\lambda$$ parameter. How do we choose this
parameter based on a dataset of observation, i.e. a collection of email counts of a certain number of days? In this section,
we will cover the most common way to estimate a distribution parameter: the maximum likelihood estimate.


In the previous section, we have seen that sometimes we would want to estimate a parameter based on data. Let us pick 
another distribution for variety, sticking with the simplest distribution out there: the Bernoulli. Essentially, a Bernoulli
distribution models a weighted coin flip: it has one parameter $$\theta$$, which denotes the probability of $$1$$, and assigns
a probability of $$1- \theta$$ to outcome $$0$$. We write $$X \sim \mathsf{Ber}(\theta)$$ to denote that $$X$$ follows a 
Bernoulli distribution with parameter $$\theta$$. 

Suppose we have some dataset $$\mathcal{D}$$ with observations from $$X$$, e.g. $$\mathcal{D} = \{1, 1, 0, 1, 1, 1, 0, 1\}$$,
i.e. we flipped $$1$$ six times, and $$0$$ two times. Intuitively, we would now expect $$\theta$$ to be estimated to be $$\frac{6}{8}$$
since that's how many outcomes were positive. But, can we prove this? 

## Maximum Likelihood Estimators

One of the most common ways to estimate parameters is maximum likelihood estimation (or: MLE). The idea behind 
MLE is quite simple: we first define a functions $$\mathcal{L}(\theta; \mathcal{D})$$ which tells us how 'likely' each parameter
value $$\theta$$ is given the data we have observed, and then we simply find the $$\theta$$ for which this function is maximized, i.e.

$$\theta_{\text{MLE}} = \text{argmax}_{\theta} ~\mathcal{L}(\theta; \mathcal{D}).$$

Sometimes - especially since many distributions have exponential in them - it is easier to optimize an equivalent objective, 
which we call the log-likelihood: 

$$\theta_{\text{MLE}} = \text{argmax}_{\theta} ~ \log \mathcal{L}(\theta; \mathcal{D}).$$

Please note that this is allowed since $$\log$$ is a monotone function, i.e. that $$x \leq y$$ implies we have $$\log x \leq \log y$$. 
Notice that if some point $$x \leq y$$ for all points $$y$$, we therefore also have that $$\log x \leq \log y$$ for all points $$y$$,
and hence the location of the minimum does not change.

So, what is this likelihood function? It is slightly subtle, but if we consider some observation $$x$$ we could consider $$\mathbb{P}(X=x)$$. 
Of course, implicitly that distribution is parametrized by some parameters, in this case, we can write $$\mathbb{P}(X=x; \theta)$$. 
In this case, the pmf is given by

$$p_X(x; \theta) = \theta^x (1-\theta)^{1-x}.$$

Take some time to digest this: if $$x=1$$, we get back a probability of $$\theta$$, and if $$x=0$$ we get back a probability of $$1-\theta$$.

However, normally we knew $$\theta$$ and wanted to assess $$x$$, but in the case of MLE we have the actual outcomes $$x$$
and now wish to find the $$\theta$$. Since the outcomes $$x$$ are those that occured, it makes sense to find the
$$\theta$$ that maximize the above probability, and as such the choose

$$\mathcal{L}(\theta ; x) := p_X(x ; \theta) = \mathbb{P}(X=x ; \theta).$$

And in the case of our Bernoulli, we would have that

$$\mathcal{L}(\theta ; x) = \theta^x (1-\theta)^{1-x}.$$

Notice what is funny about this definition: even though a pmf typically takes $$x$$ as its input and is parametrized by
$$\theta$$, we now define a new function $$\mathcal{L}$$ which is simply the pmf where we keep the $$x$$ fixed and vary
the parameter $$\theta$$. 

This is one last subtly we need to cover. The above gives us the likelihood for $$\theta$$ given a single data point. 
Commonly when doing MLE, the following assumption is made: **all data points are identically and independently distributed**.
This is quite an important assumption we make, and fully grasping it can be hard. In short, imagine we collect datapoints
$$x_1, \cdots, x_n$$ which are all outcomes of some random variable. The assumption - very briefly - states that the order
in which we collected our data is nonimportant, i.e. if we shuffle the data around it should not matter. This makes sense for
our coin flip example: there is no reason to assume that there is any information in the order of our dataset, i.e. the 
datasets $$\mathcal{D} = (1, 1, 0, 1, 1)$$ is the same as the dataset $$\mathcal{D} = (0, 1, 1, 1, 1)$$ - which is typically
why we just write $$\mathcal{D} = \{1, 1, 0, 1, 1\}$$ as an actual set. As a consequence of this assumption, we can use independence
and say that

$$\mathcal{L}(\theta ; \mathcal{D}) = \mathcal{L}(\theta ; \{x_1, \cdots, x_n\}) = \prod_{i=1}^n \mathcal{L}(\theta; x_i).$$

Similarly, the log-likelihood of $$\theta$$ given our data would be given by

$$\log \mathcal{L}(\theta ; \mathcal{D}) = \log \prod_{i=1}^n \mathcal{L}(\theta; x_i) = \sum_{i=1}^n \log \mathcal{L}(\theta; x_i).$$

## Solving the MLE of the Bernoulli

Going back to our Bernoulli, suppose we have some dataset of observations $$\mathcal{D} = \{x_1, \cdots, x_n\}$$. Again, 
each such observation is either $$1$$ if the flip was positive, or $$0$$ if the flip was negative. Intuitively, we might guess
that $$\theta$$ should be the number of positive flips relative to the total number of observations, but let us see what the MLE 
tells us. 

In our case, the likelihood function of $$\theta$$ for a single datapoint is given by

$$\mathcal{L}(\theta ; x) = \theta^x (1-\theta)^{1-x}.$$

As such, the log-likelihood of $$\theta$$ for the entire data will be given by

$$\log \mathcal{L}(\theta ; \mathcal{D}) = \sum_{i=1}^n \log \theta^{x_i} (1-\theta)^{1-x_i} = \sum_{i=1}^n {x_i} \log \theta + (1-x_i) \log (1-\theta).$$

Now we want to know for which value of $$\theta$$ the above likelihood is maximized, i.e. we want to know when its derivative is equal to 0.
Taking the derivative is quite straightforward, since

$$\frac{d}{d \theta} \sum_{i=1}^n x_i \log \theta + (1-x_i) \log (1-\theta) = \sum_{i=1}^n  \frac{d}{d \theta}( x_i \log \theta + (1-x_i) \log (1-\theta))$$

which simply gives us that

$$\frac{d}{d \theta} \log \mathcal{L}(\theta ; \mathcal{D})  = \sum_{i=1}^n \frac{x_i}{\theta} - \frac{1-x_i}{1-\theta}.$$

Now, we are interested in setting this derivative equal to zero, to see where the optimum lies, which gives us 

$$\sum_{i=1}^n \frac{x_i}{\theta} - \frac{1-x_i}{1-\theta} = 0 \iff \sum_{i=1}^n \frac{x_i}{\theta} = \sum_{i=1}^n \frac{1-x_i}{1-\theta} \iff \frac{1}{\theta} \sum_{i=1}^n x_i = \frac{1}{1-\theta} \sum_{i=1}^n 1-x_i .$$

This can be simplified as

$$\frac{1}{\theta} \sum_{i=1}^n x_i = \frac{1}{1-\theta} \sum_{i=1}^n 1-x_i \iff (1-\theta ) \sum_{i=1}^n x_i  = \theta  \sum_{i=1}^n 1-x_i.$$

Expanding and collecting terms gives us that 

$$ \sum_{i=1}^n x_i - \theta \sum_{i=1}^n x_i = \theta  \sum_{i=1}^n 1 - \theta \sum_{i=1} x_i \implies \theta \cdot n = \sum_{i=1}^n x_i,$$

where we used that $$\sum_{i=1}^n 1 = n$$, since we simply add 1 a total of $$n$$ times. As such, we find that the $$\theta$$ value
maximizing the likelihood - which we denote as the MLE estimate of $$\theta$$ - is given by:

$$\theta_{\text{MLE}} = \frac{\sum_{i=1}^n x_i}{n}.$$

Notice how this is exactly as we expected: the value $$\theta$$ is most likely to have based on our data is exactly the number of positive outcomes -
which you can calculate simply by summing the observations - divided by the total number of observations. 

{: .content }
In this section, we learned how to define likelihood functions and studied the basic maximum likelihood objective. Moreover,
we went through an example of maximum likelihood estimation for the parameter of a Bernoulli distribution.
