---
layout: default
parent: Statistics
grand_parent: Essentials
nav_order: 1
title: Basic probability theory
---

# Basic probability theory
## Basics: Random variables and probabilities


In statistics, we will be working with a special type of mathematics that is able to handle uncertainty of events. 
The main object of interest for us is the random variable. Suppose we have a streaming site, and our variable 
of interest represents the rating some user will give for our new movie, denoted $$R$$. We assume the user can rate the 
movie on a $$5$$ star scale, i.e. they can give it exactly $$5$$ different values. Because we do not yet know the rating $$R$$,
its outcome is uncertain for us. To quantify this uncertainty, we use probabilities. We call $$R$$ a **random variable**.


To use random variables, we need a little bit of probability theory. You might intuitively understand the probability 
of a die (that is, half a pair of dice) ending up on a face with $$4$$ dots as $$\frac{1}{6}$$, because if you would roll
that die a certain number of times, you would expect it landed on a $$4$$ roughly a $$\frac{1}{6}$$th of the times. That is, a 
probability tells you how **frequently** some event occurs. Even though this intuition is nice when first learning about 
probabilities, this understanding of probabilities is quite restrictive. For instance, when we are interested in the 
probability of you becoming a great academic, there is no way to interpret that probability as a frequency. But still, 
if one says that the probability of you becoming a great academic is $$85\%$$ instead of $$15\%$$ after studying this site 
(sadly not an actual statistic), that does tell you something about my **degree of belief** in you becoming a 
great academic after reading this site. It turns out that this second interpretation of probability theory is more 
useful in deep learning, even though this exact question is a large philosophical debate called 'frequentist versus 
Bayesian interpretation of probability'. 

## Basics: Distributions

**Add something about pmf/pdf/distribution/joint.**

Besides standard probabilities, there are two types of probabilities that are of the utmost importance when doing
probability theory: **conditional and marginal probabilities**. We will introduce these probabilities intuitively here,
and show you how to calculate them in general in the next section.


## Conditional probabilities: Intuition


Random variables can describe any stochastic process, or 'experiment'. Suppose $$R$$ still denotes the rating given by a person on a 5-star scale, 
and let $$H$$ denote a random variable describing 'whether a person is happy'. In this case, $$\mathbb{P}(H=0)$$ denotes the 
probability that the customer is unhappy, and $$\mathbb{P}(H=1)$$ denotes the probability that the customer is happy. 
In this case, we assume that the customer is either happy or unhappy, so there is no third option. 

Suppose we consider our new customer, and we have no idea what rating they will give or how happy they are beforehand. For example given
variable $$H$$, for us $$\mathbb{P}(H=0) = \mathbb{P}(H=1)$$, or our belief that the customer is happy is as large as that 
the customer is unhappy. Let us now assume the user rates our movie with five stars, e.g. we observe that $$R=5$$. Intuitively, 
my belief that $$H=1$$ now increases, let us say to $$0.9$$. This is because in general a high rating is associated
with being happy with the service, and similarly a low rating is associated with being unhappy with the service. Formally,
we say that the probability that $$H=1$$ **given** that $$R=5$$ is $$0.9$$, 
written as $$\mathbb{P}(H=1 \mid R=5) = 0.9$$. 
As a consequence, we have also that $$\mathbb{P}(H=0 \mid R=5) = 0.1$$. We call this type of probability a **conditional
probability**, since we again consider the probability of $$H$$ but now using our extra information we have about $$R$$.
As you may have noticed, this again defined a distribution over $$H$$, which we denote as $$H \mid R=5$$. 


## Conditional probabilities: Independence


Suppose I now introduce yet another variable, $$B$$ which denotes whether the user has blue eyes, again taking on values $$1$$ 
and $$0$$ denoting whether or not the user has blue eyes respectively. In this case, there is no reason to assume that my
belief that someone is happy changes after observing whether or not someone has blue eyes, i.e.

$$\mathbb{P}(H=1 \mid B=1) = \mathbb{P}(H=1).$$

Without defining these notions formally here, you can convince yourself that there is no **information** about $$H$$ in $$B$$, 
where there is information about $$H$$ in $$R$$. When there is no information about $$X$$ in $$Y$$, or when 

