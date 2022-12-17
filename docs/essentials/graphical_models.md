---
layout: default
parent: Statistics
grand_parent: Essentials
nav_order: 3
title: Graphical Models
---

# Graphical Models

## Motivation

Although this might sound surprising to many, there is actually a lot of statistics we can do without specifying specific 
distributions over our variables. Our main way to go about that is through using **graphical models** in which we explicitly 
define our variables and how they relate to each other. This allows us to formulate the (conditional) independence relationships 
between the variables.

First of all, you might wonder why we would exactly care about these conditional independence relations. Suppose, 
for the time being, we measure $$4$$ different binary variables, denoted as $$X_1, X_2, X_3$$, and $$Y$$. 
For example, $$X_1, X_2, X_3$$ could denote 3 different aspects of a house (e.g. $$X_1$$ is many/few rooms, 
$$X_2$$ is old/new house, and $$X_3$$ one/multiple floors) and $$Y$$ denotes whether it was sold for a high or low price.[^1]
We can imagine that these $4$ variables define one large join distribution (of an unknown kind), i.e. for all values 
$$x_1, x_2, x_3$$, and $$y$$, we can assess $$\mathbb{P}(X_1 = x_1, X_2 = x_2, X_3 = x_3, Y=y)$$. It is important to 
realize that when we have a joint distribution, we can find any marginal or conditional probability of the variable. 
For example, to find the probability of there being many rooms, given that the house was sold for a high price and the 
house was old, we can find this:

$$\mathbb{P}(X_1 = 1 \mid Y=1, X_2 = 0) = \frac{\mathbb{P}(Y=1, X_1 = 1, X_2 = 0)}{\mathbb{P}(Y=1, X_2 = 0)},$$

which we can evaluate through marginalisation by

$$\mathbb{P}(X_1 = 1 \mid Y=1, X_2 = 0) = \frac{\sum_{x_3} 
 \mathbb{P}(Y=1, X_1 = 1, X_2 = 0, X_3 = x_3)}{\sum_{x_1, x_3} 
 \mathbb{P}(Y=1, X_1 = x_1, X_2 = 0, X_3 = x_3)}.$$



Having the full joint distribution is our ideal case, exactly it allows us to ask these types of questions. In this case, 
we need to specify $$2^4 = 16$$ different values for each of the combinations of $$X_1, X_2, X_3$$, and $$Y$$.[^2] 
However, now imagine our variables taking on $$10$$ different values (which still, compared to variables that take on an 
infinite number of values) and having $$20$$ different variables. We would have to specify $$10^{20}$$ different values. 
To put this into perspective, that are more values than there are grains of sand on the planet. 

We will see that using graphical models and the independence relations they describe will allow us to reduce the number of parameters a lot.

[^1]: Of course, the assumption of binary variables is a little awkward here, but the intuition will be slightly easier as such.
[^2]: Technically, since we know that all the probabilities will sum up to 1, we need only 15 parameters.