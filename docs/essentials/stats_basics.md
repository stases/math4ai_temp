---
layout: default
parent: Statistics
grand_parent: Essentials
nav_order: 1
title: Basic probability theory
---

# Basic probability theory
## Basics: Random variables and probabilities

In order to study machine learning well, we need to develop a mathematical language to deal with collecting, analysing,
and interpreting data. This is what we commonly understand to be 'statistics', with is our major topic of study in this
section. However, before we can deep dive into statistics we need to study the mathematical foundations of statistics 
briefly. Most importantly, we need to look a probability theory, which is what we will do in this section!


Probability theory is a special type of mathematics that is able to handle uncertainty of events. Even though this area
of mathematics is very, very vast, we will mainly focus on what very useful object in probability theory: the random variable. 
Suppose we have a streaming site, and our event of interest we want to represent is the rating some user will give for a new movie 
just uploaded to the site. Let us denote this variable as $$R$$ for rating. We assume the user can rate the 
movie on a $$5$$ star scale, i.e. they can give it exactly $$5$$ different values. For example, we can understand
$$R=1$$ as the situation that the rating given is one star, et cetera. Because we do not yet know what the rating $$R$$ is
beforehand, its outcome is uncertain for us. To **quantify** this uncertainty, we use probabilities. We call $$R$$ a **random variable**.


What does it mean for the probability of some event to be $$\frac{1}{6}$$? You might intuitively understand the probability 
of a die (that is, half a pair of dice) ending up on a face with $$4$$ dots as $$\frac{1}{6}$$, because if you would roll
that die a certain number of times, you would expect it landed on a $$4$$ roughly a $$\frac{1}{6}$$th of the times. That is, a 
probability would tell you how **frequently** some event occurs. Even though this intuition is nice when first learning about 
probabilities, this understanding of probabilities is quite restrictive. For instance, when we are interested in the 
probability of you becoming a great academic, there is no way to interpret that probability as a frequency. But still, 
if one says that the probability of you becoming a great academic is $$\frac{5}{6}$$ instead of $$\frac{1}{6}$$ after studying this site 
(sadly not an actual statistic), that does tell you something about my **degree of belief** in you becoming a 
great academic after reading this site. It turns out that this second interpretation of probability theory is more 
useful in deep learning, even though this exact question is a large philosophical debate called 'frequentist versus 
Bayesian interpretation of probability'. 

For now, there are two properties that are very important when considering a random variable. If we consider the set of 
all outcomes, we assume that 

1. The probability of each outcome lies somewhere in the interval $$[0, 1]$$, that is each probability is at least $$0.0$$ and at most $$1.0$$.
2. If we sum over the probabilities all the outcomes, the total should add up to be exactly $$1$$.



For examples, suppose we are optimistic and assign a probability of $$0.6$$ to the rating of the user being 5 stars, and assign a 
probability of $$0.1$$ to all other outcomes, this would define a valid random variable. We call the function that
assign the probability to each outcome a **probability mass function** (or: pmf). Often, we write $$f_R$$ or $$p_R$$ for
the pmf of random variable $$R$$, so in this case $$f_R(5) = 0.6$$.

Often, we denote 'the probability' with the symbol $$\mathbb{P}$$, and denote the set of all outcomes as $$\Omega$$. Hence,
for some random variable $$X$$ the above lines can be formalized as

1. $$\mathbb{P}(X=x) = f_X(x) \in [0, 1]$$ for all $$x \in \Omega$$;
2. $$\sum_{x \in \Omega} \mathbb{P}(X=x) =\sum_{x \in \Omega} f_X(x) = 1$$.

There is one subtlety: if the outcomes do not come from a discrete set but rather from a continuous set, we need a slightly 
more exotic object. In short,
if we would again assign a probability greater than $$0$$ to any outcome, the fact that are are so many outcomes will
imply that the total integral (the continuous counterpart of a sum) will not be equal to $$1$$. One solution for this
is to rather of intervals of outcomes. Suppose the outcomes of our event $$X$$ are the entire number line, and $$f_X$$
is some function over this interval (if you want, picture a normal distribution if you are familiar with this already).
We demand that the total area underneath this curve is again $$1$$, i.e. that

$$\int_{- \infty}^{\infty} f_X(x) dx = 1.$$

When associating the area with probability, we can now also ask that the probability is that $$\mathbb{P}(X \geq 0)$$ by
just integrating over all outcome greater than zero or equal to:

$$\mathbb{P}(X \geq 0) = \int_{0}^{\infty} f_X(x) dx.$$

In the continuous case, we call this function $$f_X$$ a **probability density function** (or: pdf), rather than a pmf. 


## Basics: Distributions and queries

In general, we might be interested in multiple variables. Suppose we also care about a new random variable with denotes
'whether a person is happy'. In this case, $$\mathbb{P}(H=0)$$ denotes the 
probability that the customer is unhappy, and $$\mathbb{P}(H=1)$$ denotes the probability that the customer is happy. 
In this case, we assume that the customer is either happy or unhappy, so there is no third option. This now gives us
a lot of different outcomes already, since we could in theory have a probability for the combination of outcomes and 
happiness scores, giving a total of $$5 \times 2 = 10$$ different probabilities. The notation does not change much, e.g.
if we consider the probability that someone give a five star rating and is happy to be $$0.5$$, we write $$\mathbb{P}(R=5, H=1) = 0.5$$.
We call a distribution over multiple random variables a **joint distribution**.

Now, we might ask either of the following two things: 1) what if I do not care about the specific rating of a user, but rather care whether or not their happy?  
And: 2) how do I find the probability that someone will rate a move five stars if I know they are unhappy? These questions about
our variables of interest, sometimes called **queries**, we can all answer using the joint distribution. Actually,
in general we can get to know whatever we want about our variables if we are able to specify the joint. 

In general, we differentiate two different questions:

1. **Marginal probabilities.** In this case, we are interested in the outcomes of a strict subset of out variables. The
first question in the previous section is an example of such a query. Formally, we ask how to get from $$\mathbb{P}(X_1, \cdots, X_n)$$ 
to $$\mathbb{P}(X_i)$$. 
2. **Conditional probabilities.** In this case, we are interested in the outcome of some of our variables if we already
know the outcome of the rest. This query corresponds to the second question in the previous section. We denote the probability
of $$X=x$$ given the outcome that $$Y=y$$ as $$\mathbb{P}(X=x \mid Y=y),$$ but this notation will be made formal in the
next section where we also study how to calculate these probabilities.