$$\mathbb{P}(X=x \mid Y=y) = \mathbb{P}(X=x)$$ 

for whatever values $$x$$ and $$y$$, we say that $$X$$ and $$Y$$ are **independent**. You may also have encountered this as

$$\mathbb{P}(X=x, Y=y)  = \mathbb{P}(X=x) \cdot \mathbb{P}(Y=y),$$

which is exactly the same thing when multiplied by $$\mathbb{P}(Y=y)$$ and making using of the fact that 
$$\mathbb{P}(X=x, Y=y) = \mathbb{P}(Y=y) \cdot \mathbb{P}(X=x \mid Y=y).$$


In a real-life situation, simple independence is almost something you never encounter. A much more common scenario is 
that of two random variables being independent _given_ some third variable. Suppose we consider two students that both 
travel by the same train to the university, and we denote $$S_1$$ as the binary variable describing whether student $$1$$ 
is on time for the lecture, and $$S_2$$ the binary variable describing whether student $$2$$ is on time. Intuitively, these 
events are related, since when you tell me that $$S_1$$ is on time, that increased my belief that $$S_2$$ also is on time, 
for the reason that the trains were not delayed. In other words,

$$\mathbb{P}(S_2 = 1 \mid S_1 = 1) > \mathbb{P}(S_2 = 1).$$ 

Therefore, we observe that $$S_1$$ and $$S_2$$ are **not independent**.

However, let us now introduce yet a third variable $$T$$ denoting whether the train was on time. By a similar argument, we have that 

$$\mathbb{P}(S_2 = 1 \mid T = 1) > \mathbb{P}(S_2 = 1),$$ 

since again telling me that the train was on time increases my belief 
that student 2 is on time. However, suppose now that I already know that the train is on time. Does my observing that $$S_1$$ is 
or is not on time still tell me something new? In this case no, because the only thing it could tell me is something about 
whether or not the train is delayed, and since we already knew that the train was not delayed we obtain no information. 
In this case, we have that actually that for all situations $$s_1, s_2, t$$, we intuitively find that

$$\mathbb{P}(S_2 = s_2 \mid T = t, S_1 = s_1) = \mathbb{P}(S_2 = s_2 \mid T = t).$$

In this case, we say that $$S_2$$ is **conditionally independent** of $$S_1$$ given $$T$$. 
In other words, we say that $$X$$ is conditionally independent of $$Y$$ given $$Z$$, if my belief in $$X$$ is not affected by the 
outcome of $$Y$$ if I already know that $$Z$$. Please take you time to absorb this, this is arguably the most important
notion introduced in this section.

In the case above, we had a situation where $$X$$ and $$Y$$ were dependent, but $$X$$ and $$Y$$ were independent given some $$Z$$. 
I.e., even if there is an 'information flow' between $$X$$ and $$Y$$, there can be no 'information flow' from $$X$$ to $$Y$$ if 
we know that $$Z$$. Actually, the other case is also possible, the situation where $$X$$ and $$Y$$ are independent variables, 
but they become dependent given some variable $$Z$$. For example, suppose that $$S$$ denotes whether or not the first 
strawberry I eat on a day is sweet, and $$E$$ denotes whether or not the first coffee I prepare is an espresso. Needless 
to say, the outcomes of these events do not affect each other, and hence $$S$$ and $$E$$ are independent. However, 
assume for a moment I found someone crazy enough to follow me around my entire life, making sure to light some fireworks 
if either the first strawberry I eat on a given day is sweet or the first coffee I drink is an espresso 
(or both), denoted with $$F$$. Even though $$\mathbb{P}(S=1 \mid E=0) = \mathbb{P}(S=1)$$, if I now also observe that $$C=1$$, 
we have that $$\mathbb{P}(S=1 \mid E=0, F=1) \neq \mathbb{P}(S=1 \mid F=1)$$, because since the fireworks were lit, I 
know that since I did not have an espresso, it must mean that I had a sweet strawberry. So in this way, magically there is an 
information stream between my strawberries and coffee! So, if you have two variables that are independent, we can create
'fake' dependencies by conditioning them external variables. This all is to show that statistics is pretty tricky, and that 
being imprecise about which variables we assume to be (conditionally) independent can remove and create patterns in 
our observations that are unexpected.

## Marginal probabilities

**Add**